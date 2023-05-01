# FLSUN-Cube-Marlin-2.1.2-files
Working Marlin 2.1.2 configuration.h for the FLSUN Cube and MKS SGEN_L V1.0, MKs TFT32_L V4.0, and TMC2209 drivers

# My Configuration
My machine is configured as follows:
<ul>
<li>Original model: FLSUN Cube</li>
<li>Replace original MB with MKS SGEN_L V1.0 board. This board is know as LPC1768 in Marlin</li>
<li>Movement Extremities: X=320, Y=335, Z=355)</li>
<li>Movement Endstops: X=280 (could be set to 300), Y=335, Z=350</li>
<li>Drivers 5*TMC2209 (1=X, 1=Y, 1=Z, 2=Extruders)</li>
<li> *Z uses the FLSUN Driver splitter to run 2 motors for the dual Z leadscrews</li>
<li>Tools: Chimera, Volcano, Single, Laser (manually swapped via DB25 M/F connectors with standardized full pinout cable from MB)</li>
<ul><li>MKS SGEN_L V1.0 Temp sensors used are TM1, TB, TM2</li></ul>
<li>...</li>
<br/>
Other notes about my setup:<br/>
1. My setup uses an induction Z sensor (08N model) and my hotend carriage is completly custom, so you'll need to take these setting into acocunt for you Z sensor offsets as well as your bed dimensions.<br/>
2. My Z offsets are found in the configuration.h file as NOZZLE_TO_PROBE_OFFSETS on LN#1564. Adjust these X=25, Y=10, Z=0 values based on your own measurements because these values take into account my custom swappable hotend carriages and my Z Probe is attached to that housing so when I swap the hotends, I keep the Z Probe on the main carriage.<br/>
3. As much as people think it's futile, you can use Z_SAFE_HOMING with a fixed sled Z Probe and having home set to the bed center as is done in this configuration.h file.<br/>
4. I'm using Bilinear ABL (9 touch points).<br/>

# Instructions to setup TMC2209 Drivers
Set the drivers up to use UART and you will not need to make any changes in your configuration_adv.h file.<br/>
No need to cut pins, jump wires, or do anything more than plugin them in (in the correct orientation of course) if you use the default UART (not Standalone) mode.<br/>
The configuration.h file is already set up to make use of the TMC2209 drivers for X, Y, Z, E0, and E1 - all in conjunction with the FLSUN.<br/>
You'll need to install Visual Studio code on your computer to compile all this and save it as a file named firmware.bin on your computer.<br/>
You'll then copy that file to an SD card, insert that SD card into your port on the MKS SGEN_L V1.0 MB and power on the printer.<br/>
If the configuration does not take, you'll need to open Pronterface (or whatever GCODE terminal you use):
<li>Enter G502 to clear the MB settings, then</li>
<li>Enter G500 so save the curent settings to the EEPROM on the MKS SGEN_L V1.0 MB</li>
