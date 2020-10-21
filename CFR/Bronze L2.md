Lighting Controls Basics - BRONZE TRAINING - L2

# Overview

## CFR Lighting Design Matrix

<img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201013114100458.png" alt="image-20201013114100458" style="zoom:33%;" />

Can be found in CFR Standards: Electrical Symbols. Knowing your code and appliance, tells you a letter. Go to the letter block. It tells you the fixtures you need to use, time clocks, sensors, and lists of the details you need. 

Workflow: throw all of this info on your detail sheet, do your plans, layout sensors, controls, and lights, and come back to detail sheet to revise things.

Afterwards, look at the code exceptions to the matrix's right.

# Standalone Controls

A system that doesn't have a control system. 

<img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201013115449954.png" alt="image-20201013115449954" style="zoom:50%;" />

Blue lines represent power. A wall switch can turn your lighting fixture on and off. 

A wall dimmer requires an extra green wire that goes to your fixture.

A OCC sensor interrupts the power line and tells the power pack when to turn the lights on and off. Now there's two points that can turn off the light. You can have OCC sensors going to the same power line. This fixture can be chained to different fixtures to create a "zone". 

A daylight sensor connects to the power pack to turn lights off if there's too much light. Daylight sensor also connects to the green wire to dim the lights if there's some light (it will send the fixture will send a 5V signal at its refresh rate to tell the fixture to be at 50%. It overrides the wall dimmer's command).

You can create another zone connected to the same power pack controlled by a wall dimmer. However, you cannot have multiple daylight zones because it must connect to the power pack.



In a stand alone system, you can't override a daylight sensor. 

## Room Controller

<img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201013120420184.png" alt="image-20201013120420184" style="zoom:50%;" />

This is a 10V system. Important to know because if an architect wants to use a pendant that is not 10V, he can't.

This is a good example for a conference or classroom. It has multiple zones. One can dim the lights in front of the tv, etc. The switches and OCC (Occupancy sensors) connect to the controller, or the brain, which then communicates with each zone.

# Wireless Controls

<img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201013204443714.png" alt="image-20201013204443714" style="zoom:50%;" />

10,000+ sqft normally uses wireless controls.

Essential brain called "hub" or gateway", depending on manufacturer. This needs a dedicated 120V circuit to work. It takes input from the OCC Sensors, daylight sensor, and wall dimmers. 

The power pack (0-10V dimmer) will send the signal about how dim a fixture should be, instead of the wall dimmer. 

Every zone gets its own power pack. Don't document power packs because its covered in controls and emergency language. Don't show power packs.

# Sensors

Sensor Layout depends on the sensor you select.

<img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201013204338833.png" alt="image-20201013204338833" style="zoom:33%;" />

Use sensor switch coverage circles to know how far to place sensors. Make sure the circles overlap.

## Occupancy and Vacancy Sensors

Line voltage (power pack is integrated into the sensor itself) is not our standard, Low Voltage is. 

Occupancy turns 

## Daylight Sensors

Senses how many lumens it senses

Two different types: daylight only  and daylight/occupancy/power pack (line voltage; not our standards)

<img src="C:\Users\Trxn\AppData\Roaming\Typora\typora-user-images\image-20201013204834304.png" alt="image-20201013204834304" style="zoom:25%;" />

General rule of thumb for sensor layout: top of window height = depth of sensor into space on the ceiling. Move it closer to the window if there is something in the way. Put one daylight sensor per zone.

# Modifying Controls Details

Read the red text carefully and delete and keep according to your needs.

