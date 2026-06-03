


```
import { translationStore } from "c/translationStore";
```

```
translationStore.sub(this.translationClb);
this.translationClb();

translationStore.unsub(this.translationClb);
```

```
translationGroup = "truckList";
  searchTruckHolderText = null;
  translationClb = () => {
    const translations = translationStore.getGroup(this.translationGroup) ?? {};
    this.searchTruckHolderText = translations.truck_label ?? "Search Trucks:";
  }
```
