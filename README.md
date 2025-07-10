# Dual Servo Motor Sweep with Arduino

This Arduino project controls two servo motors in opposite sweeping motions using an Arduino UNO board. It is great for beginners learning about servo control and `for` loops.

## 📹 Demo Video

Watch the video demonstration:  
[🎥 Video File](./IMG_0570%20(4).MP4)

## 🖼️ Circuit Diagram

![Servo Circuit Diagram](./Screenshot%202025-07-10%20190257.png)

## 🔧 Components Used

- Arduino UNO board
- 2 × Servo motors (e.g., SG90)
- Jumper wires
- USB cable (for power and programming)
- Optional: External power supply for servos

## 🔌 Wiring

- **Servo 1 signal wire (orange)** → Digital Pin **8**  
- **Servo 2 signal wire (orange)** → Digital Pin **9**  
- Both servo **VCC (red wires)** → Arduino **5V**  
- Both servo **GND (brown wires)** → Arduino **GND**


---

## 💻 Arduino Code

```cpp
#include <Servo.h>

Servo servo1; // First servo
Servo servo2; // Second servo

void setup() {
  servo1.attach(8);  // Connect first servo to pin 8
  servo2.attach(9);  // Connect second servo to pin 9
}

void loop() {
  // Sweep: servo1 from 0 to 180, servo2 from 180 to 0
  for (int pos = 0; pos <= 180; pos++) {
    servo1.write(pos);           // First servo moves forward
    servo2.write(180 - pos);     // Second servo moves in reverse
    delay(15);
  }

  // Sweep back: servo1 from 180 to 0, servo2 from 0 to 180
  for (int pos = 180; pos >= 0; pos--) {
    servo1.write(pos);           // First servo moves backward
    servo2.write(180 - pos);     // Second servo moves forward
    delay(15);
  }
}
