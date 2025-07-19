# Co-Print-SV08-Config
Co-Print SV08 Config pack

<a href='https://ko-fi.com/T6T517TCF6' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi6.png?v=6' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

# this will get you to a working starting point. anything else you will need to work on. please use the issues tab to let me know of any fixes that should be made. good luck. sorry for the sub-par how to. 

# !!!you must redo your PA test!!!


# replacement all your files with these. I have fix a few additional things. I suggest downloading all your files before hand. 

![image](https://github.com/user-attachments/assets/c46ed2b1-ccfb-4434-84ff-c1df7f16b2c0)

if you have issue with homing lower this setting 

```driver_sgthrs: 65```

use the offical wiki for more help:
https://wiki.coprint3d.com/orcaslicer
https://github.com/coprint

for going mainline:
https://github.com/Rappetor/Sovol-SV08-Mainline

if you have more then 4 you need the ecm_1.cfg from here

https://github.com/Val-dose-things/configs

#here are some modles i made to help fix issues with the stock options.

https://www.printables.com/model/1099879-coprint-sv08-bracket-upgrade
---------------------------

you should update the devices to
use /dev/serial/by-id/

Unplug the KCM usb and then run this in the ssh shell.

```ls -la /dev/serial/by-id/```
This will show the host mcu

Then plug in the KCM with the toolhead disconnected

```ls -la /dev/serial/by-id/```
The new one is the kcm mcu

Plug in the toolhead

```ls -la /dev/serial/by-id/```
This will show the toolhead mcu.

![482081274_1935388256864842_4292328743022954373_n](https://github.com/user-attachments/assets/e5e69390-d015-4c42-af3b-f177bbb7415c)
![481957638_1935388526864815_1304757567423387391_n](https://github.com/user-attachments/assets/215391a9-d271-4905-8d6e-a1f0cf646454)
![483917301_1935388723531462_1055497483776585922_n](https://github.com/user-attachments/assets/1a6300e8-9b05-4c00-b187-564002229834)

-------------------

you will need to use this in your slicer start gcode.
```
G28
G90
T{initial_extruder}
SET_HEATER_TEMPERATURE HEATER=extruder TARGET=150
M140 S[bed_temperature_initial_layer_single] ;set bed temp
M190 S[bed_temperature_initial_layer_single] ;wait for bed temp

HEATSOAK

START_PRINT EXTRUDER=[initial_extruder]

G92 E0.0 ; reset extruder
G1 X{first_layer_print_max[0]-80} Y{first_layer_print_max[1]+10} Z0.8 F6000.0 ; position 10mm behind print
M104 S[nozzle_temperature_initial_layer] ;set extruder temp
M109 S[nozzle_temperature_initial_layer];wait for extruder temp
M400

G1 E121 F600 ; set filament 
G92 E0.0 ; reset extruder
G1 X{first_layer_print_max[0]-80} Y{first_layer_print_max[1]+10} Z0.8 F6000.0 ; position 10mm behind print
G1 X{first_layer_print_max[0]-120} Y{first_layer_print_max[1]+10} E50 F360.0 ; extrude 60mm of filament in the x direction
G92 E0.0 ; reset extruder
G1 X{first_layer_print_max[0]-120} Y{first_layer_print_max[1]+7} Z0.8 F6000.0 ; position 7mm behind print
G1 X{first_layer_print_max[0]-80} Y{first_layer_print_max[1]+7} E50 F360.0 ; extrude 60mm of filament in the x direction
G92 E0.0 ; reset extruder
G1 E-0.5 F2100 ; small retraction
G1 X{first_layer_print_max[0]-40} F6000.0 ; move an additional 10mm without extruding
G92 E0.0 ; reset extruder

```
also add 

In Layer change Gcode add:
```SET_PRINT_STATS_INFO CURRENT_LAYER={layer_num + 1}```

and

In Change filament Gcode add:
```FILAMENT_CHANGE LAYER_NUM=[layer_num] NEXT_EXTRUDER=[next_extruder]```

update the following in orca

![image](https://github.com/user-attachments/assets/5b50e0ec-133e-4502-a620-4fecfcaa50c7)

![image](https://github.com/user-attachments/assets/e09d8b17-201c-4d35-b1d2-fed8ed58c63d)

open the others folder here(https://github.com/Val-dose-things/Co-Print-SV08-Config/tree/main/other). download them on to your compute.
for the backup-mainsail.json go to settings and restore. this will geve you a better lay out for the macros. 

![image](https://github.com/user-attachments/assets/9809aca9-20bd-45c0-b9a3-3022e0cd867e)
![image](https://github.com/user-attachments/assets/2b44681d-eef4-4a0a-b7ed-48b44488b696)

copy the coprint_zoffset_test.gcode in to the gcode directly.
rename it with as ".coprint_zoffset_test.gcode" this will make it a hidden file and keep you from deleting it when you clear out your files. 
This will replace the stock one from sovol and have a PA in a range and settings that should not grind your extruder to dust. 

![image](https://github.com/user-attachments/assets/d9d93382-2933-41f0-8d59-f8932a1a5700)

to get input shaper working you need to switch to mainline or use the BIGTREETECH S2DW V1.0 USB C input shaper. its plug and play.

verify this section if on mainline 
```
[printer]
kinematics: corexy           
max_velocity: 700            
max_accel: 40000             
#max_accel_to_decel: 10000 ; comment out for mainline
minimum_cruise_ratio: 0.5 ; use on mainline only
max_z_velocity: 20           
max_z_accel: 500             
square_corner_velocity: 5.0  
```




