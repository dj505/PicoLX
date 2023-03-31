# PicoLX
The cooler PicoFX :sunglasses:  
This README will be updated over time as the project is worked on and tested.  

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Y8Y8106HR)

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
| 100uF Capacitor        | 0805      | 19  | C437555  | N/A  | Y                     |
| 10uF Capacitor         | 0402      | 2   | C15525   | N/A  | Y                     |
| USB C Receptor         | N/A       | 1   | C2988369 | N/A  | Y                     |
| SK6812MINI-E LED\*     | N/A       | 19  | N/A      | N/A  | N                     |
| MX-style keyswitch\*   | N/A       | 10  | N/A      | N/A  | N                     |
| Kailh hotswap socket\* | N/A       | 10  | N/A      | N/A  | N                     |
| 1k Ohm Resistor        | 0402      | 2   | C11702   | N/A  | Y                     |
| 27 Ohm Resistor        | 0402      | 2   | C25100   | N/A  | Y                     |
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

# Ordering PCBs
The gerber files for both PCBs are available in this repository, however the BOM/pick and place files for PCB assembly services are not. You'll have to generate these yourself if you plan to use them. Here's how:

### Main PCB
1. Install [KiCAD](https://www.kicad.org/)
2. Clone this repository and its submodules to your PC
3. Open KiCAD and navigate to the "Plugin and Content Manager" window
4. Download the appropriate plugin for the fab house you plan to use:
    * "Fabrication Toolkit" for JLCPCB
    * "PCBWay Plug-in for KiCad" for PCBWay
5. Open the PicoLX project file in the "MainPCB" folder and set up the component properties in the schematic editor appropriately. **These steps may require manual part sourcing - double check all the components and footprints are appropriate matches.**
    * For JLC orders, set up the compoent properties according to their [support page](https://support.jlcpcb.com/article/84-how-to-generate-the-bom-and-centroid-file-from-kicad). Once you reach the "Generating Pick and Place files" step, stop - you'll be using the Fabrication Toolkit to do this automatically.
    * For PCBWay orders, configure the component properties according to the example shown on their [PCBWay plugin blog post.](https://www.pcbway.com/blog/News/PCBWay_Plug_In_for_KiCad_3ea6219c.html)
    * **Optional:** customize the PCB to your liking. You can change up the text, add graphics to the silkscreen layer, and so on. Doing so will require you to create a new gerber file.
6. Open the PCB editor and look for the icon that matches the plugin you installed. Click it and let it process.
    * The JLC fabrication toolkit plugin will create a "production" folder that contains a gerber.zip as well as the BOM/CPL (pick-and-place/position) csv files. See [JLCPCB's SMT assembly page](https://jlcpcb.com/smt-assembly) for basic information on using these files.
    * The PCBWay plugin will create a zip file containing the gerber files, BOM, and pick-and-place files, then automically open this zip in the "Instant Quote" page.
    * If the gerber files generated by either of the above processes do not look right, use the known good ones I've included in this repository.
7. On your chosen PCB manufacturer's website, select your desired solder mask colour and finish, and select the PCB assembly option if necessary.
    * For JLCPCB orders, ensure the part numbers shown in the component selection step match the BOM in this readme, or in the component properties window. I've made sure these part numbers are made up of "basic" component library parts to save on extended parts fees as much as possible.
    * I recommend **excluding a few parts from the assembly process.** See the above table in the [Bill of Materials](#bill-of-materials) section. These items will need to be sourced and purchased separately, and soldered by hand. You can either edit the BOM before uploading to remove these components, or deselect them on the manufacturer's website as part of the order process.
    * JLC sometimes mixes up component orientation. **Pin 1 is designated by a pink dot. Please be sure to double, triple, and quadruple check the following:**
        * The RP2040 (designated U1) should have pin 1 at the **upper left corner**
        * The clock crystal (designated Y1) should have pin 1 at the **lower left corner**
        * The SPI flash chip (designated U2) should have pin 1 at the **lower left corner**
        * The logic level inverter (designated U4) should have pin 1 at the **upper left corner**
        * If the components do not line up with the pads or are backwards (i.e. the USB port or voltage regulator), click the "Align" button.
        * Most other components are passive components where orientation doesn't matter, or have an obviously correct orientation that ensures any mistakes are caught before manufacturing.

### Plate
1. Upload the gerber file for the plate to your manufacturer of choice.
    * This part does not require PCB assembly services, only PCB manufacturing.
2. Select your desired soldermask colour.
3. Select your desired finish. There will be exposed finish as an part of the design, so I would recommend selecting the __**lead-free**__ **HASL finish** or the **Immersion gold (ENIG)** finish. I would not recommend using a finish that contains lead for a plate with exposed metal!
4. Add the order to your cart.

### Once both parts are in your cart
You're ready to place the order! Ensure all of the information is correct, and be prepared to wait some time. Manufacturing and assembly takes a few days to a week. Shipping times vary.

# Assembly
If you used a PCB assembly service for the majority of the parts, the remainder is very straightforward. If not, I'm going to assume you own a hot air soldering station and have enough of an idea of what you're doing that you don't need a step by step guide.
1. Match the LEDs on one side with their solder pads, ensuring the leg with the notch matches the marking on the silkscreen. Flip the board and repeat for the remaining LEDs.
2. Slot the hotswap sockets in place and solder the tabs to the rectangular pads.
3. Insert and solder the test and service buttons. Ensure these are pointing out from the back of the PCB so as to not collide with the top plate.
4. Snap a few of your keyboard switches into the plate. Not all of them yet - just 2 or 3 in opposing corners are a good start. Use these to align the main PCB and insert the switches into the sockets.
5. Insert the remainder of the switches and make sure everything is properly aligned. You can always fix this later as the switches aren't permanently soldered in.
6. Slot the assembly into the 3D printed case and screw together.
7. Attach some rubber non-slip feet or a non-slip pad that's been cut to size to the bottom of the case.
8. Flash the firmware and play!

# Firmware
// TODO
