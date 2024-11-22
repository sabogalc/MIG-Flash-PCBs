# MIG Flashcart

### NOTE
This board is currently untested. Given my analysis of the board and its similarities to the Dumper (which has been fully tested), I have about 90% certainty that this board will work, but a full test will be conducted in the future.

### Overview
The Flashcart board is very compact, and it would be very challenging to assemble it by hand. Most of the passive components are the 0201 size, and the 0404 RGB LED in the top right is also extremely small. Additionally, the vias have been trimmed down to a 0.2mm size to accommodate the board's routing.

### Ordering Specifications
To ensure this board fits in the game enclosure and that it can be read, it should be ordered as a 0.8mm thick board with an ENIG finish. All other options can be left as their default.

### Component Measurements and BOM Discrepancies
I measured the components to the best of my ability, but there may be slight discrepancies. For example, I found it odd that 12 of the capacitors measured as 0.82uF and 4 of them measured as 0.88uF. I suspect that all of them are 0.82uF, and imperfections in the measurements caused the 4 outliers to read higher values. Even so, they were consistently measuring high enough that I felt it best to mark them as 0.88uF in the schematic. This point is a bit moot, however, because I could not find any 0201 capacitors on either Digikey or Mouser for 0.82uF or 0.88uF. As such, the BOMs have some substitutions, such as 1uF capacitors in place of the 0.82uF and 0.88uF ones, but the measurements in the schematic and PCB are what most align with what I measured in real life.

### Can I use these designs to manufacture my own MIG Flashcart?
The answer is the same as in [the corresponding section of the Dumper's README](https://github.com/sabogalc/MIG-Flash-PCBs/tree/main/KiCad%20Projects/MIG%20Dumper#can-i-use-these-designs-to-manufacture-my-own-mig-dumper). Due to the firmware encryption on the original boards, making this board from scratch (e.g. without transplanting the original μC and FPGA) proves to be a bit of a challenge.

Importantly though, the programmer board schematic I made for the Dumper will not work for the Flashcart as-is since the Flashcart has no 5V/VBUS signal. The programmer board would need to be modified to have an onboard 3.3V regulator, and then with this signal on the Flashcart's VCC breakout signal, it should work. Should anyone make that programmer board and want to write their own firmware, the instructions for accomplishing this can be found on [Espressif's website in the bootloader mode note](https://docs.espressif.com/projects/esp-idf/en/v5.2/esp32s2/api-guides/dfu.html).

### KiCad 3D View
Below are screenshots of the board from KiCad's 3D board viewer.
![MIG Flashcart Front](https://github.com/user-attachments/assets/5ff4c5d8-9a7c-4a3f-b2bb-35ee3b8a732e)
![MIG Flashcart Back](https://github.com/user-attachments/assets/f55e2d2e-1815-43f6-b93c-4e452c501559)