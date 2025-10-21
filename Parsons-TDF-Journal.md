# MDes-TDF

## [Week 2 (9/2): Hello World + Serial Blinking]
### Code + Serial Blinking

https://github.com/user-attachments/assets/11079986-5b01-4e25-a491-b1ba81671e10

### Notes:
I found the exercise to be great for getting back into code and Arduino work. The proverbial, "wheels are starting to trun," on a how I might implement serial outputs related to music, lights, and sounds. For example, could one build a system using the Arduino which transforms noise (db) as an input and light as an output or noise (db) as an input and noise as an output (response). In theory can two Arduio's communicate with sound?

### Code: 

```/*
  Hello World
  A "Hello, World!" program generally is a computer program that
	outputs or displays the message "Hello, World!".
	Such a program is very simple in most programming languages,
	and is often used to illustrate the basic syntax of a programming language.
	It is often the first program written by people learning to code
*/

int led = 13;  // define a variable to hold the pin number of the internal LED

void setup() {
//initialize serial communications at 9600 baud rate
Serial.begin(9600);
pinMode(led, OUTPUT);
}

void loop(){
//send 'Hello, world!' over the serial port
Serial.println("Hello, world!");
digitalWrite(led, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
  digitalWrite(led, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);         
//wait 100 milliseconds so we don't drive ourselves crazy
delay(1000);
}
```

## [Week 3 (9/8): Write a program to flash the onboard LED while printing Hello World to serial]

### Experiment and PLAY!
Make “something interesting” happen with:
1 LEDs + 1 LDR
2 or more LEDs

https://github.com/user-attachments/assets/6a624b4b-d8bc-4e73-b855-3627fff7e6da

### Notes: 
I used an LDR to detect light sensitivity and turn off and on the two (red / blue) lights. I began with just one light (blue) and once it was working I added in the code, wiring, and hardware for the second light (red). Note -- the red light is dim in the video, however it is turning on and off as expected. 

### Code: 

```const int LDR_Pin = A0;     // LDR connected to analog pin A0
const int LED_Pin_1 = 9;    // First LED on digital pin 9
const int LED_Pin_2 = 8;    // Second LED on digital pin 8

void setup() {
  pinMode(LED_Pin_1, OUTPUT);
  pinMode(LED_Pin_2, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int ldrValue = analogRead(LDR_Pin);
  Serial.print("LDR Value: ");
  Serial.println(ldrValue);

  // Set threshold for dark condition (adjust if needed)
  if (ldrValue < 10) { 
    digitalWrite(LED_Pin_1, HIGH);       // Turn on LED at pin 9
    digitalWrite(LED_Pin_2, HIGH);       // Turn on LED at pin 8
    Serial.println("If it's dark turn the light on");
  } else {
    digitalWrite(LED_Pin_1, LOW);        // Turn off LED at pin 9
    digitalWrite(LED_Pin_2, LOW);        // Turn off LED at pin 8
  }
  delay(100);
}

```
## [Week 3 (9/10): Designing & Lazer-Printing a Ring]

### Using typography to Design a Ring
Lately, I have been exploring fun typefaces. One which I came across this year is called Hoffman; the namesake of Armin Hoffman. Hoffman Typeface was not created by Armin Hoffman himself, but was inspired by his "Graphic Design Manual." In his manual he conducts an experiment in which he suggests all glyphs can be hand-drawn using circle tangents; later Nguyen and Gobber digitized these methods for broader contemporary use.

Hoffman's Graphic Design Manual (see page 40): http://b.parsons.edu/~dejongo/12-fall/stuff/departmentalReadings/graphic-design-manual-principles-and-practice.pdf


### Design Approach

I downloaded a trial of the Hoffman Typeface and used it in Adobe Illustrator to discover letters which might be suitable for a ring. Unsurpisingly I gravitated towards the "O" and the "B." 

To determine the internal size of the ring, I used the digital callipers to measure the internal width of a ring which I currently wear. The size is roughly .725 in or 19mm. for my cut, I used slightly smaller dimensions, since it is easier to remove more material rather than adding material back in. 

<img width="558" height="576" alt="image" src="https://github.com/user-attachments/assets/133b7608-cfa2-40d5-b1d8-6c800144888e" />

![IMG_8902](https://github.com/user-attachments/assets/0c6be577-a4fb-42c5-9b30-1fe16cfe99d8)

### Printing & Constuction

The printing process was relatively smooth. I did however, need to stop the first print and reposition the wood, due to a miscalculation of space.

After printing I opted to combine the two rings -- rotating one by 45 degrees to create an overlapping effect. I also sanded down the rings to refine the wearability and aesthetic. Finally, I used wood glue and a single clamp to fuse the two rings in plance. 

### Finishing

In finishing the ring, I learned the valuable lesson of when NOT to take a risk or try something new. Once I had sanded down my "C" shaped ring, I then decided I would use a small drill bit to drill through the top of the "O" to inset a gem-like object. In doing so, I fractured the wood close to the edge of the ring and effectvely runied the smooth aesthetic I was aiming to achieve. I salvaged the ring by cutting out the damage, such that it resembled a "C." The "C" represents, Cal Berkeley. 

### Result

![IMG_8918](https://github.com/user-attachments/assets/25fd2c34-cdcc-463d-9512-dafa6e623451)
![IMG_8917](https://github.com/user-attachments/assets/0d2f82e8-55e0-42c7-98d8-6404f848c5d4)



## [Week 4 (9/15): Arduino RGB Light]

## RGB Blinking
### Code

``` 
/* 

 Example code for Arduino Tutorial
  
    RGB LED connected to pins 9, 10, 11

  We still need to use limiting resistors to keep our LEDs safe

  Generally we use a slightly larger resistor (470 ohm) for the RED component 
    and the same slightly smaller resistor values (430 ohm) for the GREEN and BLUE components.

  for our circuit let's use:
  - 470 ohm for RED
    - color bands -> yellow, purple, black, black, brown
  - 430 ohm for GREEN and BLUE
    - color bands -> yellow, orange, black, black, brown
*/

 
// the numbers of the LED pins
const int redLED = 9;  
const int greenLED = 10;  
const int blueLED = 11;  

int delaytime = 500;  // a variable for all delay times
                      // now we can change them all just by changing this one number!
 
void setup(){
  pinMode(redLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(blueLED, OUTPUT);
}

// note: full brightness is REALLY bright, so we often start at 50% and increase from there if necessary 

void loop(){
    analogWrite(redLED, 127);   // turn red on 50%
    delay(delaytime);           // wait
    analogWrite(redLED, 0);     // set red to 0%
    delay(delaytime);           // wait

    analogWrite(greenLED, 127);
    delay(delaytime);
    analogWrite(greenLED, 0);
    delay(delaytime);

    analogWrite(blueLED, 127);
    delay(delaytime);
    analogWrite(blueLED, 0);
    delay(delaytime);
```

### Result

https://github.com/user-attachments/assets/bb82ce77-663d-40f9-a4d6-e80453cccf98

## RGB Fading

### Code

```
/*
Example Code - ST 12/16/2018

single RGB LED - common anode (negative)
using pins 9, 10, 11
simple test to fade 3 channels LED

  This example code modified from: https://www.arduino.cc/en/Tutorial/BuiltInExamples/Fade
*/

int brightness = 0;    // how bright the LED is
int redBrightness = 0;
int greenBrightness = 0;
int blueBrightness = 0;

int fadeAmount = 5;    // how many points to fade the LED by
int redFadeAmount = 1;    
int greenFadeAmount = 5;    
int blueFadeAmount = 3;    

const int redLEDPin = 9;     // LED connected to pin 9
const int greenLEDPin = 10;  // LED connected to pin 10
const int blueLEDPin = 11;    // LED connected to pin 11

void setup() {
  // initialize serial communications at 9600 bps:
  Serial.begin(9600); 

  // set the digital pins as outputs
  pinMode(greenLEDPin,OUTPUT);
  pinMode(redLEDPin,OUTPUT);
  pinMode(blueLEDPin,OUTPUT);

  TestEm();
}

void loop() {
  
// set the brightness of RED - pin 9:
  analogWrite(redLEDPin, redBrightness);  
  
  // change the brightness for next time through the loop:
  redBrightness = redBrightness + redFadeAmount;

  // reverse the direction of the fading at the ends of the fade: 
  // range scaled just because: 0-255 changed to 0-100
  if (redBrightness == 0 || redBrightness == 200) {
    redFadeAmount = -redFadeAmount ; 
  }     
  // wait for 30 milliseconds to see the dimming effect    
  delay(30); 
 
 // set the brightness of Green - pin 10:
  analogWrite(greenLEDPin, greenBrightness);  
  
  // change the brightness for next time through the loop:
  greenBrightness = greenBrightness + greenFadeAmount;

  // reverse the direction of the fading at the ends of the fade: 
  if (greenBrightness == 0 || greenBrightness == 120) {
    greenFadeAmount = -greenFadeAmount ; 
  }     
  // wait for 30 milliseconds to see the dimming effect    
  delay(10);   
  
  // set the brightness of BLUE - pin 11:
  analogWrite(blueLEDPin, blueBrightness);  
  
  // change the brightness for next time through the loop:
  blueBrightness = blueBrightness + blueFadeAmount;

  // reverse the direction of the fading at the ends of the fade: 
  if (blueBrightness == 0 || blueBrightness == 255) {
    blueFadeAmount = -blueFadeAmount ; 
  }     
  // wait for 30 milliseconds to see the dimming effect    
  delay(30); 


// Fade;
}

// ---------------------------------
void AllOff (){
  analogWrite(redLEDPin, 0);
  analogWrite(greenLEDPin, 0);
  analogWrite(blueLEDPin, 0);
}
// ---------------------------------

// ---------------------------------
void TestEm() {
  //Test the LED.
  analogWrite(redLEDPin, 100);
  delay(300);
  analogWrite(redLEDPin, 0);
  delay(300);
  analogWrite(greenLEDPin, 100);
  delay(300);
  analogWrite(greenLEDPin, 0);
  delay(300);
  analogWrite(blueLEDPin, 100);
  delay(300);
  analogWrite(blueLEDPin, 0);
  delay(300);
}
// ---------------------------------

```

### Result: 

https://github.com/user-attachments/assets/e3c76fc5-2858-4d58-97e8-632ec2a18dd3

## Button + Light

### Code 

``` 
/*
  Button

  Turns on and off a light emitting diode(LED) connected to digital pin 13,
  when pressing a pushbutton attached to pin 2.

  The circuit:
  - LED attached from pin 13 to ground through 220 ohm resistor
  - pushbutton attached to pin 2 from +5V
  - 10K resistor attached to pin 2 from ground

  - Note: on most Arduinos there is already an LED on the board
    attached to pin 13.

  created 2005
  by DojoDave <http://www.0j0.org>
  modified 30 Aug 2011
  by Tom Igoe

  This example code is in the public domain.

  https://www.arduino.cc/en/Tutorial/BuiltInExamples/Button
*/

// constants won't change. They're used here to set pin numbers:
const int buttonPin = 2;     // the number of the pushbutton pin
const int ledPin =  13;      // the number of the LED pin

// variables will change:
int buttonState = 0;         // variable for reading the pushbutton status

void setup() {
  // initialize the LED pin as an output:
  pinMode(ledPin, OUTPUT);
  // initialize the pushbutton pin as an input:
  pinMode(buttonPin, INPUT);
}

void loop() {
  // read the state of the pushbutton value:
  buttonState = digitalRead(buttonPin);

  // check if the pushbutton is pressed. If it is, the buttonState is HIGH:
  if (buttonState == HIGH) {
    // turn LED on:
    digitalWrite(ledPin, HIGH);
  } else {
    // turn LED off:
    digitalWrite(ledPin, LOW);
  }
}
```

### Result

https://github.com/user-attachments/assets/78308fe6-5b03-421b-9a66-7aa2622b00a6

## Potentiometer 
### Code

```
/*
  Analog Input

  Demonstrates analog input by reading an analog sensor on analog pin 0 and
  turning on and off a light emitting diode(LED) connected to digital pin 13.
  The amount of time the LED will be on and off depends on the value obtained
  by analogRead().

  The circuit:
  - potentiometer
    center pin of the potentiometer to the analog input 0
    one side pin (either one) to ground
    the other side pin to +5V
  - LED
    anode (long leg) attached to digital output 13 through 220 ohm resistor
    cathode (short leg) attached to ground

  - Note: because most Arduinos have a built-in LED attached to pin 13 on the
    board, the LED is optional.

  created by David Cuartielles
  modified 30 Aug 2011
  By Tom Igoe

  This example code is in the public domain.

  https://www.arduino.cc/en/Tutorial/BuiltInExamples/AnalogInput
*/

int sensorPin = A0;    // select the input pin for the potentiometer
int ledPin = 13;      // select the pin for the LED
int sensorValue = 1;  // variable to store the value coming from the sensor

void setup() {
  // declare the ledPin as an OUTPUT:
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // read the value from the sensor:
  sensorValue = analogRead(sensorPin);
  // turn the ledPin on
  digitalWrite(ledPin, HIGH);
  // stop the program for <sensorValue> milliseconds:
  delay(sensorValue);
  // turn the ledPin off:
  digitalWrite(ldPin, LOW);
  // stop the program for for <sensorValue> milliseconds:
  delay(sensorValue);
}
```
### Result: 

https://github.com/user-attachments/assets/4ad0c9a4-8482-4fff-a961-ded944494ea5


## Ring Project, 3D Printed Form 

### Reproducing My Original Ring
### Fusion Files

<img width="769" height="743" alt="image" src="https://github.com/user-attachments/assets/90ad0bf1-977b-466f-8a94-2ac2c9512848" />

<img width="844" height="740" alt="image" src="https://github.com/user-attachments/assets/45a49fee-fe65-40ef-8770-d790ff4e3e91" />

### Notes/Reflection: 
Given that we used the Lazer Cutter to create the first variaiton of our rings, I found the process of reproducing it in Fision to be relatively straight forward -- importing the file to fusion as a sketch and extruding the sketch. 

My wood ring broke while I was shaping it after cutting. For the 3D printed ring, I shaped it in Fusion and then printed the exact final version of it; turning out un broken and better looking. I did have to print twice, as I experienced a scaling issue. 

### Making a New Style of Ring
### Fusion Files

<img width="627" height="705" alt="image" src="https://github.com/user-attachments/assets/9cb3cc0a-42e5-446d-a472-78afc259b09e" />

<img width="760" height="737" alt="image" src="https://github.com/user-attachments/assets/62e4db19-fa2a-4528-942e-dcd977eba430" />

### Notes/Reflection: 
Strating from scratch in Fusion was more difficult than I anticipated. The sketching process was relatively straightforward, however I faced a fair bit of difficulty achieving the exact form I wanted in Fusion. 

## Iterations (New & Old Ring): 

<img width="884" height="275" alt="image" src="https://github.com/user-attachments/assets/b270c002-a5c4-4db7-98d7-8c7ab2fb6f9c" />

## [Week 5 (9/22): Origami Project]
## Entry 1: 
Early in this week (9/22-9/24) I prototyped the early stages of my origami project; transitioning from sketches, to workable prototypes. I also iterated on my code significantly.

### Sketches: 
Initially I sketchedout a few concepts of what I'd like to do for the Origami assignment; two of which I've linked below. I considered doing the  bed concept, but ultimately I determined that it was too small scale and not in line with the project expectations. In retrospect, I wish I took this direction, since it would have stood out from the rest of the class on the factor of size alone. 

![IMG_9038 2](https://github.com/user-attachments/assets/dae111ea-2830-4479-9fae-16c95551ec39)

### Prototypes:
Two very early prototype. Here I was testing that a) the servo had enough leverage to pull the paper, b) what optimal length of the servo arm should be, c) that the servo placement was correct in order to achieve the intended effect. 

https://github.com/user-attachments/assets/72124490-5cad-4a04-9277-22579470c07e

![IMG_8994](https://github.com/user-attachments/assets/474fcdec-db95-41e3-9799-f0ac63aeedbb)

### Reflections: 
Prototyping quickly is fun -- especially knowing that this won't be the unltimate form factor. 

I played with a couple of different options for the code in at this stage however, they ultimately proved to be too difficult to implement given the hardware and the intended setting for the piece (our demo). One idea I tried out what an effect which adjusted the waves form based off of proximity to the wave e.g., if someone was 5ft away it the servo would rotate 1/5 of the way to 180 degrees, sequencing in 1/5 increments all the way to <1ft away. Unfortunately, the ultra-sonic sensor senses things in a wide cone, thus I found this almost impossible to work in a setting where many people are in proximity of the wave.

## [Week 5 (9/24)]
## Project 1: Emotive Origami

### Video Demo

[Click Here to view]([url](https://vimeo.com/1122500571?share=copy))

### Final Iterations, creating my final form, and the documentation of my hardware and software systems. 

<img width="1126" height="603" alt="image" src="https://github.com/user-attachments/assets/a3c6c0f3-95ff-4a33-9972-5d08d3d77e1e" />

### Pivot to Acrylic: 

While the origami element of the project relied on fairly simple movement, I chose to elevate both its aesthetic and function by incorporating an acrylic structure. I found beauty in exposing the internal mechanism behind the wave, allowing the viewer to both see and understand the system that drives its motion. 

Acrylic SVG File in Adobe Illustrator. For viewing purposes, I adjusted the stroke weight to be 1pt from the <.072 required for printing. 

<img width="902" height="598" alt="image" src="https://github.com/user-attachments/assets/b333422b-7aef-4cb1-ac51-dac6c2b19067" />

### Code

Code: 

``` #include <Servo.h>

const int trigPin = 7;
const int echoPin = 6;
const int servoPin = 9;
Servo myServo;

const float thresholdDist = 30.48; // 1 ft in cm
bool hasSwept = false;               // Tracks if sweep occurred
int currentAngle = 0;                // Servo's current angle

void setup() {
  Serial.begin(9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  myServo.attach(servoPin);
  myServo.write(0);
}

void loop() {
  float distance = getDistance();

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  if (distance > 0 && distance <= thresholdDist && !hasSwept) {
    sweepServo(0, 180); // Sweep from 0 to 180 smoothly
    hasSwept = true;
    currentAngle = 180;
  } else if ((distance == 0 || distance > thresholdDist) && hasSwept) {
    sweepServo(180, 0); // Sweep back from 180 to 0 smoothly
    hasSwept = false;
    currentAngle = 0;
  }

  delay(50);
}

// Smoothly moves the servo from startAngle to endAngle
void sweepServo(int startAngle, int endAngle) {
  int step = (startAngle < endAngle) ? 1 : -1;
  for (int pos = startAngle; pos != endAngle+step; pos += step) {
    myServo.write(pos);
    delay(10); // Adjust for smoother/faster motion
  }
}

// Returns measured distance in centimeters
float getDistance() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  long duration = pulseIn(echoPin, HIGH);
  return (duration * 0.034) / 2;
}
```

### Schematic

![IMG_9042](https://github.com/user-attachments/assets/4107ed40-5ab9-4546-b584-10cd2989a203)

### Reflections on the whole: 

This project was a blend of abstract design, technical prototyping, and personal inspiration, as I explored the motion and emotion of ocean waves through layered paper origami and Arduino-powered mechanics. Drawing from my own surfing experience and the elegant force of Hokusai’s wave, I used microcontroller logic to trigger dynamic movements that capture both the beauty and complexity of wave forms. The acrylic form allowed for transparent exposure of the system, adding an intentional emphasis on process, not just outcome. 

On the whole, I found the project to be an excellent reminder about how much we can achieve in just a few day or even hours time. I'm looking forward to evolving my prototyping and craft skills to build more technical and complex systems throughout the semester. 

## [Week 6 (9/29): Expressive Mechanics Prototyping & Exploration]
### Concept Sketches - Exploring Expressive Mechanics Wave Movements and Mechanisms
![IMG_9094](https://github.com/user-attachments/assets/585849f5-d0d9-4188-9f91-3bcc51e832f6)
![IMG_9093](https://github.com/user-attachments/assets/959a9670-c1b9-461f-9a2d-d708b3535c0e)
![IMG_9155](https://github.com/user-attachments/assets/83be56a1-3c97-4189-a3ac-d964c797a165)

### Reflection/Notes:
I decided to design an evolution of my last project––the Paper Wave––so that when a there is some input stemming from the computer vision program, the wave it acuated. Per my concept sketches, I intend to drive a rack and pinion system with a servo, which has a wave like structure mounted on it, which pushes a living hinge, forming a wave. For the living hinge, like in my last project, I would like to use acrylic as it resembles water. However I believe the acrylic will not be tolerant enough to handle the wave shape. 

## [Week 6 (9/31): Understanding Suhu's P5JS Code and exploring CV Solution Options]
### Code + Screens
Perplexity Thread(s): 

Understanding the code we we're given: 

https://www.perplexity.ai/search/2a7ed7be-5623-430f-bb92-d0f5031f4e23

Using Perplexity to help debug my P5Js x Arduino Issues: 

https://www.perplexity.ai/search/8f09cd1a-a70a-4328-b48c-ff1e9a67cdc0\

CV Solution Exploration (This is a thread that Elisa created and shared with me, following a conversation we had about how we might use CV and music together to make an interactive DJ experience). I used her generated code as a jumping off point for one of my earlier iterations. 

https://chatgpt.com/share/68e3e2e9-822c-8010-9e35-796fe1ef163b

### Reflections
The timeline for our project was relatively short, so I focused my attention on what I was particularly interested in learning about most; compter vision / P5JS. I'd like to use P5JS for nore projects in the future, so I found it helpful to grok how the computer vision tech early. 

Using "off the shelf" pretrained models like, Google's PoseNet, allowed for me to quickly iterate through code solutions without having to train any new models for my intended use. Now relaizing how accessible and easy to use these pretrained models are, I am eager to explore more of them in projects going forward. 

## [Week 7 (10/5)]
### Determinging Mechanisms, Designing Mechanisms, and 3D Printing

For this project, I focused on designing small functional components to drive the mechanism as well as house the components. To do so I used a mix of 3D printing––crafted in Fusion––and lazer cutting––crafted in Adobe Illustrator. 

**Adobe Illustrator Files** (I initially designed and cut an acrylic case for the hardware, but ultimately decided not to use it as it didn't fit the minimal aesthetic I was aiming for). 

<img width="417" height="742" alt="image" src="https://github.com/user-attachments/assets/eaf9c5d6-8c03-4126-a105-e0cab9f1b584" />

**Fusion Files ** –– Including Rack and Pinion and Servo/Arduino Mount

<img width="761" height="479" alt="image" src="https://github.com/user-attachments/assets/5b1e8ddb-e98a-49ff-aeb6-11f6cffbd67d" />
<img width="687" height="473" alt="image" src="https://github.com/user-attachments/assets/affdc1dd-bbe7-4a69-b402-db85303022de" />
<img width="1023" height="716" alt="image" src="https://github.com/user-attachments/assets/90cd6cf1-9532-4e73-9f5c-588665c5a4ce" />

### Reflection
I'm becoming much more comfortable designing in Fusion and 3D printing using Prusa's. I think I want to start exploring other 3D rendering softwares like Rhino next. As my interests grow in small hardware elctronics and functional robotics mechanisms––a field I am very bullish on in the coming years––I want to become very proficient at modeling fully original mechanisms which are functional, strong, and aesteticly pleasing. Something I have yet to unlock is how to develop and design a strong personal style through 3D printed forms. 

## [Week 7 (10/8, 10/9)]
### Iterating on Final P5.JS Code and Final Form
https://www.perplexity.ai/search/6b5c6613-8b8b-4e33-aa74-471a2e68a0ca

### Expressive Mechanics Video + Diagram

Video: 
[https://youtu.be/yonCoc0AZ3E](https://youtu.be/yonCoc0AZ3E?si=v62U-6BhH0Y1XrVg)

Diagram:  
<img width="1171" height="500" alt="image" src="https://github.com/user-attachments/assets/8efa3ea4-ab08-469e-941a-1c71a038f372" />


### Reflection on the Expressive Mechanics Project: 
Although the project evolved from my original vision—a water-like wave form—to a hand-waving gesture, this transformation came through continuous iteration and creative effort, rather than a dramatic change in direction. In the end, I succeeded in building both the functional software and a mechanism featuring multiple-linkage movement.

## [Week 8 (10/14, 10/17)]
### Setting up ESP32 per Roopa's tutorial, Exploring Ambient Display Options

### Setting up ESP32 (10/14)
Generally speaking the process was fairly smooth, aside from a few points of confusion e.g., the name of the ESP32 board in Arduino's IDE. I, like everyone else, experienced the issue of getting the ESP32 to immediately work with the WIFI at Berkeley due to the fact this is a newlt registered device.

### Exploring Ambient Display Options (10/17) 

## [Week 9 (10/20, 10/24)]
### ...

