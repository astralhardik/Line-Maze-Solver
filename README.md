
# 🤖 PID Controlled Maze Solver Robot

This repository contains the implementation of a **line-following maze solver robot** using **PID control logic** with IR sensors. The robot is capable of navigating a black-line maze, making directional decisions at junctions, and optimizing its path using an intelligent path-reduction algorithm.

---

## 📌 Project Overview

This robot uses five IR sensors arranged laterally to detect black lines on a white surface. Based on sensor feedback, it calculates deviation (`error`) and applies a PID controller to steer the robot precisely on the path. It can also:
- Detect junctions
- Record and optimize turns
- Execute a final optimized run through the maze

---

## 🔁 Modes of Operation

1. **Learning Mode**  
   - Follows the maze
   - Stores decisions (L, R, S, B) in a path string

2. **Final Run**  
   - Optimizes the path using known junction patterns
   - Executes the most efficient route through the maze

---

## 🧠 Key Features

- PID-controlled line following
- IR sensor-based path detection
- Multi-junction decision making
- Path optimization using string manipulation
- Final run with minimal movements
- LED indication on stop point
- Support for both **learning** and **execution** phases

---

## 📐 Hardware Setup

| Component         | Description                             |
|------------------|-----------------------------------------|
| IR Sensors (5)    | For line detection                      |
| Arduino Uno       | Main controller                         |
| L298N Motor Driver| Drives 2 DC motors                      |
| DC Motors (2)     | Left and right wheel motors             |
| LED               | Visual indication of stop condition     |
| Chassis & Wheels  | Base body of the robot                  |
| Power Supply      | Battery or external 12V supply          |

---

## 🔧 Pin Configuration

### IR Sensors

| Sensor | Arduino Pin |
|--------|-------------|
| s1     | 2           |
| s2     | 4           |
| s3     | 5           |
| s4     | 7           |
| s5     | 8           |

### Motor Pins

| Function         | Arduino Pin |
|------------------|-------------|
| Left Motor Fwd   | 9           |
| Left Motor Back  | 10          |
| Right Motor Fwd  | 11          |
| Right Motor Back | 12          |

### LED
- Pin: 13

---

## ⚙️ PID Tuning Parameters

```cpp
float kp = 40;
float ki = 1;
float kd = 0;
```

---

## 📈 Path Optimization Logic

| Pattern    | Replaced With |
|------------|----------------|
| LBL        | S              |
| LBS        | R              |
| RBL        | B              |
| SBS        | B              |
| SBL        | R              |
| LBR        | B              |

---

## 📂 File Structure

- `FinalmazeSolver_with_pid.txt` – Full maze solver with PID logic and path optimization
- `pid_hardik.txt` – Basic PID line follower implementation
- `README.md` – This documentation

---

## 🧪 Final Maze Solver Logic

- Follows the maze and logs directions at junctions
- Optimizes the path using string replacement
- Executes the optimized path in a second run
- Blinks LED at endpoint and stops

---

## 🎮 Modes in Code

| Mode Name        | Value | Description                        |
|------------------|-------|------------------------------------|
| STOPPED          | 0     | Bot stopped                        |
| FOLLOWING_LINE   | 1     | Regular PID control on line        |
| NO_LINE          | 2     | Lost line, takes recovery action   |
| RIGHT            | 3     | Executes right turn                |
| LEFT             | 4     | Executes left turn                 |

---

## 📊 Serial Output (Sample)

```text
forward
left
right
Motor stops
Motor reverse
The End
```

---

## 🛠️ Future Improvements

- Add buzzer for audio alert at endpoint
- Integrate an OLED for live path display
- Add real-time tuning for PID parameters
- Use rotary encoders for distance feedback

---


## 📄 License

This project is open for learning, modification, and educational use. Please credit the original author if reused.

---
