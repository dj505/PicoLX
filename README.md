# PicoLX
The cooler PicoFX :sunglasses:  
This README will be updated over time as the project is worked on and tested.

# Foreword
### This project assumes you're not a first time builder! If you are, consider building a [PicoFX](https://github.com/dj505/PicoFX) instead.
If you're comfortable with using PCB assembly services and potentially doing some fine soldering, or have a friend who can do the above, consider going that route instead.  

# Changes
## Improvements
The PicoLX has a few significant upgrades over the PicoFX, such as:
* Native USB C - no more flimsy MicroUSB port
* Full RGB - every key now has an RGB LED, with extra LEDs illuminating the logo
* Kailh hotswap sockets - use whatever switches you want, whenever you want
* Aesthetics - it looks way cooler, with a brand new logo and redesigned top plate inspired by the Pump it Up LX cabinet artwork

## Drawbacks
* Dozens of very tiny surface mount components are now required, which are very difficult to solder by hand
* PicoFX firmware may or may not be compatible; this remains to be seen
* This project has a higher overall cost than the PicoFX due to the higher complexity of the build

# Required KiCAD Libraries
If you want to fork and/or modify this project, you can find the libraries required to do so here:
* [Raspberry Pi "Minimal" RP2040 files](https://datasheets.raspberrypi.com/rp2040/Minimal-KiCAD.zip)
* [ai03's MX V2 footprints](https://github.com/ai03-2725/MX_V2) (Clone as submodule)
    * For the actual PCB footprints
* [ai03's MX Alps Hybrid footprints](https://github.com/ai03-2725/MX_Alps_Hybrid) (Clone as submodule)
    * For the schematic symbols, as they're not part of the V2 library
* [marbastlib keyboard parts](https://github.com/ebastler/marbastlib) (Clone as submodule)
    * For the SK6812 schematic symbols and footprints

# Bill of Materials
Below is a list of materials required for 1 controller.  
**Read the notes after this table.** There are important clarifications.  

|        Component       | Footprint | Qty |  LCSC #  | Link | Assembly Recommended? |
|------------------------|-----------|-----|----------|------|-----------------------|
| 100nF Capacitor        | 0402      | 10  | C1525    | N/A  | Y                     |
| 1uF Capacitor          | 0402      | 2   | C52923   | N/A  | Y                     |
| 27pF Capacitor         | 0402      | 2   | C1557    | N/A  | Y                     |
| 100uF Capacitor        | 0804      | 19  | C15008   | N/A  | Y                     |
| USB C Receptor         | N/A       | 1   | C2988369 | N/A  | Y                     |
| SK6812MINI-E LED\*     | N/A       | 19  | N/A      | N/A  | N                     |
| MX-style keyswitch\*   | N/A       | 10  | N/A      | N/A  | N                     |
| Kailh hotswap socket\* | N/A       | 10  | N/A      | N/A  | N                     |
| 1k Ohm Resistor        | 0402      | 2   | C106235  | N/A  | Y                     |
| 27 Ohm Resistor        | 0402      | 2   | C2909343 | N/A  | Y                     |
| 5.1k Ohm Reistor       | 0402      | 2   | C25905   | N/A  | Y                     |
| TS-1187A Pushbutton    | N/A       | 1   | C318884  | N/A  | Y                     |
| 90 Degree Pushbutton   | N/A       | 2   | C221887  | N/A  | N                     |
| RP2040                 | QFN-56    | 1   | C2040    | N/A  | Y                     |
| W25Q32JVSS             | SOIC-8    | 1   | C82344   | N/A  | Y                     |
| NCP1117-3.3            | SOT-223-3 | 1   | C146799  | N/A  | Y                     |
| SN74LV1T34DBV          | SOT23-5   | 1   | C100024  | N/A  | Y                     |
| 12.000MHz Crystal      | 3225-4Pin | 1   | C9002    | N/A  | Y                     |

\* Recommended to source on your own  

### Notes:
* Unless you have a hot air station, **PCB assembly services will save you a lot of trouble!** These components are VERY small and trying to solder them by hand with an iron will give you a bad time.
* For your keyswitches to properly illuminate, makes sure you use switches with a **clear or translucent housing.**
* I recommend soldering through-hole parts on your own to save on assembly costs, since they're easy.
* There are a few components not listed that typically aren't needed. If you would like to include these for peace of mind, you can find them by cloning the project and viewing the list of symbols in the schematic.
