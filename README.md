# HydroTesla - Gabe Syring and Matyas Velgersdyk - May 15, 2024
![IMG_5241](https://github.com/whatdousmean/Matyas-and-Gabe-HydroTesla/assets/124313095/b9e69c82-e9d5-4cff-80aa-5952a6ff592d)

This is a project created by Gabe S and Matyas V. We call it HydroTesla. This will be a car that relies on water to move. We are using a water board sensor, which generates voltage when it touches water, to turn on a larger voltage supply going to the motor. 
This will be done through a mosfet gateway. Our code will be through an arduino uno. The larger power supply will power a motor that is connected to our back axel via a gear shaft. This car features headlights at the front that use photoresistors to determine the direction
of the car. It has a front turning mechanism that is controlled by a servo.
This will require numerous things, including 3D design, code, purchasing of pre-made items, and more. 
Our aim of the final result is a car that relies on water to be powered, coded by an arduino uno or raspberry pi, that involves a mosfet circuit, featuring a gear shaft connecting the motor and the back axel, that uses a servo to control steering, that has photoresitor-headlights to determine steering.

# Design Summary
This is a car that is powered by a 12 volt battery. The battery current flows through a mosfet gateway, that can be opened by the 12 pin on an arduino uno being powered. That 12 pin is powered when our water board is put into water, stored in a tupperware container near the center of the car. That water board sends a signal back to the A0 pin on the arduino. If that analogRead value is over 150, the 12 pin will be powered, allowing the circuit to be completed, powering our 12 volt motor. This motor is connected to a simple gear system near the back of the car that is also attached to our back axel. When the motor turns, so does the axel. At the front of the car, there are two "headlights". These "headlights" are mini photoresistor circuits. Both of these circuits are powered through 5 volt pins on the arduino, and they feature voltage dividers. These voltage dividers split the current to ground and an analog pin. These two pin values are read, and then transferred into a servo. This servo is connected to our specially designed front axel, capable of performing front-steering based off of the direction of the servo. The arduino is coded to specific standards with these photoresistors. The requirements for the servo to turn are as follows: 1) The motor must be running (The water board must be in water). 2) The analogRead value returned by one photoresistor circuit must be higher than the other. 3) The value must be higher than 150. If all of these requirements are met, the servo will turn to either 57.5 or 122.5 degrees. This is determined by if the photoresistor is on the left or right. Otherwise, the servo remains at 90 degrees, allowing for the car to be straight. Finally, when the water board is active, it also activates the 9 pin on the arduino, turning on a green LED on the top of the car. This is just a signal showing that the car is on.

# System Details
Our main circuit is what turns on our motor. Our water board is attached to the A0 pin, which gets a value from it through analogRead(). If this number is over 150, it activates the 12 pin, which turns on the mosfet gateway. This completes the 12 volt circuit, allowing the motor to run and the back axel to spin. Our photoresistor headlights have a voltage divider on the back end of them. This splits the voltage to ground and to an analogRead() pin. If these values are above 150, the 3 pin will activate using the myservo.write() function, turning the servo to the desired degree. Lastly, when the water board is activated by water, the 9 pin is turned on. This is connected to a simple LED circuit. It's only purpose is to be an on/off indicator.

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
  
