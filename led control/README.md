# Built-in LED Blink (ESP32)

## What I explored
Controlling the built-in LED on the ESP32 using a GPIO pin.

## Components Used
- ESP32 board

(No external components required)

## Connections
No external wiring required.

The built-in LED is internally connected to
- GPIO 2

## How it works
The ESP32 sends HIGH and LOW signals to GPIO 2, which turns the onboard LED ON and OFF at regular intervals.

## Code
See `led_blink.ino`

## Output
The onboard LED blinks continuously.

## Notes
This was my first step in understanding digital output control using ESP32.
