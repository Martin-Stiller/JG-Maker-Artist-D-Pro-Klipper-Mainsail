
JG Maker Astist D Pro with Klipper on an Old Lenovo Thinkpad

Running Klipper installation on the JGMAKER Artist D PRO 3D Printer.

Features: UART | BLTouch 3DTouch) | KAMP | IDEX

Latest Update now with:                        
        Endstops integration                        
        Input Shaper                        
        Better Accelerations                        
        Script for Z-Offset Caliration ( BL Touch)                        
        Axis Twist Compensation                        
        Screw Tilt Adjust                        


I assume no liability for destroyed printers! Use at your own risk !

Start G-code and End G-code for Prusa Slicer:

Start G-code:                                                                                            
```

SET_PRINT_STATS_INFO TOTAL_LAYER=[total_layer_count]
START_PRINT BED_TEMP=[first_layer_bed_temperature] EXTRUDER_TEMP=[first_layer_temperature] EXTRUDER1_TEMP=[first_layer_temperature] MATERIAL=[filament_type]       
;ACTIVATE_COPY_MODE       ;for Copy Mode
```

End G-code:
```

; total layers count = [total_layer_count]                                
END_Print
```


![image](https://github.com/Martin-Stiller/JG-Maker-Artist-D-Pro-Klipper-Mainsail/assets/49054392/06c73b74-d6d8-4498-9539-7fa06db71131)



