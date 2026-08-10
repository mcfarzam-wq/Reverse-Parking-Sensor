**Project Overview**

An Arduino-based reverse parking sensor prototype that uses an ultrasonic sensor to measure the distance to nearby obstacles. The system indicates the distance level using three LEDs:

-Far distance: Green LED ON, buzzer OFF

-Medium distance: Yellow LED ON, buzzer OFF

-Close distance: Red LED ON, buzzer ON

This project demonstrates the basic functionality of a vehicle reverse parking sensor using an Arduino and an ultrasonic sensor.

[open the simulation, codes and circuit diagram](https://wokwi.com/projects/471873504875075585)

**How It Works**

1. The Arduino code makes the ultrasonic sensor work by sending an ultrasonic pulse. When the pulse is sent, it travels toward the nearest obstacle, hits it, and returns to the sensor. The ultrasonic sensor measures the time it takes for the pulse to return, and the Arduino stores this value in a variable. The Arduino then multiplies the value by "0.0343" and divides it by "2". The result is stored in a new integer variable, converting the measured distance into centimeters.

2. Based on the measured distance in centimeters, the Arduino turns the LEDs and buzzer on or off.

[My other projects on wokwi simulator](https://wokwi.com/makers/farzamfahimpour)

**Photos and videos**

```cpp
#define Trig 2
#define Echo 3
#define LEDG 4
#define LEDY 5
#define LEDR 6
#define BUZ 9
void setup() {
  pinMode (Echo, INPUT);
  pinMode (Trig, OUTPUT);
  pinMode (LEDG, OUTPUT);
  pinMode (LEDY, OUTPUT);
  pinMode (LEDR, OUTPUT);
  pinMode (BUZ, OUTPUT);
}

void loop() {
  digitalWrite (Trig, LOW);
  delayMicroseconds (2);

  digitalWrite (Trig, HIGH);
  delayMicroseconds (20);
  digitalWrite (Trig, LOW);

  long Distance = pulseIn (Echo, HIGH);
  int DIC = Distance * 0.0343 / 2;

  if (DIC > 20) {
    digitalWrite (LEDG, HIGH);
    digitalWrite (LEDY, LOW);
    digitalWrite (LEDR, LOW);
    digitalWrite (BUZ, LOW);
  }
  else if (DIC > 10 && DIC <= 20) {
    digitalWrite (LEDG, LOW);
    digitalWrite (LEDY, HIGH);
    digitalWrite (LEDR, LOW);
    digitalWrite (BUZ, LOW);
  }
    else if (DIC <= 10){
    digitalWrite (LEDG,LOW);
    digitalWrite (LEDY,LOW);
    digitalWrite (LEDR,HIGH);
    digitalWrite (BUZ,HIGH);
    delay (100);
    
    digitalWrite (BUZ,LOW);
    delay (100);
  }
    delay (100);
  }
  ```
