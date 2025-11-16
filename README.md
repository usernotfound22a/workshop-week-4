# workshop-week-4

For this workshop we are using ultrasonic sensor to measure the 
distance of nearby objects. 
> Required materials:-

i. Arduino Board

ii. Ultrasonic Sensor 

iii. LEDs

iv. Jumper Wires

> ### Steps
> Connect the Ultrasonic Sensor (HC-SR04)
> - VCC → 5V on Arduino
> - GND → GND on Arduino
> - Trig → Digital Pin 9
> - Echo → Digital Pin 10
**Code** 
```
 // Define the pins
const int trigPin = 9;      // trig pin of ultrasonic sensor
const int echoPin = 10;     // echo pin of ultrasonic sensor
const int ledPin  = 13;     // LED pin (inbuilt LED on Arduino)

// Variables
long duration;              // stores time taken for sound to return
float distance;             // stores calculated distance

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledPin, OUTPUT);

  Serial.begin(9600);       // initialize the serial monitor
}

void loop() {
  // Send ultrasonic pulse
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);  // correct trigger pulse = 10 microseconds
  digitalWrite(trigPin, LOW);
  
  // Read echo time
  duration = pulseIn(echoPin, HIGH);

  // Calculate distance in cm
  distance = duration * 0.034 / 2; 
  
  // Print distance
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  // --- LED blinking logic ---
  if (distance < 10) {
    // Fast blinking
    digitalWrite(ledPin, HIGH);
    delay(100);
    digitalWrite(ledPin, LOW);
    delay(100);
  } 
  else {
    // Slow blinking
    digitalWrite(ledPin, HIGH);
    delay(500);
    digitalWrite(ledPin, LOW);
    delay(500);
  }
}

```
### Task 
```
Connect the ultrasonic sensor as per the guide and write the learning reflection.
Working on the ultrasonic sensor project helped me understand how electronic components and Arduino programming work together to solve real-world problems. By connecting the HC-SR04 ultrasonic sensor with the Arduino UNO and controlling the inbuilt LED, I learned how distance measurement is performed using sound waves and how the Arduino reads and interprets sensor signals.

While writing the program, I gained experience with important Arduino functions such as pinMode(), digitalWrite(), delayMicroseconds(), and pulseIn(). I also learned how to calculate distance using the speed of sound and why timing plays a critical role in obtaining accurate sensor readings. Implementing the blinking logic improved my understanding of conditional statements and timing control using delays in milliseconds.

During the process, I identified and fixed errors, such as ensuring the correct duration of the trigger pulse and adjusting the LED response based on measured distance. This helped me develop troubleshooting skills and confidence in debugging Arduino code.

Overall, this project enhanced my knowledge of sensors, digital I/O, and microcontroller programming. It also improved my problem-solving abilities and gave me hands-on experience in building an interactive system that reacts to its environment. This learning experience will support me in future electronics and embedded system projects.
```
