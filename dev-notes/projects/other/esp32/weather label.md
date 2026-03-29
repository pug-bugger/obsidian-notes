screen to see weather in Vilnius and inside the house. Switch between pages with button.

```
#include <WiFi.h>
#include <HTTPClient.h>
#include <ArduinoJson.h>
#include <U8g2lib.h>
#include <DHT.h>
#include <Wire.h>

// --- CONFIGURATION ---
const char* ssid = "Have a Nice Day";
const char* password = "sunShine100";
String apiKey = "c1b2bbfd448949bc16c9482fa5f26f65";

// --- PINS ---
#define DHTPIN 4       // DHT11 Data Pin
#define DHTTYPE DHT11
#define BUTTON_PIN 5  // Button Pin

// --- OBJECTS ---
DHT dht(DHTPIN, DHTTYPE);
U8G2_SSD1306_128X64_NONAME_F_HW_I2C u8g2(U8G2_R0, /* reset=*/ U8X8_PIN_NONE);

// --- VARIABLES ---
volatile int page = 0;          // 0 = Vilnius, 1 = Room
unsigned long lastDebounceTime = 0;
float vilniusTemp = 0;
unsigned long lastWeatherUpdate = 0;

// Button Interrupt: Switches page instantly when pressed
void IRAM_ATTR handleButton() {
  if ((millis() - lastDebounceTime) > 250) { // Debounce 250ms
    page = !page;
    lastDebounceTime = millis();
  }
}

void setup() {
  Serial.begin(115200);
  dht.begin();
  u8g2.begin();
  u8g2.enableUTF8Print(); // Needed for symbols

  pinMode(BUTTON_PIN, INPUT_PULLUP);
  attachInterrupt(BUTTON_PIN, handleButton, FALLING);

  u8g2.clearBuffer();
  u8g2.setFont(u8g2_font_6x10_tf);
  u8g2.drawStr(0, 30, "Connecting WiFi...");
  u8g2.sendBuffer();

  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
}

void fetchWeather() {
  if (WiFi.status() == WL_CONNECTED) {
    HTTPClient http;
    String url = "http://api.openweathermap.org/data/2.5/weather?q=Vilnius,LT&units=metric&appid=" + apiKey;
    http.begin(url);
    if (http.GET() > 0) {
      StaticJsonDocument<1024> doc;
      deserializeJson(doc, http.getString());
      vilniusTemp = doc["main"]["temp"];
    }
    http.end();
  }
}

void loop() {
  // Update weather every 10 minutes (non-blocking)
  if (millis() - lastWeatherUpdate > 600000 || lastWeatherUpdate == 0) {
    fetchWeather();
    lastWeatherUpdate = millis();
  }

  u8g2.clearBuffer();

  if (page == 0) {
    // --- PAGE 0: VILNIUS (OUTSIDE) ---
    u8g2.setFont(u8g2_font_open_iconic_weather_4x_t);
    u8g2.drawGlyph(0, 48, 69); // Cloud icon
    
    u8g2.setFont(u8g2_font_9x15_tf);
    u8g2.drawStr(45, 20, "VILNIUS");
    
    u8g2.setFont(u8g2_font_helvB14_tf);
    String tempStr = String(vilniusTemp, 1) + "°C";
    u8g2.drawUTF8(45, 50, tempStr.c_str());
  } 
  else {
    // --- PAGE 1: ROOM (INSIDE) ---
    float h = dht.readHumidity();
    float t = dht.readTemperature();

    u8g2.setFont(u8g2_font_open_iconic_app_4x_t);
    u8g2.drawGlyph(0, 48, 70); // Home icon
    
    u8g2.setFont(u8g2_font_9x15_tf);
    u8g2.drawStr(45, 20, "INSIDE");
    
    u8g2.setFont(u8g2_font_9x15_tf); // Slightly smaller to fit both
    u8g2.drawUTF8(45, 42, (String(t, 1) + "°C").c_str());
    u8g2.drawUTF8(45, 62, (String(h, 0) + "% Hum").c_str());
  }

  u8g2.sendBuffer();
  delay(100); // Small delay for screen stability
}
```

