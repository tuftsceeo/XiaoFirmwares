Open Terminal
Type ls/dev/tty.* and hit enter
find the serial port for your esp32c6 - most likely /dev/tty.usbmodem101 or similar
Now cd yourself into the firmware folder
and run the command below



esptool.py -p /dev/tty.usbmodem101 -b 460800 --before default_reset --after hard_reset --chip esp32c6 --no-stub write_flash --flash_mode dio --flash_size 4MB --flash_freq 80m 0x0 bootloader/bootloader.bin 0x8000 partition_table/partition-table.bin 0x10000 micropython.bin


