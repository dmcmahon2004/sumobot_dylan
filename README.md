# sumobot_dylan
Sumobot Blueprint 
![Screenshot (6)](https://user-images.githubusercontent.com/86384669/123455350-72a29380-d596-11eb-8642-c3efdd71768e.png)
The wheels were designed to imitate the astetic of actual wheels and stronger traction in the groves of the wheels. Including sockets for the motors to fit and rotate the wheels with enough force. 
![Screenshot (7)](https://user-images.githubusercontent.com/86384669/123455359-7504ed80-d596-11eb-98b8-1e43c27939b6.png)
![Screenshot (8)](https://user-images.githubusercontent.com/86384669/123455366-76ceb100-d596-11eb-8fbe-9381a541bef0.png)
![Screenshot (9)](https://user-images.githubusercontent.com/86384669/123455370-77674780-d596-11eb-8f22-81667421fa47.png)
![Screenshot (10)](https://user-images.githubusercontent.com/86384669/123455373-79310b00-d596-11eb-830b-2f345f3e0b6e.png)
The main body of my sumobot was created to take advantage of interior space and specific openings to acomodat all the parts needed to run my robot. The two front openings on the outer edges of my car were designed to implace smaller motors. These motors would be attached to thin plastic blades as both a defensive and offensive caracteristic. 
The frontal holes were added to place my ultrasonic sensor. I had to later modifie the lenght and width using a dremile to better fit my sensor to the body frame. 
The two rear holes were added for access towards my arduino boards and other electrical plug in's for my sumo bot. 
The rear holes in both corners are for my motors and allows to attach them without the need of screws or glue. Due to the tight spacing and plastic straps, the motors are securely attached to the body. 
A smaller slit at the bottom was also added to fit my light sensor, giving my robot rhe ability to view it's suroundings with colours and spacing between objects.


// Ultrasonic Sensor testing code. 
#include // Imports the NewPing Library.
int ledPin =(13); // Add the onboard LED on pin 13.
int trigPin = (10); // Add the Trig pin on pin 10.
int echoPin = (9); // Add the ECHO pin on pin 9.
int duration, distance; // Add types 'duration' and 'distance'.
void setup()
{
pinMode (ledPin, OUTPUT); // The LED must be controlled by Arduino, it means it is an output type.
pinMode (trigPin, OUTPUT);// Same as above, the TRIG pin will send the ultrasonic wave.
pinMode (echoPin, INPUT); // The ECHO pin will recieve the rebounded wave, so it must be an input type.
}
void loop()
{
digitalWrite (ledPin, LOW); // Here, LOW means off and HIGH means on.
digitalWrite (trigPin, HIGH);
delay(50);
digitalWrite (trigPin, LOW);
duration=pulseIn(echoPin,HIGH);
distance=(duration/2)/29.1;
if(distance <=30) // If the sensor detects an obstacle less than 30 cm in distance, the LED will start to blink.
digitalWrite (ledPin, HIGH);
delay(50);
if(distance >=30)// If no obstacle is there within 30 cm, the Led should turn off.


smaller motors: 
#include <Servo.h>
   Servo myservo; 
   int potpin = 0;    int val;
void setup() {
   myservo.attach(9); // attaches the servo on pin 9 to the servo object
}
void loop() {
   val = analogRead(potpin);
      val = map(val, 0, 1023, 0, 180);
     myservo.write(val);    delay(15);
}

light sensor:
const int IRSensor=4;
void setup() { 
// initialize the digital pin as an output.
pinMode(13, OUTPUT); 
//Pin 4 is connected to the output of IR sensor
pinMode(IRSensor,INPUT);
}
void loop() {
if(digitalRead(IRSensor)==HIGH) //Check the sensor output
{
digitalWrite(13, HIGH); // set the LED on
}
else
{
digitalWrite(13, LOW); // set the LED off
}
}

heavy motors:


int motorPin = 3;
void setup() {
}
void loop() {
   digitalWrite(motorPin, HIGH);
}
int motorPin = 9;
void setup() {
   pinMode(motorPin, OUTPUT);
   Serial.begin(9600);
   while (! Serial);
   Serial.println("Speed 0 to 255");
}
void loop() {
   if (Serial.available()) {
      int speed = Serial.parseInt();
      if (speed >= 0 && speed <= 255) {
         analogWrite(motorPin, speed);
      }
   }
}



