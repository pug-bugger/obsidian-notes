iv.lt prisijungimas:
pugbugpro
650203

Prisijungimo vardas: `pugbugpro`  
Slaptažodis: `K.,BSJu.f%+0^dop`

ID:             8872d38c-f3e1-42b4-bacb-cd55ba1f388a
Host:           w6f5.l.dedikuoti.lt
CPU:            1 unit(s)      
RAM:            1024 MB        
Quota:          10 GB          
IP(s):          195.181.246.48 
Password:       Te7jyUmjCdMntxjh


## Connect via terminal
`ssh root@195.181.246.48`
password above.

# pugbug.eu:22 SSH-2.0-OpenSSH_9.6p1 Ubuntu-3ubuntu13.8
pugbug.eu ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIMYozUJUiQCBkrbXgNY8zfeVBeTXsb7rGngDuoejH1NA



env from /var/www/church-cafe-backend/shared/.env
```
PORT=4000
NODE_ENV=production

DB_HOST=localhost
DB_PORT=3306
DB_USER=church_cafe
DB_PASSWORD=RsZ1Kq0MJqyMOzHg73m7obqR
DB_NAME=church_cafe_db

JWT_SECRET=69d053bc990bed11005cf9f484f750c4697b070f621cd7274f926cfc545bce4718eb0fd5a550705bc9054a090638681b
JWT_EXPIRES_IN=7d

# Both processes are served from one origin, so this is the only allowed one.
CORS_ORIGIN=https://pugbug.fun

UPLOAD_MAX_IMAGE_MB=15

# Network receipt printer (MUNBYN ITPP047P), raw TCP/IP on port 9100.
# Left unset on purpose: the printer sits on the church LAN and a public VPS
# cannot reach a 192.168.x.x address. Printing degrades gracefully - orders are
# still created and staff get a printer:unavailable socket event. To restore
# printing you need a tunnel/VPN back to the church network, then set the host.
PRINTER_HOST=
PRINTER_PORT=9100
```


check mp2 in server:
sudo -u deploy -H pm2 list

change user password:
```bash
cd /var/www/church-cafe-backend/current
npm run set-password -- user@example.com
```


To do
- [ ] update apk app to launch menu page on tv android properly
- [ ] deploy updated app to google play
- [ ] write step by step instruction