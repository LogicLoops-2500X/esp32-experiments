# 3 LED Brightness Control (ESP32)

## What I explored
Controlling the brightness of multiple LEDs simultaneously using PWM on ESP32.

## Components Used
- ESP32
- 3 LEDs
- 3 Resistors (220Ω recommended)
- Breadboard
- Jumper wires

## Connections
- LED1 → GPIO 5
- LED2 → GPIO 18
- LED3 → GPIO 19

- All LED cathodes → GND through resistors

## How it works
The ESP32 gradually changes the brightness of all three LEDs together.

- A loop increases brightness from 0 → 255  
- Another loop decreases brightness from 255 → 0  
- This creates a smooth fading (breathing) effect  

The same brightness value is applied to all LEDs simultaneously.

## Code
```cpp
#define led1 5
#define led2 18
#define led3 19

void setup() {
  Serial.begin(115200);

  pinMode(led1, OUTPUT);
  pinMode(led2, OUTPUT);
  pinMode(led3, OUTPUT);
}

void loop() {
  // Increase brightness
  for (int brightness = 0; brightness <= 255; brightness++) {
    analogWrite(led1, brightness);
    analogWrite(led2, brightness);
    analogWrite(led3, brightness);
    delay(10);
  }

  // Decrease brightness
  for (int brightness = 255; brightness >= 0; brightness--) {
    analogWrite(led1, brightness);
    analogWrite(led2, brightness);
    analogWrite(led3, brightness);
    delay(10);
  }
}