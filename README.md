# Co-Print-SV08-Config
Co-Print SV08 Config pack

use the offical wiki for more help.
https://wiki.coprint3d.com/orcaslicer

here are some modles i made to help fix issues with the stock options.

https://www.printables.com/model/1099879-coprint-sv08-bracket-upgrade

https://www.printables.com/model/1108791-sv08-coprint-mount-light

you will need to use this in your slicer

G28
G90
G1 X175 F9000
G1 Y175
G1 Z0.800 F600
SET_HEATER_TEMPERATURE HEATER=extruder TARGET=150
M140 S[bed_temperature_initial_layer_single] ;set bed temp
M190 S[bed_temperature_initial_layer_single] ;wait for bed temp
START_PRINT
G92 E0.0 ; reset extruder
G1 X{first_layer_print_max[0]-90} Y{first_layer_print_max[1]+10} Z0.8 F6000.0 ; position 10mm behind print.
M104 S[nozzle_temperature_initial_layer] ;set extruder temp
M109 S[nozzle_temperature_initial_layer];wait for extruder temp

G1 E100 F600
M400
G92 E0.0 ; reset extruder
G1 X{first_layer_print_max[0]-80} Y{first_layer_print_max[1]+10} Z0.8 F6000.0 ; position 10mm behind print.
G1 X{first_layer_print_max[0]-120} Y{first_layer_print_max[1]+10} E40 F360.0 ; extrude 40mm of filament in the x direction
G92 E0.0 ; reset extruder
G1 E-0.5 F2100 ; small retraction
G1 X{first_layer_print_max[0]-40} F6000.0 ; move an additional 10mm without extruding
G92 E0.0 ; reset extruder

add this to here

0x0, 22x0, 22x350, 0x350, 0x0, 350x0, 350x1, 0x1, 0x340, 350x340, 350x350, 0x350

![image](https://github.com/user-attachments/assets/54b55204-f05c-4227-b9a3-400c92882be9)

this will keep you from printing in parts of the printer you really dont want to.(until someone makes a compleate redesign that centers the nozzle. not me i cant moddle that well.)

![image](https://github.com/user-attachments/assets/e0abb280-f721-466f-a8e4-c584cce7c71c)

in the others folder you should make these changes. 
for the backup-mainsail.json go to settings and restore. this will geve you a better lay out for the macros. 

![image](https://github.com/user-attachments/assets/9809aca9-20bd-45c0-b9a3-3022e0cd867e)
![image](https://github.com/user-attachments/assets/2b44681d-eef4-4a0a-b7ed-48b44488b696)



copy the coprint_zoffset_test.gcode in to the 
![image](https://github.com/user-attachments/assets/d9d93382-2933-41f0-8d59-f8932a1a5700)
rename it with a ".coprint_zoffset_test.gcode" this will make it a hidden file and keep you from deleting it when you clear out your files. 
This will replace the stock one from sovol and have a PA in a range and settings that should not grind your extruder to dust. 
