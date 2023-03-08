---
title: "F4 &#124;&#124; Making an Arduino Sonar Module"
excerpt: "Figuring out how to make an 180-degree sonar module with an Arduino Kit"
permalink: /bme66/F4
classes: wide
sidebar:
- title: Relevant Topics
  text:  Arduino, C++, Ultrasonic Sensors, Servo Motors
---
- [Introductions](#introductions)
- [Code and Simulation](#code-and-simulation)
- [Prototyping](#prototyping)

## Introductions

Tasked with making _anything_ with an ELEGOO Super Starter Kit, I did some Reddit-diving and got the idea to make a sonar module! Essentially, I can slap an ultrasonic sensor on a a servo, rotate it every degree or so (I'll probably have to tweak the resolution) and take distance measurements. Then I can slap this (somehow) into a polar plotter and make a 180-degree "distance map" that should roughly approximate the surroundings of my device!

## Code and Simulation

After some Googling, I realized that it's actually possible to completely simulate the circuit and Arduino module without ever building everything (which should probably save me a lot of time). I used [TinkerCad](https://www.tinkercad.com/dashboard) to build and simulate my code. This is the initial setup with labeled pins:

![Initial schematic of pinouts and connections](INSERT PATH HERE)

To summarize, I essentially created a power and ground channel on the breadboard to support anything else I might want to add to the circuit later. I connected the ultrasonic and servo power/ground pins to these channels, and fed the power channel with the 5V power output from the UNO R3 and the GND pin as demonstrated. I also hooked up the signal line of the servo to pin 3, the trigger line of the ultrasonic to pin 5, and the echo line of the ultrasonic to pin 6. Relatively straightforward!

As for the code, it's relatively short, so I'll attach it here:
```
#include <Servo.h>
Servo uSweeper; //Instantiate servo

//Create variables for all pins
int USEchoPin = 5;
int USTrigPin = 6;
int servoPin = 3;
//Create variable to store all of the sonar data
long sonarArray[2][180/5];

void setup()
{
  uSweeper.attach(servoPin); //Attach DIGPin3 to servo object
  Serial.begin(9600); //Serial for debugging
  pinMode(USTrigPin, OUTPUT); //Set pinout modes for US
  pinMode(USEchoPin, INPUT);
  pinMode(LED_BUILTIN, OUTPUT);
}

// Public function that inputs the pin for the trigger and echo pins
// of the ultrasonic component, and outputs a distance long in cm.
long usDist(int trigPin, int echoPin) {
  //Send out US pulse (triggered by HIGH for 10 useconds)
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  long waveDur = pulseIn(echoPin, HIGH);
  long dist = waveDur*0.343/2;
  return dist;
}

void loop()
{
  int iterPos = 0;
  uSweeper.write(0); //Reset servo
  delayMicroseconds(15);
  Serial.println("Begin sonar loop");
  for (int ang = 0; ang < 180; ang+=5) {
    sonarArray[0][iterPos] = (long) ang; //Sonar angle input
  	uSweeper.write(ang); //Turn servo to this angle
    delayMicroseconds(15); //Wait for servo to move
    long angleDist = usDist(USTrigPin, USEchoPin); //Get distance
    sonarArray[1][iterPos] = angleDist; //And input it into sonar array
  }
  //Signify completion of one sonar loop
  
  digitalWrite(LED_BUILTIN, HIGH);
  //delayMicroseconds(200);
  digitalWrite(LED_BUILTIN, LOW);
  Serial.println("End sonar loop");
  //Print array
  for (long element:sonarArray[1]) {
    Serial.print(element + " ");
  }
}  
  ```

The comments provide a bit more detail as to what each line is doing - but overall, the code essentially does an ultrasonic sensor read (trigger and echo), then records this distance in a "sonar array". It then advances the servo motor forwards by about 5 degrees, and does it again. Repeat until 180 degrees (the range of the servo) has been achieved, blink an LED and do some serial prints to signify that we're done with a loop, then repeat! TinkerCad also lets you simulate your code, which is really helpful to be able to debug without messing with the actual Arduino parts. I still had to figure out a way to get the data onto an actual "graph" such that it's readable, but I wanted to build and test this initial prototype, as graphing the data (probably by reading the serial port) is mostly software-based. 

## Prototyping

