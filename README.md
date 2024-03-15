# IoT-Pet-Feeder
Ever felt tired of constantly having to re-fill your pet’s food bowl? Or perhaps too busy to do so? This project, the IoT Pet Feeder, is here to solve those problems. The IoT pet feeder is created to assist a user by automatically refilling a food bowl, freeing the user from having to do so himself/herself. 
The IoT Pet Feeder is capable of its automation by utilizing specific codes that are uploaded into the Arduino UNO that was used for the purpose of this project. The Arduino UNO uses the codes provided to connect itself to the IoT platform application, Blynk, which can be downloaded and installed on a user’s mobile phone. This enables the users of IoT Pet Feeder to easily control it with their mobile devices, allowing them to use it any time, anywhere. 
The reasoning behind the usage of the Blynk application is specifically to provide portable control of the rotor and and the DS1302 RTC (Real-Time Clock) module located on the IoT Pet feeder in order to set up a specific time upon which the device itself would activate and perform its task by rotating the rotor and opening up a section of the provided food reserves, thus dispensing a portion of pet food into a food bowl located below it. 

Components used:
	Arduino UNO
	Male-to-male Jumper cables
	SG-90 Servo
![image](https://github.com/MrArrow12/IoT-Pet-Feeder/assets/98644709/ee990643-25dc-47d1-96ff-2da69af150b3)

Codes used in project
#define BLYNK_PRINT SwSerial

#include <SoftwareSerial.h>
SoftwareSerial SwSerial(10, 11); // RX, TX
    
#include <BlynkSimpleStream.h>
#include <Servo.h>

// You should get Auth Token in the Blynk App.
// Go to the Project Settings (nut icon).
char auth[] = " ";

Servo servo;

BLYNK_WRITE(V3){
  servo.write(param.asInt());
}

void setup(){
  // Debug console
  SwSerial.begin(9600);

 
  // Blynk will work through Serial
  // Do not read or write this serial manually in your sketch
  Serial.begin(9600);
  Blynk.begin(Serial, auth);

  servo.attach(9);
}

void loop(){
  Blynk.run();
} 
IoT Reference Architecture of Blynk

Blynk is a platform designed for IOT. It has the ability to control hardware using remote. It can store data, visualize, and display sensor data.
There are 3 Major components in the platform
	Blynk App = This allows you to create user interfaces for our projects using various widgets that it provides.
	Blynk Server = Responsible for all the communications between smartphone and hardware. You can use Blynk Cloud or run your local private Blynk server. It is open-source, it can easily handle multiple devices that can range into hundreds of thousand, and can be launched on Rasphberry Pi.
	Blynk Libraries – It is widely used for all hardware platforms, it enable communication with the server and process all incoming and outcoming commands.
![image](https://github.com/MrArrow12/IoT-Pet-Feeder/assets/98644709/62fb7279-947c-4037-8e35-0e170a5f71df)

Above the picture, when a user press a Button in the Blynk app, the message will travel to the Blynk Server , then to Blynk Libraries which will incoming messages, and it will find its way to your hardware. It can also work in the reverse direction, and it happens instantly. 

Steps for connecting Arduino code to the Arduino UNO and through Blynk app.
	First, we need to write a code on Arduino IDE in order to allow communication between the Arduino UNO device and the software Blynk app.
	After that, we need to write down our authentication token to connect the Blynk application with the Arduino UNO. This can be done by sending the authentication token through e-mail or from within the Blynk application itself.
	Once the code is compiled, the compiler will show messages to notify that the code is running. Otherwise, it will send an error message specifying details of the error.
	Then, We plug in the USB cable to the Arduino UNO and connect it to a laptop through the USB port cable. The name of the port will be shown on the Arduino IDE specifying details on which port that it was plugged into.  (Arduino IDE -> Tools -> Port) 
	Afterwards, we start the command prompt in order to start the connection between Arduino UNO and the Blynk Application. Then, write down the paths based on our script folder from the Arduino folder found in documents (usually) depending on where you install your script folder. In addition, write the instruction command  based on  the port given by Arduino IDE on your path.
	Launch the Blynk application through a mobile phone based on our authentication code. Use the command interface to control the servo motor for verification.


