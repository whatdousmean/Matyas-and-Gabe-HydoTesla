# HydroTesla - Gabe Syring and Matyas Velgersdyk - May 15, 2024
Figure 1 - Final Product
![IMG_5241](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/b9e69c82-e9d5-4cff-80aa-5952a6ff592d)
Figure 2 - Water Board
![WaterBoard](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/bc03661d-4047-47e4-8a66-93835cf0833f)
Figure 3 - Main Circuit
![MainCircuit](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/8798b343-7cd8-4ad8-b4d7-1bc820f9bf86)
Figure 4 - Photoresistor Headlights
![Headlights](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/af2474e2-ecc5-4e60-a223-979f37a226f8)
Figure 5 - Full Circuit (Main, photoresistors, and LED circuit all combined)
![FullCircuit](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/137b6068-840f-49b9-bed1-4b703bb3d5b0)
Figure 6 - Back axel connected to gear shaft and motor
![BackAxel](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/ebf99a09-a12d-4d8c-b8da-a3308f73a85e)
Figure 7 - Circuit Schematic
![CircuitSchem](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/16d6b388-4b68-4a00-ab5d-38f643cded5e)
Figure 8 - LED Circuit
![LED](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/a671e197-f456-4b10-8d88-73dca41c9150)
Figure 9 - Battery
![battery](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/e71bef56-d1d5-4ddf-980c-20203ddbf916)
Figure 10 - Battery Plug
![batteryconnect](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/16e3b7d4-8f09-44b0-ba98-589879899b92)
Figure 11 - Battery Holder
![batteryPlace](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/a3a51db9-cde7-4d45-a734-f9d9fb150f52)
Figure 12 - Finished Chassis
![chassis](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/562eb42f-b834-4e75-9e68-3b3e4e6cc009)
Figure 13 - Front Axel
![frontAxel](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/c7dd328a-bb87-4e0e-8135-541da75aa819)
Figure 14 - Motor & Custom Motor Holder
![motor](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/76cbae83-c900-4be0-bedf-2287d7f6c615)
Figure 15 - Servo
![servo](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/cb5ba651-d4d5-41d7-8939-864e1a6f43b8)



# Design Summary
This is a car that is powered by a 12 volt battery. The battery current flows through a mosfet gateway, that can be opened by the 12 pin on an arduino uno being powered. That 12 pin is powered when our water board is put into water, stored in a tupperware container near the center of the car. That water board sends a signal back to the A0 pin on the arduino. If that analogRead value is over 150, the 12 pin will be powered, allowing the circuit to be completed, powering our 12 volt motor. This motor is connected to a simple gear system near the back of the car that is also attached to our back axel. When the motor turns, so does the axel. At the front of the car, there are two "headlights". These "headlights" are mini photoresistor circuits. Both of these circuits are powered through 5 volt pins on the arduino, and they feature voltage dividers. These voltage dividers split the current to ground and an analog pin. These two pin values are read, and then transferred into a servo. This servo is connected to our specially designed front axel, capable of performing front-steering based off of the direction of the servo. The arduino is coded to specific standards with these photoresistors. The requirements for the servo to turn are as follows: 
1) The motor must be running (The water board must be in water).
2) The analogRead value returned by one photoresistor circuit must be higher than the other.
3) The value must be higher than 150.

If all of these requirements are met, the servo will turn to either 57.5 or 122.5 degrees. This is determined by if the photoresistor is on the left or right. Otherwise, the servo remains at 90 degrees, allowing for the car to be straight. Finally, when the water board is active, it also activates the 9 pin on the arduino, turning on a green LED on the top of the car. This is just a signal showing that the car is on.

# System Details
## Main Circuit
The main circuit features a mosfet gateway that is activated from pin 12. Pin 12 is turned on by the analogRead function coming from the water board. Our circuit also features other small things, like resistors and a diode. A picture of the main circuit with the headlights and LED connected can be found in **Figure 5**.
## Water Board
Our water board is attached to the A0 pin. This pin gets a value from the water board through the analogRead() function. If the analogRead value is over 150, it activates the 12 pin, turning on the mosfet gateway. This allows the circuit to be completed, and the motor to move. The motor makes the car move because it is connected to the back axel via a gear system. A picture of the water board can be found in **Figure 2**.
## Motor
Our motor is powered through our main circuit once the mosfet gateway is activated. It is located underneath the car. We designed a custom motor holder for this, and used zipties and screws to hold it in place. A picture of the motor, gear shaft, and back axel can be found in **Figure 6**.
## Photoresistor Headlights
Our photoresistor headlights have a voltage divider on the back end of them. This splits the voltage to ground and to an analogRead() pin (Pins A1 and A2). If either these values are above 150, the 3 pin will activate using the myservo.write() function, turning the servo to the desired degree. A picture of the headlights can be found in **Figure 4**.
## Servo System
Once the 3 pin sends the servo a signal through the myservo.write() function, the servo turns to the desired degree. (For our project those degrees are 90, 57.5, and 122.5).
## LED Circuit
When the water board is activated by water, the 9 pin is turned on. This is connected to a simple LED circuit. It's only purpose is to be an on/off indicator. A picture of the LED circuit can be found in **Figure 8**.
## Battery
We used a 12 volt battery, found in the robotics lab. We used anderson power pole connectors to connect the battery to the circuit, and electical tape to secure the connection. Pictures of this can be found in **Figures 9, 10, and 11**.
## Wiring Diagram
**A detailed schematic of our wiring systems can be found in Figure 7**

# Design Evaluation
  ## Output Display 
  We used a singular green LED on the top of the car to show if it was on or off. It is powered by the 9 pin, which is turned on when the water board is dipped in water.
  ## Manual User Input 
  Our manual user input is in the form of our photoresistor headlights. The user shines a light at either of the headlights, and the car will turn towards the light.
  ## Automatic Sensor 
  Our water board automatically senses if there is water on it or not. If there is, the water board will activate our 12 volt motor and green LED. If not, the car will remain stationary and the LED will be off.
  ## Actuators 
  We used two different actuators, our servo, which activated our front steering, and a 12 volt motor, which powered the back axel to spin, and thus, the car to move.
  ## Mechanisms 
  Our two main mechanisms were our gear shaft that connected our motor to the back axel, and the servo's connection to the front axel to determine steering.
  ## Hardware 
  We had lots of different hardware, so here are all of the items: Arduino uno, plywood, screws, bolts, axels, wheels, motor, servo, tupperware, wires, CUSTOM 3D PRINTED MOTOR HOLDER, resistors, photoresistors, mosfet, LED, water board, breadboard, CUSTOM PRINTED GEARS

  Link to gear STL file: https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/blob/ece42019ce43cfadcfe1f235608ce2f768c4addd/Main%20Gear.stl
  ## Logic, Processing, and Control
  Our full Arduino Uno code can be found here:
  
  https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/blob/e636a06a375cc82a635ebf0bc8ff4fe23f6c6746/Water%20Board%20Arduino%20Code

  Our arduino uno was the main part of this entire project. It enabled everything, the water board, motor, photoresistors, servo, and more to work together. It is important to note that we imported the Servo library into our code in order to be able to use our servo properly. This line where we import the Servo library is on line 2 of our code. 

  ## Other Adjustments
  We did not have very many adjustments to our final plan, just two main ones:

  1) Originally, we had planned to add another photoresistor to determine speed. Unfortunately, we had to cancel this plan due to already low speeds and high resistance from the photoresistor.
  2) While this may not be a real "adjustment" this is important. We designed a custom motor holder that we installed underneath the car. This holds our motor steady and in place. The link to the stl file of this can be found here:
     
     https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/blob/3997745cd45f1ab076b2cb9a97db56c113268df8/Custom_Motor_Holder.stl

## Construction, Quality, Aesthetics, and Visual Appeal

We worked down to the last minute on this project, and unfortunately did not have time to make it look very nice.

## Level of Effort

We put numerous out of class hours into this project, and worked down to the very last minute on it. We think we will get extra points for this.

## Cost

Our cost is below $100. We think we will get the extra points for this as well.

# Lessons Learned

Our main lesson that we learned is to be calm. At many points, we got very frustrated. This hindered our work time usage, mood, and overall production. We had many issues building our circuits and getting everything to work together. In the end, staying calm and trying new methods is what enabled us to finish on time. 

Throughout this project, we learned that planning how to use your time is very important. Time flies when you are so focused on something. The class periods went by a lot faster than we expected.

# Parts List
-Wheels: 8.99 https://www.amazon.com/Electric-Geared-Magnetic-Gearbox-Plastic/dp/B098PZF2DV/ref=sr_1_35?crid=2EX4VLOOX9ZS1&dib=eyJ2IjoiMSJ9.QyNo_q32Tb5r0dJjOPnSxBZr4yA-B5iu3OLGnrt55-NtK0fSX2xsWF0SIiKr9BteU9lhkEpoJUbyJA6mTq9xJom_y_ZfmbW2l-aCfV-bfdcfuozrW4GbZy2iNj6dsrnMGohfvct19fdgS_4q4sBj_5His3QXNjMObXypGrpzfOr-ciKmTmgQ3SHNNUW0_7R_mTHN0B5D7dOXr0FEIe8-oeWTB8BXjX0G-aqSa6OY2ftj2PUJBBzLYk0FmMbtB36QC0pLump2k7H2kwUVN1D_oop1ZNCCQrIVPOGMCrVZ29A.mQP96o5QqT9otElbv6JFUxQx5Nv1aVHpL-fQXE19-dw&dib_tag=se&keywords=3+robot+car+wheels&qid=1715630647&sprefix=3+robot+car+wheels%2Caps%2C152&sr=8-35

-Tupperware: 4.99 https://www.amazon.com/GladWare-Everyday-Rectangle-Storage-Containers/dp/B0085UK4GW/ref=sr_1_2?crid=KFULQCQ8D44N&dib=eyJ2IjoiMSJ9.qniL6n_WpV07Ntr_aKAR3SbwgNJrouvW0urSOjySUg88YMwmjzenWX7w4vuhvvSifPcTPkVxM3uzMr0NI9OsxzPInJpWdJ6hzs5x7DBUVh-GCZ6G4F4CH3EGrbz0MOgHROvs3Er0VdBKZaMj53bYJUIKThW896W60Ay1vVC57qhHQ9l2iggkhqNKi83YwSbS-zSo0niFttbh1K8n46KPdIMPd3aWqs3ILa_CtIq7U7MZVZeyjwJFdHgg6EMchmmiT64eoYqecJygG940isFpI4qq4j0-gVY1eXcFWmKNk9g.7IbXckfI7hkQRKR4os2Dfjf2mO1mmd-_yBTUc1No0Oc&dib_tag=se&keywords=small%2Bplastic%2Brectangular%2Btupperware%2Bcontainers&qid=1715630928&sprefix=small%2Bplastic%2Brectangular%2Btupperware%2Bcontainers%2Caps%2C173&sr=8-2&th=1

-Nuts, Bolts(1/4 inch diameter, 2.5 inch length, 13 count), Washers and Axel : Aprox. 17.50 (Tax Included) at Ace

-Plywood: 10.00

-12 Volt Motor: 14.99 https://www.amazon.com/Greartisan-Electric-Reduction-Centric-Diameter/dp/B07K9KPDNV/ref=sr_1_37?crid=2L68TUI7OPKDJ&dib=eyJ2IjoiMSJ9.shxNoP6K5tB_7COt6jYSGBLCRiCXxoHEG93gGNCuwFTQ_180RWadObOSBDDb4qDwpQVZ-0hcE1qTjMCiGYU3ATVRA0LUq_y1n-99t9j5PQSsraSBjutjXswp7IklgVY_W5ROXAmGZrvo8ohmerzVQw6m92hddUPSXtnZxMFXjCA6fc-030nQsKQ2gxuTb8GrE0YdNc2wUCQKWsKGzpDoX85UYZ0dHJ4fBedBZCFEeb58A2316nnHKjkX-ASzKATBzCQMTVAaBg5nZ2LKRwaI1lYk9YpJDu2wKNzqUpE97Dc.vlYfL5pdRIgY8L57MlkP_6oJubZeUaeSgdR1S4Nj0sQ&dib_tag=se&keywords=electric%2Bmotor&qid=1709584829&sprefix=electric%2Bmotor%2Caps%2C219&sr=8-37&th=1

-Arduino: 15.00

-General Electronics(Including Servo, Water Board, and Battery): Aprox. 20.00
	- 4 220 Ohm resistors, mosfet, diode, LED, breadboards

-3d Prints: Motor Casing (50 grams) Beveled Gears (29 grams)

### Total: $91.47
## Other Parts
- Wires
- 3D Printer
- Arduino app
- Connection cords
- Electical tape
# Assembly Instructions
If you want to build this, follow these instructions!
## Electronics
The electronic and coding portions of this project are very complicated. Start by copying our code (In logic, processing, and control) over to your arduino script. Also make sure you have all the materials listed. You will need many male to male and male to female wires for this. 
### Circuits
In **Figure 7**, you can see all of the circuit's wiring. Start by building all of these circuits. Put the main circuit on a big breadboard, and the other 3 on mini breadboards. The servo and waterboard do not need a breadboard, you can directly connect them. Make sure to not take off the bottom stickers to these breadboards yet. Throughout building these parts, make sure you are testing voltage and amperage levels with a multimeter. All of this, including the arduino should be powered by the 12 volt battery. Tip: Connect the main power from the battery to the + strip on the main breadboard. From there, power the arduino and the rest of the circuits from the arduino. You will most likely need an arduino shield to have enough ports. A picture of our final circuit can be found in **Figure 5**.
## 3D Printed Parts
We used OnShape to print our **3** custom parts. Download our STL files above and 3D Print these parts. (You will need to print two of the gears).
## Chassis (Main Body)
Before the chassis was constructed, it was planned out on a 3d modeling software used by Geomatic Engineers, colloquially called Surveyors, known as Autodesk Civil 3d. The chassis was modeled after a Ford F150 outline from the top, and although plans were made to make layers to build out the full body shape of the Ford truck, that was never done as it would have taken far too long. Instead, 2 layers, identical for the most part excluding some minor changes surrounding the front wheel wells, and the motor-casing attachment point and cutout. 

After the chassis was designed, it was printed full-scale onto a sheet of paper, and traced onto a sheet of plywood. It was then cut out, excluding the cutouts for the motor casing and the water tank(tupperware container) making use of a scroll saw. After that was done, holes were drilled for support posts between the two chassis layers (the bolts), and the first assembly was done. These bolts at the time were 1.5 inches in length, but after being discovered to be too short later on, they were changed to be 2.5 inches long. In any case, once this was done, focus switched to the steering mechanism and the back axel. 
	
The steering mechanism is made up of very small cutouts of plexiglass spanning across two free-spinning armistices holding the wheels onto a fixed point, which will be explained in more depth during the presentation. These are then connected to a servo using more free spinning attachment points, to enable easy rotation, and precise control. This was made using the scroll saw and the drill press over the course of a couple of class periods, and was swiftly assembled. The rear axle was much simpler, only making use of 1 beveled gear(3d printed, model lifted from a beveled gear found in the lab) that interfaces with one attached to the motor, a dowel rod, and two wheels,  as well as two pillow blocks to keep the axle in place. WD40 was used to  lubricate the pillow blocks to reduce friction on them, but that was all. After this, the cutouts in the chassis were made using the drill press and chisels, and the motor casing and water tank were then attached, leaving one final step, which was to insert the electronic components, thus completing the build process. A more detailed breakdown of the dividual parts will take place during the presentation.

To build the chassis, take your plywood and form it to the specifications of the blueprint in Figure ?. This takes a while, but it will be worth it in the end. After you have your 2 pieces of wood, you can begin connecting them with the nuts, bolts, and columns as seen in **Figure 1** and on the blueprints. Throughout the rest of the assembly, you will be taking the two pieces apart and putting them together multiple times. A picture of the finished chassis can be found in **Figure 12**.

## Motor & Motor Holder
At this point, you should have your custom printed motor holder. Take your actual motor and slide it in. After this, strip two wires and wrap it around the motor's positive and negative extensions. We used electrical tape to secure this. These two wires will link back into your circuit. Use zipties to secure the motor to the motor holder. This is shown in **Figure 14**.

## Tupperware
This part is not complicated. Take the lid of your tupperware, and cut a slit in the middle of it big enough for the water board to fit in. In the end, your waterboard will slide into this.

## Axels
A picture of the front axel can be found in **Figure 13**.

## Gears
For the gears, connect one to the back axel, and the other to the part of the motor that sticks out. Slide these around until they connect. After that, you can superglue them to the axel and motor. This will make your gear shaft.

## Servo
A picture of the installed servo can be found in **Figure 15**.

## Battery Pack
Near the back of the chassis, you will find two small holes. These are designed to have zipties go through them. Take your two zipties, and tie down the motor here. Get yourself an anderson power pole connection for the connection into the breadboard. Pictures of this can be found in **Figures 9, 10, and 11**.

## Final Assembly
Now, it is time to combine everything. Take off the second piece of plywood, and install your circuit. This is where you take off the stickers of your breadboards. Your headlights go on the front of the car, your breadboard and arduino in between your tupperware and motor, and your LED and water board will go on top of the car on the second piece of plywood. These will connect to the arduino through the little holes for the wires as seen on the blueprint. Your servo will still be connected to the arduino, but it will be screwed in as stated above.
