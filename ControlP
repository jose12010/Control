#include <Servo.h>
int sensor1 = 0;
int sensor2 = 0;
int sensor = 0;
int sp = 0;
int error = 0;
int output = 0;
Servo myservo;
int pos = 0;
bool flag = false;



void setup() {
  Serial.begin(9600);
  myservo.attach(5);
  myservo.write(0);
  delay(15);
}

void loop() {
  
  sensor1 = map(analogRead(A0), 0, 1024, 0, 100);
  sensor2 = map(analogRead(A1), 0, 1024, 0, -100);
  sensor = (sensor1 + sensor2);
  error = (sensor - sp);
  output = 0.75 * error;

  if (flag) {
    
    myservo.write(pos);
    if (abs(output)>5) { flag = false; }
    delay(50);

  } else {
    
    if (output > 0) {
      pos++;
    } else if (output < 0) {
      pos--;
    } else {
      flag = true;
    }

    myservo.write(pos);
    delay(50);
  }

  Serial.print("0");
  Serial.print(0);
  Serial.print(",");
  Serial.print("100:");
  Serial.print(100);
  Serial.print(",");
  Serial.print("Error:");
  Serial.print(error);
  Serial.print(",");
  Serial.print("Output:");
  Serial.print(output);
  Serial.print(",");
  Serial.print("sensor:");
  Serial.print(sensor);
  Serial.print(",");
  Serial.print("SetPoint:");
  Serial.println(sp);
}
