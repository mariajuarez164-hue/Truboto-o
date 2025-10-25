# Truboto-o
Turbotoño is an autonomous robot that was designed for competitions
🚗 Turbotoño
Autonomous Vehicle Project

Team:

Gómez Hernández Alejandro

Zárate Luna Diego Alexander

Juárez Laurel María José

Martínez García Karla Yazmín
Group: 5° TMEC-AMBI

🌎 Project Description (English Overview)

Turbotoño is a basic autonomous vehicle designed to navigate a predefined track using sensor data to detect and avoid obstacles. The goal of this project is to explore logical programming, robotics control, and efficient mechanical design through the construction and testing of an independent, self-navigating robot.

The vehicle is capable of reading distances, reacting to nearby obstacles, making directional decisions, and moving efficiently around a circuit. This README details every step of the development process: from design and mechanical structure to electrical configuration, sensors, logic programming, and future improvements.

🧭 Table of Contents

Introduction

General Objective

Functions and Challenges

Motivation

Mobility Management

Motors

Wheels and Traction

Speed and Direction Control

Design and Efficiency

Power and Sensor Management

Power Supply

Circuit Overview

Sensors Used

Justification of Sensors

Obstacle Management

Avoidance Strategy

Logic Explanation (with Code Snippets)

How It Works

Testing and Evidence

Engineering Factor and Technical Justification

Challenges and Solutions

Future Improvements

Annexes

🧩 Introduction

In this project, the team presents Turbotoño, an autonomous robot designed to detect and avoid randomly placed obstacles on a track. The system combines mechanical design, electronic components, and logical programming to enable intelligent motion and decision-making.

Throughout this documentation, we present the design process, hardware description, circuit diagrams, programming logic, and test results. The project is part of an academic effort to develop technical and logical problem-solving abilities through robotics.

🎯 General Objective

To build, design, and program an autonomous vehicle capable of detecting and avoiding randomly positioned obstacles on a circuit. The vehicle must complete three laps in the shortest time possible, operating independently without remote control.

⚙️ Functions and Challenges

Turbotoño must:

Detect obstacles within its frontal path.

Decide whether to move forward, stop, reverse, or turn depending on sensor readings.

Complete three laps in the shortest possible time, either clockwise or counterclockwise.

Maintain efficient motion, power consumption, and sensor accuracy.

Main Challenges

Balancing speed and control.

Achieving smooth motion while avoiding sensor lag.

Designing a strong but lightweight chassis.

Managing power efficiency for longer operation.

💡 Motivation

Participating in this project allows the team to develop logical thinking, practice coding for physical systems, and understand autonomous vehicle principles. It’s also an opportunity to apply theoretical knowledge in a hands-on project and be evaluated based on performance and innovation.

🚙 Mobility Management
🧠 How Turbotoño Moves

Turbotoño’s movement depends on two geared DC motors controlled by an L298N H-Bridge module. The Arduino Nano processes sensor inputs and outputs PWM signals to the bridge, adjusting motor speed and direction.

🔩 Type of Motors and Why They Were Chosen

TT 1:90 Metal Gear Motors

These DC motor-reducers were selected because of their balance between torque and speed and their low current consumption. The metal gears improve durability and ensure consistent torque for movement on small ramps or rough surfaces.

Reduction ratio: 1:90

Voltage: 6–12V

Torque: High enough for 65mm wheels

Current Draw: Low (ideal for LiPo batteries)

Their torque provides sufficient push force to overcome minor friction, and the metal gears prevent internal wear compared to plastic gear models.

🛞 Wheels and Traction System

Rubber Wheels (65x28 mm) with Front-Wheel Drive configuration.
This choice was made to ensure:

Excellent grip on the surface.

Accurate turning with controlled traction.

Better reverse handling (important for obstacle avoidance).

Front traction allows the robot to pivot smoothly and maneuver efficiently during obstacle detection and evasion.

⚡ Speed and Direction Control

Speed and direction are managed through:

PWM (Pulse Width Modulation) from the Arduino Nano to the L298N driver.

Direction pins (IN1–IN4) control forward/reverse motion of each motor.

Enable pins (ENA/ENB) adjust speed proportionally.

This combination allows for:

Smooth acceleration.

Real-time control adjustments.

Efficient power management.

🧱 Chassis Design and Efficiency

The chassis was designed to be compact, lightweight, and balanced, made of acrylic for ease of mounting components.

The battery pack and Arduino are centered to keep the center of gravity stable.

Sensors are positioned for maximum range and accuracy.

Cable routing minimizes interference and allows for easy maintenance.

🔋 Power and Sensor Management
⚡ Power Supply

The robot is powered by four 3.7V LiPo batteries, providing stable energy for both logic (Arduino) and motors (via the L298N driver).

Advantages: Lightweight, high energy density, and long-lasting.

The total nominal voltage (~14.8V) ensures consistent performance even as the charge drops.

LiPo batteries were chosen for stability and portability.

🔌 Circuit Overview

The circuit consists of:

Arduino Nano (brain)

L298N H-Bridge (motor control)

HC-SR04 Ultrasonic Sensor (frontal detection)

Infrared Sensor (edge or object detection)

Battery pack (4x LiPo 3.7V)

Each component is connected through a common ground, ensuring signal consistency and preventing interference.

📡 Sensors Used

Ultrasonic Sensor (HC-SR04):
Detects distance using ultrasonic sound waves. Located at the front of Turbotoño, it measures the time taken for the echo to return, allowing precise distance detection.

Infrared Sensor:
Detects nearby obstacles or track edges using IR light reflection. Positioned at the lower front part of the chassis.

🤖 Justification of Sensors

Both sensors complement each other:

The ultrasonic sensor offers long-range distance measurement.

The infrared sensor provides quick reaction to closer objects.

Together, they create a dual-layer detection system, improving obstacle avoidance accuracy and reliability.

🚧 Obstacle Management
🧠 Avoidance Strategy

Turbotoño constantly monitors its front distance using the ultrasonic sensor.
When an obstacle is detected within 20 cm, it:

Stops immediately.

Moves backward for a short predetermined time.

Compares left and right distances.

Turns toward the direction with more free space.

Continues moving forward.

🧮 Logic Explanation (with Code Snippets)

Below is a simplified representation of Turbotoño’s decision-making process:

// Distance reading and motion logic
if (frontDistance > 20) {
  moveForward();
} else {
  stopMotors();
  moveBackward();
  delay(800);

  if (leftDistance > rightDistance) {
    turnLeft();
  } else {
    turnRight();
  }
}


The logic relies on:

Continuous distance measurement (frontDistance, leftDistance, rightDistance).

Conditional statements to decide movement.

Delay periods to ensure stable turns.

This simple structure allows efficient, reactive motion without complex computation.

⚙️ How It Works

Power On:
The robot initializes sensors and motor pins.

Constant Reading:
It continuously reads the front sensor data.

Movement Decision:

If no obstacle → move forward.

If obstacle detected → stop, back up, turn toward safest direction.

Loop:
This cycle repeats indefinitely until the circuit is complete or the power is turned off.

🧪 Testing and Evidence

At the current development stage, the team has:

Verified motor response to PWM signals.

Confirmed sensor readings on serial monitor.

Simulated obstacle detection successfully.

Begun assembling the chassis and components for physical testing.

Next stages include:

Real track testing.

Performance timing (three-lap challenge).

Optimization of turning delay for efficiency.

🧠 Engineering Factor and Technical Justification

Each design choice was guided by practical and technical reasoning:

Component	Justification
Motors (TT 1:90)	High torque with low power draw, reliable for controlled speed.
Metal gears	Durable and suitable for repetitive testing cycles.
LiPo Batteries	Lightweight and efficient power source for both logic and motors.
Ultrasonic Sensor	Precise obstacle detection up to several centimeters away.
Infrared Sensor	Fast close-range detection and track following.
Chassis	Lightweight acrylic provides rigidity without excess weight.

This combination allows Turbotoño to perform efficiently and consistently in the obstacle course.

⚔️ Challenges and Solutions
Challenge	Solution
Unstable sensor readings	Added averaging filter to stabilize data.
Power drops during motion	Separated motor and logic power lines with capacitors.
Uneven traction	Adjusted wheel alignment and weight balance.
Timing delays	Tuned code delays for smoother movement.

Each issue was documented and resolved through iterative testing and teamwork.

🚀 Future Improvements

The next goals for Turbotoño include:

Adding line-following functionality for track precision.

Using encoders to measure wheel speed and distance traveled.

Incorporating Bluetooth or Wi-Fi modules for remote debugging.

Improving chassis design with 3D printed parts for better weight distribution.

Expanding the code logic with PID control for smoother turns.

These improvements would transform Turbotoño from a basic autonomous car into a more advanced and adaptable robotic platform.

📎 Annexes
📁 Source Code

Main Arduino sketch (turbotono.ino)

Library dependencies (NewPing.h, Servo.h, etc.)

⚡ Electrical Diagrams

Motor driver connections

Sensor input pins (front, left, right)

Power distribution layout

🧰 CAD Files

STL and DXF files for chassis design

Mounting bracket models

🖥️ GitHub Repository

All code, diagrams, and design files are hosted in the Turbotoño Repository:
👉 [link placeholder]

🧾 Conclusion

The Turbotoño Project represents a complete journey from conceptual design to implementation of an autonomous system.
It demonstrates the integration of mechanics, electronics, and programming into a single, functional robot.

Through this project, the team developed:

Problem-solving and logical reasoning.

Practical knowledge of power and motion systems.

Understanding of autonomous navigation.

While there is room for improvement, the foundations built here are strong enough to support future versions of Turbotoño that can navigate complex environments and perform more sophisticated tasks.

“Turbotoño” — Simple, efficient, and autonomous.
