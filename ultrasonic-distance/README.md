# Ultrasonic Distance Measurement (ESP32)

## What I explored
Measuring distance using an ultrasonic sensor by calculating the time taken for sound waves to reflect back.

## Components Used
- ESP32
- Ultrasonic Sensor (HC-SR04)
- Jumper wires
- Breadboard

## Connections
- TRIG → GPIO 13
- ECHO → GPIO 12
- VCC → 5V (or 3.3V depending on module)
- GND → GND

## How it works
The ultrasonic sensor works by sending a sound pulse and measuring the time it takes to return.

Steps:
1. ESP32 sends a 10µs pulse to TRIG
2. Sensor emits ultrasonic wave
3. Wave reflects from object and returns
4. ECHO pin stays HIGH for the duration of travel
5. ESP32 measures this time using `pulseIn()`

Distance is calculated using:
- Speed of sound ≈ 0.0343 cm/µs
- Distance = (time × speed) / 2

## Code
```cpp
#define TRIG_PIN 13
#define ECHO_PIN 12

void setup() {
  Serial.begin(115200); 
  pinMode(TRIG_PIN, OUTPUT); 
  pinMode(ECHO_PIN, INPUT); 
}

void loop() {
  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);

  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);

  long duration = pulseIn(ECHO_PIN, HIGH);

  float distance = (duration * 0.0343) / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  delay(500);
}