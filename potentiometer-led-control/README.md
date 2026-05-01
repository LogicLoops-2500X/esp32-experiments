# LED Brightness Control using Potentiometer (ESP32)

## What I explored
Controlling LED brightness using analog input from a potentiometer and PWM output on ESP32.

## Components Used
- ESP32
- LED
- Resistor (220Ω)
- Potentiometer
- Breadboard
- Jumper wires

## Connections
### Potentiometer:
- One side → 3.3V
- Other side → GND
- Middle pin → GPIO 34 (analog input)

### LED:
- Anode → PWM pin (e.g., GPIO 2)
- Cathode → GND (via resistor)

## How it works
The potentiometer provides a variable voltage (0–3.3V).

- ESP32 reads this as an analog value (0–4095)
- This value is mapped to PWM output
- PWM controls LED brightness

## Code
```cpp
#define potPin 34    // Potentiometer middle pin connected to GPIO 34
#define ledPin 5     // LED connected to GPIO 5

void setup() {
  Serial.begin(115200);
  
  pinMode(ledPin, OUTPUT);
}

void loop() {
  int potValue = analogRead(potPin);  // Read potentiometer value (0 to 4095)
  
  int brightness = map(potValue, 0, 4095, 0, 255); // Convert to PWM range
  
  analogWrite(ledPin, brightness);    // Set LED brightness
  
  Serial.print("Pot Value: ");
  Serial.print(potValue);
  Serial.print("  Brightness: ");
  Serial.println(brightness);
  
  delay(100);
}