# Two LED Blink using ESP32

## What I explored
Controlling multiple digital outputs simultaneously using ESP32.

## Components Used
- ESP32
- 2 LEDs
- 2 Resistors (220Ω or similar)
- Breadboard
- Jumper wires

## Connections
- LED1 → GPIO 2
- LED2 → GPIO 4
- Both LEDs connected to GND through resistors

## How it works
The ESP32 sends HIGH signals to both GPIO pins at the same time, turning both LEDs ON.  
Then it sends LOW signals, turning both LEDs OFF.  
This repeats, creating a blinking effect.

## Code
```cpp
#define LED1 2
#define LED2 4

void setup() {
  pinMode(LED1, OUTPUT);
  pinMode(LED2, OUTPUT);
}

void loop() {
  digitalWrite(LED1, HIGH);
  digitalWrite(LED2, HIGH);
  delay(1000);

  digitalWrite(LED1, LOW);
  digitalWrite(LED2, LOW);
  delay(1000);
}