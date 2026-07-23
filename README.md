# Obstacle-avoiding-Robot-with-Voice-Control

The objective of this project is to design and implement an intelligent mobile robot that combines autonomous navigation with human-friendly voice interaction. The robot system is designed around the Arduino Uno microcontroller, which serves as the control unit for both autonomous navigation and manual control.

## Features
- Autonomous obstacle detection and avoidance using ultrasonic sensing
- Manual/voice-based control via Bluetooth from a smartphone app
- Seamless switching between autonomous and manual driving modes
- Real-time distance measurement and direction correction

## Components Used (BOM)

| Component | Quantity | Purpose |
|---|---|---|
| Arduino Uno | 1 | Main microcontroller/control unit |
| HC-SR04 Ultrasonic Sensor | 1 (or more) | Obstacle detection / distance measurement |
| HC-05 Bluetooth Module | 1 | Wireless voice/text command input from phone |
| L298N Motor Driver | 1 | Driving the DC motors |
| DC Geared Motors | 4 | Robot locomotion |
| Robot Chassis + Wheels | 1 set | Mechanical base |
| Servo Motor  | 1 | Rotating ultrasonic sensor for wider scanning |
| Li-ion/LiPo Battery Pack | 1 | Power supply |

Circuit Diagram



<img width="907" height="1028" alt="circuit-diagram" src="https://github.com/user-attachments/assets/93ccc093-9de6-4c85-af90-a466b3d57cf4" />




## How It Works
1. The ultrasonic sensor continuously measures distance to obstacles ahead.
2. If an obstacle is detected within a threshold distance, the Arduino automatically halts and redirects the robot (e.g., reverses and turns) to avoid collision.
3. The HC-05 Bluetooth module receives commands from a paired smartphone app, allowing manual override — the user can send simple voice-to-text or button commands (forward, back, left, right, stop) that get transmitted over Bluetooth serial.
4. The Arduino parses incoming Bluetooth commands and controls the motor driver accordingly, letting the user switch between autonomous and manual modes.

## Getting Started

### Hardware Setup
1. Connect the HC-SR04 ultrasonic sensor's Trig/Echo pins to the Arduino's digital I/O pins.
2. Wire the HC-05 Bluetooth module's TX/RX to the Arduino (via a voltage divider on RX, since Arduino is 5V and HC-05 RX expects 3.3V).
3. Connect the L298N motor driver inputs to Arduino digital pins, and motor outputs to the DC motors.
4. Power the Arduino and motor driver from the battery pack (ensure separate power rails for logic and motors if needed).

### Firmware
1. Install the [Arduino IDE](https://www.arduino.cc/en/software).
2. Open `firmware/obstacle_avoiding_robot.ino` in the IDE.
3. Select **Board: Arduino Uno** and the correct COM port.
4. Upload the sketch.

### App/Bluetooth Setup
1. Pair your phone with the HC-05 module (default PIN is usually `1234` or `0000`).
2. Use a serial Bluetooth terminal app (e.g., "Arduino Bluetooth Controller" or "Serial Bluetooth Terminal") to send commands, or a voice-to-text app that forwards recognized speech as serial text.
3. Send commands (`F` = forward, `B` = backward, `L` = left, `R` = right, `S` = stop) to manually drive the robot; leave it idle to let autonomous obstacle avoidance take over.





## Future Improvements
- Add a servo-mounted ultrasonic sensor for a wider field of view
- Integrate an actual speech-recognition module instead of relying on phone-side voice-to-text
- Add IR line-following as a secondary navigation mode
- Add an OLED display for status feedback

## License
This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
