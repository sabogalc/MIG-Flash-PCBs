# MIG Flash PCBs
This repository hosts KiCad projects of the MIG Dumper and Flashcart PCBs. These files should prove very useful towards understanding the inner workings of the devices, especially with the schematics and boardview files. As-is, not much can be done with the board files since the original boards are programmed at the factory. The only way to currently get a working board from these files is by transplanting at minimum the FPGA and the microcontroller from an OEM MIG device to the new board.

> ![IMG-20241018-063244](https://github.com/user-attachments/assets/9da3f7e0-b5c1-410c-b6fc-eb0e8665748b)
> The 8 pins seen above the USB-C port and to the right of the microcontroller in this photo are the ones used to program the board at the factory (see https://docs.espressif.com/projects/esp-idf/en/v5.2/esp32s2/api-guides/dfu.html for more information)

> ![PXL_20250715_021333887](https://github.com/user-attachments/assets/e6a34638-6de8-4230-8c75-d49f5e133ad6)
> The flashcart PCB inside of the game enclosure.

Another useful resource found in this repo is the bill of materials for both devices. If you have a MIG device but a part on it has gone bad or is missing, this repository should assist with finding replacement resistors or capacitors of the correct value, or finding part numbers for components such as the toggle button on the Flashcart. For more information on either board, see their folders in the `KiCad Projects` directory.