# ESP32 Button-Controlled LED (Pull-Down Configuration)

## Project Overview
This project uses a push button in a **Pull-Down** configuration to control the ESP32's onboard LED. When the button is pressed, it sends a HIGH signal to GPIO 13, triggering the LED on GPIO 2.

## Components Used
*   **Microcontroller:** ESP32 Dev Module
*   **Input:** Push Button
*   **Resistor:** (External Pull-Down)
*   **LED:** Onboard LED (GPIO 2)
*   **Breadboard & Jumper wires**

## Connections
To match the logic in the provided code, follow these specific wiring steps:

1.  **Input Signal:** Connect **GPIO 13** to one side of the Push Button.
2.  **Power:** Connect the other side of the Push Button to the **3.3V** pin.
3.  **Pull-Down Resistor:** Connect a **10kΩ resistor** from **GPIO 13** to **GND**.
    *   *Why?* This ensures GPIO 13 stays at 0V (LOW) when the button is not pressed.
4.  **Output:** The built-in LED is internally connected to **GPIO 2**.

## How it Works
*   **Button NOT Pressed:** GPIO 13 is connected to GND via the resistor. `digitalRead` returns `LOW`. LED stays **OFF**.
*   **Button Pressed:** 3.3V flows to GPIO 13. `digitalRead` returns `HIGH`. LED turns **ON**.

## Code
```cpp
#define BUTTON_PIN 13
#define LED_PIN 2

void setup() {
  pinMode(BUTTON_PIN, INPUT);  // Reading from the external pull-down circuit
  pinMode(LED_PIN, OUTPUT);
  
  // Initial state: LED OFF
  digitalWrite(LED_PIN, LOW);
}

void loop() {
  // Check if button is pressed (HIGH)
  if (digitalRead(BUTTON_PIN) == HIGH) {
    digitalWrite(LED_PIN, HIGH);
  } else {
    digitalWrite(LED_PIN, LOW);
  }
}