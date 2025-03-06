# DC Motor Driver 250A continuous current

## Specification
- Supply Voltage 12v - 24v DC
- Winsok Semicon WSK250N03 250 A continuous current
- Mode 4 PWM (In_H+, In_L+, In_H-, In_H-)
- positive overtravel limit & negative overtravel limit
- buit-in current sensing
- 5v 2A BEC output

## Connector Pin out 
![IDC](https://github.com/user-attachments/assets/7bb2627c-7547-4325-87fc-089639590858)
- Pin 1 : 5V 2A BEC output
- Pin 2 : H_In-
- Pin 3 : H_In+
- Pin 4 : L_In-
- Pin 5 : L_In+
- Pin 6 : Cut_M- (
set to logic low to stop CCW rotation, CW rotation can still be done)
- Pin 7 : Cut_M+ (
set to logic low to stop CW rotation, CCW rotation can still be done)
- Pin 8 : Current sensing (connect to analog input to read V-shunt value)
- Pin 9 : 12V
- Pin 10 : GND

## Circuit Example
![circuit_image](https://github.com/user-attachments/assets/36d45656-ea33-4683-9479-8983e37b6df3)

## Code Example
You need this library https://github.com/khoih-prog/AVR_PWM to run the code below
```C++
#define _PWM_LOGLEVEL_ 4
#include "AVR_PWM.h"

#define H1 2
#define L1 3
#define H2 6
#define L2 7
#define Cut1 10
#define Cut2 11

AVR_PWM* PWM[4];
uint16_t Freq = 20000;
float dutty;

void setup() {
  pinMode(L1, OUTPUT);
  pinMode(L2, OUTPUT);
  pinMode(H1, OUTPUT);
  pinMode(H2, OUTPUT);
  pinMode(Cut1, OUTPUT);
  pinMode(Cut2, OUTPUT);
  PWM[0] = new AVR_PWM(H1, Freq, 0);
  PWM[1] = new AVR_PWM(H2, Freq, 0);
  PWM[2] = new AVR_PWM(L1, Freq, 0);
  PWM[3] = new AVR_PWM(L2, Freq, 0);

  digitalWrite(Cut1, HIGH);
  digitalWrite(Cut2, HIGH);
  delay(100);
}

void loop() {
CW (10.0);
delay (1000);
CW (0.0);
delay (1000);
CCW (10.0);
delay (1000);
CCW (0);
delay (1000);
}

void CW(float duty_cycle) {
  digitalWrite(L1, LOW);
  digitalWrite(H1, LOW);
  PWM[3]->setPWM(L2, Freq, duty_cycle);
  PWM[1]->setPWM(H2, Freq, duty_cycle);
}

void CCW(float duty_cycle) {
  digitalWrite(L2, LOW);
  digitalWrite(H2, LOW);
  PWM[2]->setPWM(L1, Freq, duty_cycle);
  PWM[0]->setPWM(H1, Freq, duty_cycle);
}
```





