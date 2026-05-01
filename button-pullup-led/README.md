# Button Control with Internal Pull-Up (ESP32)

## What I explored
Using a push button as a digital input with ESP32 and controlling the built-in LED using internal pull-up configuration.

## Components Used
- ESP32
- Push Button
- Breadboard
- Jumper wires

(No external resistor required)

## Connections
- Button connected between:
  - GPIO 13
  - GND

- Built-in LED:
  - GPIO 2 (internal to board)

## How it works
The ESP32 uses an internal pull-up resistor:

- Default state → HIGH  
- Button pressed → LOW  

This means:
- LOW = Button pressed  
- HIGH = Button released  

When the button is pressed, the ESP32 detects LOW and turns ON the LED.

## Code
```cpp
#define BUTTON_PIN 13
#define LED_PIN 2

void setup() {
  pinMode(BUTTON_PIN, INPUT_PULLUP);
  pinMode(LED_PIN, OUTPUT);
  digitalWrite(LED_PIN, LOW);
}

void loop() {
  int buttonState = digitalRead(BUTTON_PIN);

  if (buttonState == LOW) {
    digitalWrite(LED_PIN, HIGH);
  } else {
    digitalWrite(LED_PIN, LOW);
  }
}