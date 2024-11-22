# MIG Dumper

### Overview
This is a very straightforward board design. The FPGA is is the first point of contact with the cartridge, and it takes care of direct communication with the data and clock lines in order to be able to read the onboard cartridge data. The microcontroller then takes this data from the FPGA, and it relays it to the SD card to USB adapter, presumably through SPI (reference [here](https://switchbrew.org/wiki/Gamecard#Protocol)). With data moving to and from the FPGA/microcontroller in SPI, it is very simple to configure the board as if it were reading an SD card, after which the dumper allows the files to be read by any USB-enabled device.

### Ordering Specifications
The original board is a standard 1.6mm thick board, and all other options (soldermask, surface finish, etc.) can be customized to your liking. Please note that if you are using the OEM enclosure, the 4.7uF capacitor for C29 in the included Digikey/Mouser BOMs is too tall to allow for it to fully close. The capacitor on the original board is 0.85mm tall, but the one I included is 1.6mm tall.

### Component Measurements and BOM Discrepancies
I measured the components to the best of my ability, but there may be slight discrepancies. For example, the aforementioned 4.7uF capacitor was read in real life to be 4.5uF, but I could not find a 1206 4.5uF capacitor on either Digikey or Mouser. As such, the BOMs have some substitutions, such as 100nF capacitors instead of 110nF capacitors, but the measurements in the schematic and PCB are what most align with what I measured in real life. For capacitors in the pF range that I could not measure, I referenced the datasheets for the [ECS-400-10-37B2-CKY-TR](https://ecsxtal.com/store/pdf/ECX-1637B2.pdf) and [MAX20022ATIA+](https://www.analog.com/media/en/technical-documentation/data-sheets/max20021-max20022.pdf) to obtain these values.

Additionally, the SD card to USB adapter chip and the cartridge reader are not present in the BOMs because neither part is available on Digikey or Mouser, but you can purchase both of them from AliExpress.

[GL823K-HCY04 chip](https://www.aliexpress.com/item/3256805047594623.html)

[Cartridge reader](https://www.aliexpress.com/item/3256804487003304.html)

### Can I use these designs to manufacture my own MIG Dumper?
Yes and no. I have succesfully transplanted all the parts of an original Dumper to this PCB, and it works perfectly. Building it from scratch with the parts from the included `.csv` and `.xlsx` BOMs does not work, but if you substitute in an OEM FPGA and ESP32, then it works. This is because the firmware for these chips is programmed and encrypted at the factory, as specified in the main landing page's `README`.

While it may be possible to break this encryption (see [here](https://hackaday.com/2024/01/15/breaking-the-flash-encryption-feature-of-espressifs-microcontrollers/)), I am a hardware engineer and not very interested in delving into the firmware side of things. However, I will include a schematic for a programmer board below should anyone want to embark on that journey. The instructions for the boot sequence needed are found at https://docs.espressif.com/projects/esp-idf/en/v5.2/esp32s2/api-guides/dfu.html in the bootloader mode note.

![Programmer Schematic](https://github.com/user-attachments/assets/8a2aebe1-cfdf-4c0c-950c-3228ec176417)


Below is a photo of the board from this repository screwed into the enclosure and reading a gamecard.
![MIG Dumper in enclosure](https://github.com/user-attachments/assets/2d17e25d-7f2f-41b9-9f3d-f410cb2be924)


### KiCad 3D View
Below are screenshots of the board from KiCad's 3D board viewer.
![MIG Dumper Front](https://github.com/user-attachments/assets/abeef0b2-bc1b-488a-9de0-0a4f166f5a97)
![MIG Dumper Back](https://github.com/user-attachments/assets/9fdab72f-ced8-4a40-b066-0036c76ccaaa)