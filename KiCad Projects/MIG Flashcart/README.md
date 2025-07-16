# MIG Flashcart

### Overview
The Flashcart board is very compact, and it is a bit challenging to solder it by hand. Most of the passive components are the 0201 size, and the 0404 RGB LED in the top right is also extremely small. Additionally, the vias have been trimmed down to a 0.2mm size to accommodate the board's routing.

A series of leaks in July 2021 made the low-level hardware of the Switch game cartridge reader public, and it is powered by an ASIC called [Lotus3](https://switchbrew.org/wiki/Lotus3). I don't know much about how this chip/protocol works, but the FPGA and microcontroller in this flashcart are programmed to communicate on this custom interface. 

### Ordering Specifications
To ensure this board fits in the game enclosure and that it can be read, it should be ordered as a 0.8mm thick board with an ENIG finish. All other options can be left as their default.

### Component Measurements and BOM Discrepancies
I measured the components to the best of my ability, but there may be slight discrepancies. For example, I found it odd that 12 of the capacitors measured as 0.82uF and 4 of them measured as 0.88uF. I suspect that all of them are 0.82uF, and imperfections in the measurements caused the 4 outliers to read higher values. Even so, they were consistently measuring high enough that I felt it best to mark them as 0.88uF in the schematic. This point is a bit moot, however, because I could not find any 0201 capacitors on either Digikey or Mouser for 0.82uF or 0.88uF. As such, the BOMs have some substitutions, such as 1uF capacitors in place of the 0.82uF and 0.88uF ones, but the measurements in the schematic and PCB are what most align with what I measured in real life.

### Can I use these designs to manufacture my own MIG Flashcart?
The answer is the same as in [the corresponding section of the Dumper's README](https://github.com/sabogalc/MIG-Flash-PCBs/tree/main/KiCad%20Projects/MIG%20Dumper#can-i-use-these-designs-to-manufacture-my-own-mig-dumper). Due to the firmware encryption on the original boards, making this board from scratch (e.g. without transplanting the original μC and FPGA) proves to be a bit of a challenge.

Importantly though, the programmer board schematic I made for the Dumper will not work for the Flashcart as-is since the Flashcart has no 5V/VBUS signal. The programmer board would need to be modified to have an onboard 3.3V regulator, and then with this signal on the Flashcart's VCC breakout signal, it should work. Should anyone make that programmer board and want to write their own firmware, the instructions for accomplishing this can be found on [Espressif's website in the bootloader mode note](https://docs.espressif.com/projects/esp-idf/en/v5.2/esp32s2/api-guides/dfu.html).

I have assembled this board with parts from the included BOM and confirmed that it works when using the chips from an OEM MIG Flashcart. If you are using the parts from the BOM, the LED has a pin 1 indicator which I will show in a photo below. Make sure that the white squre between the two gold pins is facing into the board towards the crystal oscillator.

![WIN_20250714_21_31_24_Pro](https://github.com/user-attachments/assets/dfadd25d-0b1e-4dcc-b8bd-2c9bc6971996)


Below are some photos of the board from this repository in the flashcart enclosure.

![PXL_20250715_021333887](https://github.com/user-attachments/assets/e6a34638-6de8-4230-8c75-d49f5e133ad6)
> ![PXL_20250715_020342484](https://github.com/user-attachments/assets/41d951fd-2634-4fd2-872b-caa6cc148cf1)
> The cartridge reading a game in the Switch and showing a green status LED.


### KiCad 3D View
Below are screenshots of the board from KiCad's 3D board viewer.
![MIG Flashcart Front](https://github.com/user-attachments/assets/5ff4c5d8-9a7c-4a3f-b2bb-35ee3b8a732e)
![MIG Flashcart Back](https://github.com/user-attachments/assets/f55e2d2e-1815-43f6-b93c-4e452c501559)