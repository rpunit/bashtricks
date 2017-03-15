# BASHtricks
Some tips and tricks I use for when using bash

## 1. Safe Remove.
  Ever done a rm -f dir/. *  instead of rm -f dir/.* (notice the space between . and *)
  
  I did that several times and it was painful. These few will save you.
  
  In your profile .bashrc
    put his line :   ```alias rm='set -f;srm'; srm() { ~/scripts/safe_rm.sh "$@";set +f;}```
    
   And this goes in your safe_rm.sh
   
```   #!/bin/sh
for arg in "$@"; do
    if [[ $arg == "*" ]]; then
        echo "Stray * found in the rm args. Exiting "
        exit 1
    fi
done
rm $@
```

Credits 
  1. [stackoverflow]( http://stackoverflow.com/questions/11456403/stop-shell-wildcard-character-expansion)
---
