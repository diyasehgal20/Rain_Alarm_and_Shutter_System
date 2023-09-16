#include <Servo.h>

#define BUZZER_PIN 3
#define RAIN_SENSOR A1

Servo myServo;

int rainThreshold = 700; // Threshold value for rain detection
int servoStartPosition = 0; // Initial position of the servo
int servoEndPosition = 280; // Final position of the servo

void setup()
{
  pinMode(BUZZER_PIN, OUTPUT);
  Serial.begin(9600);
  myServo.attach(9);
  myServo.write(servoStartPosition);
}

void loop()
{
  int sensorValue = analogRead(RAIN_SENSOR);
  Serial.println(sensorValue);
  
  if (sensorValue < rainThreshold)
  {
    analogWrite(BUZZER_PIN, 100);
    int motor = map(sensorValue, 220, 1023, servoStartPosition, servoEndPosition);
    myServo.write(motor);
  }
  else
  {
    analogWrite(BUZZER_PIN, 0);
    myServo.write(servoStartPosition);
  }

  delay(1000);
}
