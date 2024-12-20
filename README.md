# Co-Print-SV08-Config
Co-Print SV08 Config pack


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


