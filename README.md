Instructions on how to get it to work.

It all started with Makerbase's GitHub.

https://github.com/makerbase-mks/Klipper-for-MKS-Boards/tree/main/MKS%20Robin%20Pro%20V1.x

There I found the standard printer.cfg for the Artist D Pro.
Includes instructions on how to create the Klipper firmware.
I still had an old laptop lying in the corner.
I then installed Ubuntu Server on it. But any other Linux or a Raspberry Pi should also work.
The SSH server should be enabled on the host system.
So let the fun begin.
First of all, get the KIAHU script. https://github.com/dw-0/kiauh
Instruktion for Insatalation can be found on the KIAUH GitHub.
This makes everything easy to install.
Klipper, Moonraker and Mainsail are used as alternative fluids.
The script is self-explanatory, so install all 3 please.
So far, everything went smoothly. But how do you do that with the firmware for the printer?
So you can use the makerbase-mks from the GitHub... and just rename it to Robin_pro35.bin.
Flash to the printer and you're done. Confusing was booting in the display of the printer ... and nothing happens.
Don't worry, it's normal.
The display will no longer work!
Now we should somehow be able to access the firmware with Clipper.
So usb cable in and connected to the laptop.
Great, now we can access Mainsail, which is the clipper web surface.
So with http://" your IP from the clipper server" (laptop, Raspi ...)"
If everything worked, you can now see this interface:

On the left-hand side, click on MACHINE

Here you delete the printer.cfg and copy all files from my GitHub repository.

Click RESTART.
If everything worked, the printer should now connect.








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



