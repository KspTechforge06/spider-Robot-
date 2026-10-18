
# what changed 
| Feature | Original Arduino Nano code | New ESP8266 code |
|---|---|---|
| Controller | Arduino Nano | NodeMCU ESP8266 |
| Servo control | Direct GPIO | PCA9685 PWM driver |
| Number of servos | 12 | 12 |
| Servo library | `Servo.h` | `Adafruit_PWMServoDriver.h` |
| Timing | FlexiTimer2 | Cooperative updates using `millis`-independent service calls and `delay(20)` |
| Inverse kinematics | Original calculations | Preserved with numerical safeguards |
| Walking algorithm | Original | Preserved |
| Wi-Fi control | Not implemented in the original demonstration loop | Not yet implemented |
| Movement demonstration | Automatic | Automatic |


# Connections 

| NodeMCU ESP8266 | PCA9685 |
|---|---|
| 3V3 | VCC |
| GND | GND |
| D2 (GPIO4) | SDA |
| D1 (GPIO5) | SCL |

Connect your 12 servos to PCA9685 channels 0–11 according to the mapping in the code.
Power connections
- Power the NodeMCU using a regulated supply suitable for its input.
- Supply the servos through the PCA9685's separate V+ power connection.
- Connect the controller, PCA9685, and servo-supply grounds together.
- Do not connect the 12 V battery directly to the servo-power terminal.
Your 5 V/3 A UBEC might not supply enough current for all 12 servos. Check the servo specifications and size the supply accordingly.
4. Before running the robot
Please follow this sequence for the first test:
1. Upload the code with the servos disconnected.
2. Confirm that the ESP8266 starts without resetting.
3. Connect one servo to PCA9685 channel 0.
4. Test its movement and confirm its rotation direction.
5. Verify the remaining channels against your motor-numbering diagram.
6. Test the complete robot with its legs supported above the ground.
7. Only attempt walking after confirming that all joints move in the correct directions.
The code assumes a 50 Hz servo signal and a pulse range of 500–2500 μs. These settings may need adjustment for your specific servo model.

One final distinction
This version automatically runs the original movement demonstration. It does not yet provide a mobile-phone control interface over Wi-Fi. That can be added separately once the servo mapping and walking sequence are working correctly.
