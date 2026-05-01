# Touch Sensor Controlled Buzzer (ESP32)

## What I explored
Using a digital touch sensor module to control a buzzer using ESP32.

## Components Used
- ESP32
- Touch Sensor Module (TTP223 or similar)
- Buzzer
- Jumper wires
- Breadboard

## Connections
### Touch Sensor:
- VCC → 3.3V
- GND → GND
- OUT → GPIO 4

### Buzzer:
- Positive → GPIO 18
- Negative → GND

## How it works
The touch sensor module outputs a digital signal:

- NOT touched → LOW  
- Touched → HIGH  

The ESP32 reads this signal using `digitalRead()`.

- When touched → buzzer turns ON  
- When not touched → buzzer stays OFF  

## Code
```cpp
#define touchPin 4
#define buzzerPin 18

void setup() {
  Serial.begin(9600);

  pinMode(touchPin, INPUT);
  pinMode(buzzerPin, OUTPUT);

  digitalWrite(buzzerPin, LOW);
}

void loop() {
  int touchState = digitalRead(touchPin);

  if (touchState == HIGH) {
    digitalWrite(buzzerPin, HIGH);
    Serial.println("Touched! Buzzer ON");
  }
  else {
    digitalWrite(buzzerPin, LOW);
    Serial.println("Not touched");
  }

  delay(100);
}