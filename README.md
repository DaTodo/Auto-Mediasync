# Auto-Mediasync
To automatically mount and rsync media onto ubuntu server

1. Install usbmount
  
  ```
  sudo apt-get install usbmount
  ```
  
2. Give Permission and allow users
  
  ```
  lsblk //find device
  chmod 777 /dev/sdx
  sudo sed -in '0,/MOUNTOPTIONS="/s/MOUNTOPTIONS="/MOUNTOPTIONS="user,umask=000,/' /etc/usbmount/usbmount.conf
  ```
  
3. Running Script After Mount

  ```
  vim /etc/udev/010custom.rules
  lsusb //to find ID and PRODUCT, DEVICE can be user defined
  BUS="usb", SYSFS{idVendor}="**IDVENDOR**", SYSFS{product}="**PRODUCT**", NAME="usb/%k", SYMLINK="DEVICE", RUN+="/path/to/your/script-to-sync-media"
  ```
