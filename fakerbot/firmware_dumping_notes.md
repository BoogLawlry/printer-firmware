#!/bin/bash
#Note: to flash the Arduino Mega (ATmega 2560)
#avrdude -p m2560 -c stk500v2 -P /path/to/serial -b 115200 -F -U flash:w:/path/to/image.hex

#Note: Makerbot Replicator (Mightyboard) has a ATmega1280
baud=115200
avr=m1280
dst=$avr.`date +"%Y%m%d_%H%M%S"`
port=/dev/ttyUSB0

#Flashing bootloader to mightyboard
#avrdude -C avrdude.conf -p m1280 -F -P usb -c usbtiny -U flash:w:bootloader/1280_bootloader/ATmegaBOOT_168_atmega1280.hex -U lfuse:w:0xFF:m -U hfuse:w:0xDA:m -U efuse:w:0xF4:m -U lock:w:0x0F:m


# calibration  One or more bytes of RC oscillator calibration data.
# eeprom       The EEPROM of the device.
# efuse        The extended fuse byte.
# flash        The flash ROM of the device.
# fuse         The fuse byte in devices that have only a single fuse byte.
# hfuse        The high fuse byte.
# lfuse        The low fuse byte.
# lock         The lock byte.
# signature    The three device signature bytes (device ID).
# fuseN        The fuse bytes of ATxmega devices, N is an integer number for each fuse supported by the device.
# application  The application flash area of ATxmega devices.
# apptable     The application table flash area of ATxmega devices.
# boot         The boot flash area of ATxmega devices.
# prodsig      The production signature (calibration) area of ATxmega devices.
# usersig      The user signature area of ATxmega devices.

for memory in calibration eeprom efuse flash fuse hfuse lfuse lock signature application apptable boot prodsig usersig; do
        avrdude -p $avr -c stk500v2 -P $port -b $baud -U $memory:r:/dev/stdout:i > ./$dst.$memory.hex ||
                rm ./$dst.$memory.hex
done