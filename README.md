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
    else if (DIC <= 10 && DIC <= 20){
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
