# MDes-TDF

## 9/2: Hello World + Serial Blinking
### Code + Serial Blinking
<img width="1232" height="1976" alt="image" src="https://github.com/user-attachments/assets/90138420-d788-4520-b054-015c2337f5db" />

https://github.com/user-attachments/assets/2bac4975-c0c1-4a36-994f-ffcbb5032728

Notes:
I found the exercise to be great for getting back into code and Arduino work. The wheels are turning on how I might implement serial interactions for related to music inputs, lights, and sounds.  

Code: 

/*
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

## 9/9: Write  a program to flash the onboard LED while printing Hello World to serial

### Experiment and PLAY!
Make “something interesting” happen with:
1 LEDs + 1 LDR
2 or more LEDs

Notes: 
I used an LDR to detect light sensitivity and turn off and on the two (red / blue) lights. I began with just one light (blue) and then once it was working, I added in the code, wiring, and hardware for the second light (red). Note -- the red light is dim in the video, but is turning on and off. 

Code: 

const int LDR_Pin = A0;     // LDR connected to analog pin A0
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


