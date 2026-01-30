- In order to find the part number of the Jetson module, it is usually stored in the module's eeprom. Refer the [docs](https://docs.nvidia.com/jetson/archives/r36.2/DeveloperGuide/HR/JetsonEepromLayout.html) to find the exact byte position of the part number.
- NVIDIA exposes the EEPROM through sysfs, as i2c will be blocked(the EEPROM driver will be used by the kernel components)
- Locate EEPROM device
```
ls /sys/bus/i2c/devices/0-0050/
```
- Dump the EEPROM safely
```
sudo hexdump -C /sys/bus/i2c/devices/0-0050/eeprom | less
```
- Extract specific bytes if required
```
sudo dd if=/sys/bus/i2c/devices/0-0050/eeprom bs=1 skip=20 count=30 2>/dev/null | strings
```
- The output should be the part number, refer the above mentioned docs to infer the output.