# Button Control with ESP32 (External Resistor)

## What I explored
Using a push button as a digital input with ESP32 and controlling the built-in LED based on user interaction.

## Components Used
- ESP32
- Push Button
- Resistor 
- Breadboard
- Jumper wires

## Connections
- Button connected to GPIO 13
- Resistor used to stabilize input signal

### Pull-Up Configuration:
- One side of button → GPIO 13
- Other side → GND
- Resistor → between GPIO 13 and 3.3V

- Built-in LED:
  - GPIO 2 (internal)

## How it works
The resistor keeps the input pin at a stable HIGH state when the button is not pressed.

- Button NOT pressed → HIGH  
- Button pressed → LOW  

When the button is pressed, the input goes LOW, and the ESP32 turns ON the built-in LED.

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
