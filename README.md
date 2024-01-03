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

Instructions on how to get it to work.

It all started with Makerbase's GitHub.

https://github.com/makerbase-mks/Klipper-for-MKS-Boards/tree/main/MKS%20Robin%20Pro%20V1.x

There I found the standard printer.cfg for the Artist D Pro.   
The file "generic-mks-robin-pro-v1.cfg" Includes instructions on how to create the Klipper firmware.  
But you can skip the Firmware Compilation if you want.        

I still had an old laptop lying in the corner.        
I then installed Ubuntu Server on it. But any other Linux or a Raspberry Pi should also work.        
The SSH server should be enabled on the host system.        
So let the fun begin.        
First of all, get the KIAHU script. https://github.com/dw-0/kiauh                
Instruction for installation can be found on the KIAUH GitHub.                        
This makes everything easy to install.                
We need Klipper, Moonraker and Mainsail.                
The script is self-explanatory, so install all 3 please.   

So far, everything went smoothly. But how do you do that with the firmware for the printer?        
So you can use the "Robin_pro35 v0.10.0-557.bin" from the GitHub... and just rename it to Robin_pro35.bin.        
Flash to the printer and you're done.
Alternativly you can build your own Firmware with the KIAUH script.

Confusing was the  "...booting" Message in the display of the printer ... and nothing happens.        
Don't worry, it's normal.        
The display will no longer work!        

Now we should somehow be able to access the firmware with the WEB Interface Mainsail.                
So put the USB cable in and connect to the laptop, PI whatever you have to the Printer.  

Great, now we can access Mainsail, which is the Klipper WEB surface.        
So with "http://" your IP "  from your Desktop connect to the Klipper server" (laptop, Raspi ...)"        
If everything worked, you can now see this interface:

![image](https://github.com/Martin-Stiller/JG-Maker-Artist-D-Pro-Klipper-Mainsail/assets/49054392/badf6f85-2ff1-4d6d-9bed-3106f6e5692a)

On the left-hand side, click on MACHINE

![image](https://github.com/Martin-Stiller/JG-Maker-Artist-D-Pro-Klipper-Mainsail/assets/49054392/17b18014-ade5-4bd7-8f8c-9086a1eae993)


Here you delete the printer.cfg and copy all files from my GitHub repository.

![image](https://github.com/Martin-Stiller/JG-Maker-Artist-D-Pro-Klipper-Mainsail/assets/49054392/0650aea4-388c-467e-a0e4-b6876019cfb3)


Click RESTART.        
If everything worked, the printer should now connect.        
If not check your printer.cfg for this section:        
                [mcu]
                serial: /dev/serial/by-id/usb-1a86_USB_Serial-if00-port0
this ist your USB port your Printer connectet.        

SSH ino your Laptop, Pi.. an type 
```

ls /dev/serial/by-id/

```
![image](https://github.com/Martin-Stiller/JG-Maker-Artist-D-Pro-Klipper-Mainsail/assets/49054392/4b2b9521-2817-4ddd-a4d1-924696ea8cbf)

Change the [MCU] to the shown usb-port. 



