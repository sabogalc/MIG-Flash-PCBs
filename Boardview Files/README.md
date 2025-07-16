# Boardview Files

## What is a Boardview File?

A boardview file is a netlist of all the connections on a PCB with every component laid out exactly as it is in real life. This modern approach provides a more intuitive way to inspect connections and troubleshoot PCBs compared to traditional schematic diagrams.

## How Can I View These Files?

Much like how there are many PCB EDA software programs out there, there are also many board viewing programs. The two that I have used and recommend are listed below:

1. **[OpenBoardView](https://github.com/OpenBoardView/OpenBoardView)**  
   - **License:** MIT  
   - **Description:** An open-source tool for viewing boardview files. It provides essential features for inspecting PCB layouts.

2. **[FlexBV](https://pldaniels.com/flexbv/)**  
   - **License:** Commercial (free version available)  
   - **Description:** A commercial tool with advanced features for viewing and analyzing boardview files. The free version offers most of the basic functionalities.

### Example View

Below is a screenshot of the MIG Dumper boardview as viewed in FlexBV:

![MIG Dumper Boardview](https://github.com/user-attachments/assets/dca6e702-eea0-4680-b63f-dadacdd8fe62)

In this view, you can observe the following:
- **Net Highlighting:** The +3V3 net is highlighted in green across the board.
- **Component Table:** A table on the right lists components and their pin numbers associated with +3V3.
- **Designator Information:** The designators, values of resistors and capacitors, and component footprints are all displayed.

### Note on Metadata

The metadata you see (e.g., component values, designators) is stored in the `.obdata` file. As of July 2025, this metadata is viewable only in FlexBV. The `.obdata` format is [open and documented](https://openboarddata.org/), and I would very much like to see the feature added to OpenBoardView.

### How Can I Create Boardview Files for My Own Designs?

All of the boardview files I make for my projects are using [an open-source KiCad plugin](https://github.com/whitequark/kicad-boardview). When I first came across this plugin, it had a few bugs with current versions of KiCad, so I submitted some pull requests and the plugin is back into perfect operating condition.