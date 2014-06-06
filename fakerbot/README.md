Download Possible Firmwares
----------------------------
* Sailfish: https://github.com/jetty840/Sailfish-G3Firmware

        git clone https://github.com/jetty840/Sailfish-G3Firmware.git

* Makerbot: https://github.com/makerbot/MightyBoardFirmware

        git clone https://github.com/makerbot/MightyBoardFirmware.git


List avr chips supported by avrdude
-----------------------------------

        printer-firmware/fakerbot$ avrdude -c avrisp

m1280    = ATmega1280

Flashing bootloader to mightyboard
-----------------------------------

        avrdude -C avrdude.conf -p m1280 -F -P usb -c usbtiny -U flash:w:bootloader/1280_bootloader/ATmegaBOOT_168_atmega1280.hex -U lfuse:w:0xFF:m -U hfuse:w:0xDA:m -U efuse:w:0xF4:m -U lock:w:0x0F:m

Related Links
--------------
* avrdude tutorial: http://www.ladyada.net/learn/avr/avrdude.html
* avrdude gui: http://blog.zakkemble.co.uk/avrdudess-a-gui-for-avrdude/
* wanhao flashing guide: http://www.wanhao3dprinter.com/news.aspx?cid=2013040002