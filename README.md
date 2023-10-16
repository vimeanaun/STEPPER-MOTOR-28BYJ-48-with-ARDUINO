# STEPPER-MOTOR-28BYJ-48-with-ARDUINO
https://youtu.be/IRSKMER-EtE

// Counter ClockWise & ClockWise

#include <Stepper.h>
#define A 7 //IN1 = A
#define B 8
#define C 9
#define D 10

int NUMBER_OF_STEPS_PER_REVOLUTION = 512;
void onestep();
void onestepreturn();

void setup()
{
  Serial.begin(9600);
  pinMode(A, OUTPUT);
  pinMode(B, OUTPUT);
  pinMode(C, OUTPUT);
  pinMode(D, OUTPUT);
  int i;
  for (i = 0; i <= NUMBER_OF_STEPS_PER_REVOLUTION; i++) {
    onestep();
    Serial.println(i);
    delay(5);
  }
  for (i = NUMBER_OF_STEPS_PER_REVOLUTION; i >= 0; i--) {
    onestepreturn();
    Serial.println(i);
    delay(5);
  }
}

void write(int a, int b, int c, int d)
{
  digitalWrite(A, a);
  digitalWrite(B, b);
  digitalWrite(C, c);
  digitalWrite(D, d);
}

void onestep()
{
  write(1, 0, 0, 0);
  delay(10);
  write(1, 1, 0, 0);
  delay(10);
  write(0, 1, 0, 0);
  delay(10);
  write(0, 1, 1, 0);
  delay(10);
  write(0, 0, 1, 0);
  delay(10);
  write(0, 0, 1, 1);
  delay(10);
}
void onestepreturn()
{
  write(0, 0, 0, 1);
  delay(10);
  write(0, 0, 1, 1);
  delay(10);
  write(0, 1, 0, 0);
  delay(10);
  write(1, 1, 0, 0);
  delay(10);
  write(0, 1, 0, 0);
  delay(10);
  write(1, 0, 0, 1);
  delay(10);
  write(1, 1, 0, 0);
  delay(10);
  write(0, 0, 0, 1);
  delay(10);
  write(0, 1, 1, 0);
  delay(10);
}
void loop()
{
  //
}
