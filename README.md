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

