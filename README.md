# -6-Degrees-of-Freedom-DOF-Robot-Arm-System
# 🤖 6 Degrees of Freedom Robot Arm System

A feature-rich, Arduino Nano-based 6 DOF robotic arm project with multiple motion modes and user control via an IR remote. The system features a live LCD joint angle display and smooth, controlled joint movements to avoid mechanical stress.

---

## 📦 Features

- 🎮 **IR Remote Control** for mode selection and execution
- 🔁 **Predefined Motions**: Pick and Place, Lissajous, Horizontal Sweep
- 🎛️ **Manual Mode**: Adjust joint angles using potentiometers
- 📟 **LCD Display**: Live joint angle feedback (I2C 1602 LCD)
- ⚙️ **Smooth Motion Transitions**: 1° step movement for reduced gear stress

---

## 🎮 IR Remote Control Functions

| Button        | Function |
|---------------|----------|
| **Power**     | Move arm to Home position |
| **ST/RPT**    | Reset / Stop execution |
| **EQ**        | Enable Lissajous motion |
| **Pause**     | Start horizontal sweep |
| **Func/Stop** | Enter manual mode (potentiometer control) |
| **0**         | Full tower build sequence |
| **1 - 4**     | Pick and Place at Positions 1 to 4 |
| **5 - 8**     | Multi-level stack at Position 5 (levels 1 to 4) |
| **Others**    | Reserved for future expansion |

---

## 🧰 Components & Supplies

| Component                         | Quantity |
|----------------------------------|----------|
| Arduino Nano                     | 1        |
| Kee Yees Nano I/O Expansion Board | 1       |
| I2C 1602 LCD Display             | 1        |
| IR Receiver                      | 1        |
| IR Remote                        | 1        |
| Trim Potentiometers              | 6        |
| 6DOF Robot Mechanical Kit (e.g. Yammis) | 1    |

---

## 🛠 Platforms Used

- [Arduino IDE](https://www.arduino.cc/en/software)

---

## 🚦 Modes of Operation

### 1. 🧱 Pick and Place
Moves to predefined positions, grabs blocks, and stacks them.

### 2. 🔄 Lissajous Motion
Performs figure 8, circle, ellipse, and slanted line movements.

### 3. ↔ Horizontal Sweep
Sweeps horizontally left-to-right in arcs while incrementally moving upward.

### 4. 🎚️ Manual Trim
Use potentiometers to manually adjust each joint's angle in real-time.

---

## 📟 LCD Display

- Shows joint angle positions (in degrees)
- Refreshes on each command or potentiometer adjustment

---

## ⛓ Smooth Joint Movement

The system transitions joints in **1-degree steps** instead of jumping to final values, reducing inertia and mechanical wear on servos and gears.

```cpp
// Example smooth motion function
void moveJoint(int joint, int startAngle, int endAngle) {
  int step = (startAngle < endAngle) ? 1 : -1;
  for (int i = startAngle; i != endAngle; i += step) {
    setJointAngle(joint, i);
    delay(15); // allow for smooth motion
  }
}
Clone the repo
Open the code in Arduino IDE
Select Arduino Nano as board, ATmega328P as processor
Connect components per wiring diagram
Upload the code to the Nano
Power the arm and use the IR remote to begin!
📂 6DOF_Robot_Arm/
├── robot_arm.ino             # Main Arduino code
├── wiring_diagram.png        # Schematic (optional)
├── IR_Remote_Mapping.txt     # Button mappings
├── README.md                 # This file
