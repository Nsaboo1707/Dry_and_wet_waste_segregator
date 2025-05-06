# 🌱 Dry/Wet Waste Segregator using Arduino

An automated **Dry and Wet Waste Segregator** that uses an ultrasonic sensor to detect the presence of waste and a soil/moisture sensor to determine its type—dry or wet. A servo motor then sorts the waste accordingly.

## 📽️ 1. Demo Video

Watch the working demo here:  
👉 [https://drive.google.com/file/d/1MKrkFj3OkoPq0llMe6Bj80mbuZWkB4T1/view?usp=drivesdk](#)  
*Replace `#` with your actual video link (YouTube/Drive/etc.).*


![WhatsApp Image 2025-05-05 at 17 26 58_56b71f39](https://github.com/user-attachments/assets/c62a4a99-3c91-430c-ad4e-bf6e6cce233e)

---

## 🧰 2. Hardware Components Required

1. Arduino Uno/Nano
2. Ultrasonic Sensor (HC-SR04)
3. Soil/Moisture Sensor
4. Servo Motor (SG90/MG90S)
5. Jumper Wires
6. USB cable or 9V battery for power

---

## ⚙️ 3. Working Principle

1. **Detection**: Ultrasonic sensor checks for the presence of waste within a set distance.
2. **Classification**: Soil sensor reads the moisture level of the detected object.
3. **Sorting**: Based on the moisture reading:
   - Servo rotates to **170°** to drop *wet* waste.
   - Servo rotates to **10°** to drop *dry* waste.
   - Returns to neutral (90°) after each action.

---

## 🧾 4. Code Overview

- Written in **Arduino C++** using the `Servo.h` library.
- Moisture values are read via analog pin and mapped.
- `maxDryValue` threshold defines the cutoff between dry and wet.

## 🛠️ 5. Troubleshooting
Here are five common troubleshooting topics to help you debug and optimize your setup:

5.1 Servo Rotates Only in One Direction
This usually indicates incorrect moisture classification.

Solution: Adjust maxDryValue or calibrate the soil sensor by viewing values in the Serial Monitor.

5.2 Moisture Readings Are Inconsistent
Can occur due to power supply fluctuation or sensor noise.

Solution: Use averaging (already in the code) and ensure a stable power source.

5.3 No Output in Serial Monitor
Make sure the correct COM port and baud rate (9600) are selected.

Solution: Reconnect the board, re-upload the code, and check cable.

5.4 Servo Doesn’t Move at All
Could be wiring issue, power problem, or pin mismatch.

Solution: Check if the servo is receiving power and connected to the correct PWM pin.

5.5 Waste Not Detected Even When Placed Close
Might be due to misaligned or faulty ultrasonic sensor.

Solution: Verify distance calculation logic and re-check sensor angle and wiring.

### 📌 Main Logic Snippet:
```cpp
if(fsoil > maxDryValue) {
    Serial.println("     ==>WET Waste ");
    servo1.write(170);
} else {
    Serial.println("     ==>Dry Waste ");
    servo1.write(10);
}




