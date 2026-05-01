# ESP32 Soil Moisture Monitor with LED Indicator

## Overview
This project uses an ESP32 and a resistive soil moisture sensor to monitor the hydration levels of soil. The system categorizes the soil as **Dry**, **Moist**, or **Wet** based on analog readings and provides a visual alert by blinking the ESP32's built-in LED when the soil is completely wet.

## Components Used
*   **Microcontroller:** ESP32 Dev Module
*   **Sensor:** Soil Moisture Sensor (Resistive)
*   **Indicator:** Built-in LED (GPIO 2)
*   **Breadboard & Jumper wires**

## Threshold Logic
The ESP32 reads analog values from 0 to 4095. The code uses the following thresholds:

*   **Dry Soil:** Analog value > 3500 (LED OFF)
*   **Moist Soil:** Analog value between 1500 and 3500 (LED OFF)
*   **Wet Soil:** Analog value ≤ 1500 (Built-in LED Blinks)

## How It Works
1.  The sensor measures soil resistance, which decreases as moisture increases.
2.  The ESP32 reads the analog voltage on **GPIO 34**.
3.  The serial monitor displays the raw "Soil Value" and the interpreted status.
4.  When the soil reaches the "Wet" threshold, a `delay()`-based blink sequence is triggered on **GPIO 2** to alert the user.

## Code
```cpp
#define i_m_sensor 34
#define ledPin 2    // Inbuilt LED of ESP32

void setup()
{
  Serial.begin(9600);
  pinMode(ledPin, OUTPUT);
}

void loop()
{
  int sense_it = analogRead(i_m_sensor);

  Serial.print("Soil Value: ");
  Serial.println(sense_it);

  if (sense_it > 3500)
  {
    Serial.println("Status: Dry Soil ");
    digitalWrite(ledPin, LOW);
  }
  else if (sense_it <= 3500 && sense_it > 1500)
  {
    Serial.println("Status: Moist Soil ");
    digitalWrite(ledPin, LOW);
  }
  else
  {
    Serial.println("Status: Wet Soil ");
    // Blink Inbuilt LED when completely wet
    digitalWrite(ledPin, HIGH);
    delay(500);
    digitalWrite(ledPin, LOW);
    delay(500);
  }
  delay(1000);
}