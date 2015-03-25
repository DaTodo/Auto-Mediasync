# Auto-Mediasync
To automatically mount and rsync media onto ubuntu server

```
#!/bin/bash

sudo mount /dev/sdg1 /media/center
if grep -qs '/media/center' /proc/mounts; then
        sleep 5
        sudo rsync -rvP --ignore-existing /media/center/TV\ Shows/ /home/korey/Videos/TV\ Shows/
        sudo rsync -rvP --ignore-existing /media/center/Movies/ /home/korey/Videos/Movies/
     else
        echo "System not mounted"
        exit 1
fi

sudo umount /media/center
sleep 5

if grep -qs '/media/center' /proc/mounts; then
        echo "System is still mounted,!!DO NOT EJECT!!"
     else
         echo "System has been successfully, synced and unmounted"
fi
```
