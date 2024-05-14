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

# Design Summary
This is a car that is powered by a 12 volt battery. The battery current flows through a mosfet gateway, that can be opened by the 12 pin on an arduino uno being powered. That 12 pin is powered when our water board is put into water, stored in a tupperware container near the center of the car. That water board sends a signal back to the A0 pin on the arduino. If that analogRead value is over 150, the 12 pin will be powered, allowing the circuit to be completed, powering our 12 volt motor. This motor is connected to a simple gear system near the back of the car that is also attached to our back axel. When the motor turns, so does the axel. At the front of the car, there are two "headlights". These "headlights" are mini photoresistor circuits. Both of these circuits are powered through 5 volt pins on the arduino, and they feature voltage dividers. These voltage dividers split the current to ground and an analog pin. These two pin values are read, and then transferred into a servo. This servo is connected to our specially designed front axel, capable of performing front-steering based off of the direction of the servo. The arduino is coded to specific standards with these photoresistors. The requirements for the servo to turn are as follows: 
1) The motor must be running (The water board must be in water).
2) The analogRead value returned by one photoresistor circuit must be higher than the other.
3) The value must be higher than 150.

If all of these requirements are met, the servo will turn to either 57.5 or 122.5 degrees. This is determined by if the photoresistor is on the left or right. Otherwise, the servo remains at 90 degrees, allowing for the car to be straight. Finally, when the water board is active, it also activates the 9 pin on the arduino, turning on a green LED on the top of the car. This is just a signal showing that the car is on.

# System Details
## Main Circuit
The main circuit features a mosfet gateway that is activated from pin 12. Pin 12 is turned on by the analogRead function coming from the water board.
## Water Board
Our water board is attached to the A0 pin. This pin gets a value from the water board through the analogRead() function. If the analogRead value is over 150, it activates the 12 pin, turning on the mosfet gateway. This allows the circuit to be completed, and the motor to move.
## Photoresistor Headlights
Our photoresistor headlights have a voltage divider on the back end of them. This splits the voltage to ground and to an analogRead() pin (Pins A1 and A2). If either these values are above 150, the 3 pin will activate using the myservo.write() function, turning the servo to the desired degree. 
## LED Circuit
When the water board is activated by water, the 9 pin is turned on. This is connected to a simple LED circuit. It's only purpose is to be an on/off indicator.

# Design Evaluation
  ## Output Display 
  LED on top of the car showing on/off
  ## Manual User Input 
  Photoresistor headlights. User shines light at the headlights and the car responds by turning in the direction of the light.
  ## Automatic Sensor 
  Water board automatically senses if there is water or not. If there is, the motor is turned on and the car goes. If not, the car is stationary.
  ## Actuators 
  Servo, 12 Volt DC Motor
  ## Mechanisms 
  Gear Shaft Mechanism, Servo connection to front axel for steering
  ## Hardware 
  Arduino, plywood, screws, bolts, axels, wheels, motor, servo, tupperware, wires, CUSTOM 3D PRINTED MOTOR HOLDER
  ## Logic 
  Arduino code
  ## Processing 
  Arduino board takes in analogRead numbers from photoresistor headlights and water board.
  ## Control 
  Arduino controls the servo, LED, and motor based off of the analogRead numbers
  
