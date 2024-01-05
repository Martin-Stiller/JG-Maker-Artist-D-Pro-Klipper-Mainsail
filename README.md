<H1>JG Maker Artist D Pro with Klipper on an Old Lenovo ThinkPad</H1> 

Running Klipper installation on the JGMAKER Artist D PRO 3D Printer.

I will say I do this for fun!          
I know I can buy myself a better Printer for the money I invested in this Project !         
But I do it for fun to work on the Printer ( it was a Gift ).         
I like to Optimize Stuff :) 

Update:
Added Makerbase MKS Robin Pro v 1.0 Pinout
https://placehold.it/150/ffffff/ff0000?text=I cleaned up the config files and changed the descriptions to English!





<H3>Mods on the Printer:</H3>

I changed the 2 Extruder to BIQU H2 V2S (found one cheap on Banggood and one on Aliexpress).         
https://www.thingiverse.com/thing:5024765 Thank you! IMP67 for the STL files !
        
I ripped out the loud Fan on the Power Supply and did it with a Noctua 120 mm Fan with a Step-down converter on the Power Supply pin's 24V.         
 On the old Fan Connector on the Power Supply, I connected an LED for Safety, they will turn on if the Power Supply is too hot.         
Cut out the underside of the Printer for more Airflow for the Noctua 120mm Fan.         
I ripped out the Case Fan in the Back of the Printer. The Noctua does a Great Job, so I don't need it.         
https://www.thingiverse.com/thing:5995200 Thank you!  Living_being for your Guide !         

Changed the Stepper Bridges to UART mode .  
https://www.facebook.com/groups/artistd/posts/5582369768503249/        

Next Mods :        
Change the crapy Rollers on the BED to 2 Linear Rails. ( With the BIQU Extruders I can print at 100–120 mm/s, but The Bed is too Loud at these Speeds.        
                
                
<H2>Features: UART | BLTouch (3DTouch) | KAMP | IDEX</H2>

Latest Update now with:                        
        End stops integration                        
        Input Shaper                        
        Better Accelerations                        
        Script for Z-Offset Calibration ( BL Touch)                        
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

<H1>Instructions on how to get it to work.</H1>

It all started with Makerbase's GitHub.

https://github.com/makerbase-mks/Klipper-for-MKS-Boards/tree/main/MKS%20Robin%20Pro%20V1.x

There I found the standard printer.cfg for the Artist D Pro.   
The file "generic-mks-robin-pro-v1.cfg" Includes instructions on how to create the Klipper firmware.  
But you can skip the Firmware Compilation if you want.        

I still had an old laptop lying in the corner.        
I then installed Ubuntu Server on it.        
But any other Linux system or a Raspberry Pi should also work.        
The SSH server should be enabled on the host system.        
So let the fun begin.        
First, get the KIAHU script. https://github.com/dw-0/kiauh                
Instructions for installation can be found on the KIAUH GitHub.                        
This makes everything easy to install.                
We need Klipper, Moonraker and Mainsail.                
The script is self-explanatory, so install all three, please.   

So far, everything has gone smoothly.        
But how do you do that with the firmware for the printer?        
So you can use the "Robin_pro35 v0.10.0-557.bin" from GitHub... and just rename it to Robin_pro35.bin.        
Flash it to the printer, and you're done.
Alternatively you can build your own Firmware with the KIAUH script.

Confusing was the  "...booting" Message in the display of the printer ... and nothing happened.        
Don't worry, it's normal.        
The display will no longer work!        

Now we should somehow be able to access the firmware with the WEB Interface Mainsail.                
So put the USB cable in and connect it to the laptop, PI whatever you have to the Printer.  

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
If not, check your printer.cfg for this section:        
                [mcu]        
                serial: /dev/serial/by-id/usb-1a86_USB_Serial-if00-port0        
This is your USB port, where your Printer connected.        

SSH into your Laptop, Pi.. and type 
```

ls /dev/serial/by-id/

```
![image](https://github.com/Martin-Stiller/JG-Maker-Artist-D-Pro-Klipper-Mainsail/assets/49054392/4b2b9521-2817-4ddd-a4d1-924696ea8cbf)

Change the [MCU] to the shown usb-port on your Host. 


