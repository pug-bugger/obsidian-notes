Create branch and pull changes form master and partial.
get last sprint commit id
![[Pasted image 20250319160224.png]]
copy id from url
![[Pasted image 20250319160230.png]]

use this command to find differences
```
sf sgd:source:delta --to origin/patches_03-18 --from 09c8c4df9b21e1904df062157acc612ce08981f8 --output "./manifest"
```
and then 
```
sf force source deploy -x ./manifest/package/package.xml
```

