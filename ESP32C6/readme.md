# On MAC
1. Install **esptool **
  ```
  pip install esptool
 ```
2.  Plug your ESP32C36 to your computer
3.  Download this folder on your computer
4.  Right-click on the folder and go to Service > Open Terminal at Folder
5.  To find the port the ESP is connected to type ls /dev/tty.* and hit enter. It will probably look like /dev/tty.usbmodel101 or similar
   ```
  ls /dev/tty.usb*
  ```
6. Copy the string below and replace the /dev/tty.usbmodem101 in the following command with the port address from above and hit enter. 
```
esptool.py -p /dev/tty.usbmodem101 -b 460800 --before default_reset --after hard_reset --chip esp32c6 --no-stub write_flash --flash_mode dio --flash_size 4MB --flash_freq 80m 0x0 bootloader/bootloader.bin 0x8000 partition_table/partition-table.bin 0x10000 micropython.bin
```
