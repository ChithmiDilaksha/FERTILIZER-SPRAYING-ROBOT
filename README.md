# FERTILIZER SPRAYING ROBOT

## YouTue Video for prototype
https://youtu.be/eAUUa23bQjI?si=Efv6AeVrxratzVMY


## Source code
```sh 
const int motorA_IN1 =9;
const int motorA_IN2 =8 ;
const int motorA_ENA =10 ;

const int motorB_IN3 =7 ;
const int motorB_IN4 =6;
const int motorB_ENB =5;

#define trigPin 12

#define echoPin 13





void setup() {

Serial.begin (9600);

pinMode(trigPin, OUTPUT);

pinMode(echoPin, INPUT);

  pinMode(motorA_IN1, OUTPUT);
  pinMode(motorA_IN2, OUTPUT);
  pinMode(motorA_ENA, OUTPUT);

  pinMode(motorB_IN3, OUTPUT);
  pinMode(motorB_IN4, OUTPUT);
  pinMode(motorB_ENB, OUTPUT);
  
   stopMotors();
}

void loop() {

  // Move forward
  moveForward();
  delay(2000);  // Move forward for 2 seconds

  // Stop motors
  stopMotors();
  delay(1000);  // Stop for 1 second

  // Move backward
  moveBackward();
  delay(2000);  // Move backward for 2 seconds

  // Stop motors
  stopMotors();
  delay(1000);  // Stop for 1 second


  long duration, distance;


digitalWrite(trigPin, LOW);

delayMicroseconds(2);

digitalWrite(trigPin, HIGH);

delayMicroseconds(10);

digitalWrite(trigPin, LOW);

duration = pulseIn(echoPin, HIGH);

distance = (duration/2) / 29.1;

if (distance < 20) {
    // Stop motors if object is detected within 20 cm
    stopMotors();
  } 
  else 
  {
    // Move motors forward
    moveForward() ;
  }

  delay(100);
}

  void moveForward() 
  {
  // Motor A forward
  digitalWrite(motorA_IN1, HIGH);
  digitalWrite(motorA_IN2, LOW);
  analogWrite(motorA_ENA, 300);  // Full speed

  // Motor B forward
  digitalWrite(motorB_IN3, HIGH);
  digitalWrite(motorB_IN4, LOW);
  analogWrite(motorB_ENB, 300);  // Full speed
}

void moveBackward() {
  // Motor A backward
  digitalWrite(motorA_IN1, LOW);
  digitalWrite(motorA_IN2, HIGH);
  analogWrite(motorA_ENA, 300);  // Full speed

  // Motor B backward
  digitalWrite(motorB_IN3, LOW);
  digitalWrite(motorB_IN4, HIGH);
  analogWrite(motorB_ENB, 300);  // Full speed
}

void stopMotors() {
  // Motor A stop
  digitalWrite(motorA_IN1, LOW);
  digitalWrite(motorA_IN2, LOW);
  analogWrite(motorA_ENA, 0);

  // Motor B stop
  digitalWrite(motorB_IN3, LOW);
  digitalWrite(motorB_IN4, LOW);
  analogWrite(motorB_ENB, 0);
}
