#include <Servo.h>

// Define the servos
Servo s_Right;
Servo s_Middle;
Servo s_Left;

// Define the ultrasonic sensor pins
int trigPin1 = 2; 
int echoPin1 = 3;
int trigPin2 = 4; 
int echoPin2 = 5;
int trigPin3 = 6; 
int echoPin3 = 7;

void setup() {
  // Attach the servos to the appropriate pins
  s_Right.attach(9);
  s_Middle.attach(10);
  s_Left.attach(11);
  Serial.begin(9600);

  // Initialize the ultrasonic sensor pins
  pinMode(trigPin1, OUTPUT);
  pinMode(echoPin1, INPUT);
  pinMode(trigPin2, OUTPUT);
  pinMode(echoPin2, INPUT);
  pinMode(trigPin3, OUTPUT);
  pinMode(echoPin3, INPUT);

  Stop();
  delay(2000);
}

void loop() {
  // Get the distance from the ultrasonic sensors
  int distance1 = getDistance(trigPin1, echoPin1);
  int distance2 = getDistance(trigPin2, echoPin2);
  int distance3 = getDistance(trigPin3, echoPin3);

  Serial.print(distance1);
  Serial.print("\t");
  Serial.print(distance2);
  Serial.print("\t");
  Serial.println(distance3);

  // If an obstacle is detected in front, move left
  if (distance1 < 15) {
    moveLeft();
  }
  // If an obstacle is detected on the right, move forward
  else if (distance2 < 15) {
moveLeft();  }
  // If an obstacle is detected on the left, move right
  else if (distance3 < 15) {
    moveRight();
  }
  // If no obstacle is detected, move forward
  else {
    moveForward();
  }
}

int getDistance(int trigPin, int echoPin) {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  int duration = pulseIn(echoPin, HIGH);
  int distance = duration * 0.034 / 2;
  return distance;
}

void moveLeft() {
  s_Middle.write(110);
  delay(10);
  s_Right.write(70);
  s_Left.write(110);
  delay(150);
  
  s_Middle.write(70);
  delay(10);
  s_Right.write(110);
  s_Left.write(70);
  delay(150);

}

void moveRight() { //verifcado

  s_Middle.write(70);
  delay(10);
  s_Right.write(70);
  s_Left.write(110);
  delay(150);
  
  s_Middle.write(110);
  delay(10);
  s_Right.write(110);
  s_Left.write(70);
  delay(150);


}



void moveForward() { 

 s_Middle.write(70);
  delay(10);
  s_Right.write(110);
  s_Left.write(110);
  delay(150);
  
  s_Middle.write(110);
  delay(10);
  s_Right.write(70);
  s_Left.write(70);
  delay(150);


}

void moveBackward() {
  
 s_Middle.write(110);
  delay(10);
  s_Right.write(110);
  s_Left.write(110);
  delay(150);
  
  s_Middle.write(70);
  delay(10);
  s_Right.write(70);
  s_Left.write(70);
  delay(150);
}

//STOP
void Stop() {
s_Right.write(90);
s_Middle.write(90);
s_Left.write(90);
}
