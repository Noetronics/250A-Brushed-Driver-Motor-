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





