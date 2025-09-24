# Cost-Effective 6 DOF robotic arm

A budget friendly 6-degree-of-freedom homemade robotic arm offering both precision and a strong load capacity for its price range.

![Robot Arm CAD](/Images/CADdrawing.jpg)
![Robot Arm real](/Images/realthing.jpg)

## 🤖 Overview

This project features a fully functional 6-DOF robotic arm that combines:
- **3D printed mechanical components** for easy production and construction
- **Stepper motor actuation** for precise positioning
- **Powerfull motor controller** for driving high-torque motors with precise control
- **Arduino-based control system** for accessibility and expandability
- **Open-loop control** for simplicity, reliability and easy maintenance


## ✨ Features

- **6 Degrees of Freedom**: Full spatial movement capability
- **Stepper Motor Control**: Precise angular positioning
- **3D Printable Design**: Accessible manufacturing with standard FDM printers
- **Arduino Compatible**: Easy programming and customization
- **Open Source**: Complete design files and code available
- **standard hardware**: Easy assembly and easy to find online

## 📋 Specifications

| Parameter | Value |
|-----------|-------|
| Degrees of Freedom | 6 |
| Motor Type | Stepper Motors |
| Control System | Arduino-based |
| Control Method | Open-loop |
| Construction | 3D Printed frame + Standard Components |
| Workspace | 500mm radius |
| Payload Capacity | ~300g |
| Repeatability | ✅ |

## 🛠️ Hardware Requirements

### Electronics
- **Arduino Board** Arduino mega 2560
- **Stepper Motor Drivers** TMC2209 × 3 , LM542 x 3
- **Stepper Motors**
   - **Joint 1** NEMA23x56
   - **Joint 2** NEMA17x60 with 1:50 planetary gearbox
   - **Joint 3** NEMA17x48 with 1:27 planetary gearbox
   - **Joint 4** NEMA11x34 with 1:20 planetary gearbox
   - **Joint 5** NEMA14x40
   - **Joint 6** NEMA11x34
- **Power Supply** 24V 50W
- **Limit Switches** optical endstop x 6
- **Pin Header** and **General-Purpose Printed Circuit Board**(for the only custom extension board)


### Frame
- **3D Printed Parts** (see `/3D-model` folder)

### Mechanical Components
- **Bearings** 
   - 6009 x 2
   - 6007 x1
- **Screws and Fasteners** M3, M4, M5 bolts and nuts

### Tools Required
- 3D Printer (FDM, 200×200×200mm minimum build volume)
- Screwdrivers
- Allen keys/Hex keys
- Wire strippers
- Multimeter
- Laser cutter(optional, You can use drill and hand saw)

## 🔧 Assembly Instructions

Detailed assembly instructions with images available in `/Docs/assembly.pdf`

## 💻 Software Setup

### Prerequisites
- Arduino IDE (latest version)
- Required Libraries:
  - `AccelStepper`
  - `MultiStepper`
  - `math`
  - `Servo` (if using servo gripper)

## 🎮 Usage

### Basic Control
The robot arm can be controlled through:
- **Serial Commands**: Send position commands via serial monitor
- **I2C**: Send position from other device or microcontroller

### Command Examples
```
// Move to joint positions (degrees)
jm 45 30 -20 0 45 90

// Move to Cartesian position (first three in mm,last three in rad)
IK 200 150 100 0 90 0

// Home all joints
zro

// Control gripper
clm 95

```

## 📊 Kinematics

The robot arm uses standard Denavit-Hartenberg parameters for kinematic calculations. Forward and inverse kinematics algorithms are implemented for position control.

### Joint Configuration
- **Joint 1**: Base rotation (±90°)
- **Joint 2**: Shoulder pitch (±90°)
- **Joint 3**: Elbow pitch (±160°)
- **Joint 4**: Wrist roll (±180°)
- **Joint 5**: Wrist pitch (±90°)
- **Joint 6**: Wrist yaw (±180°)

## 🚀 Future Enhancements

- [ ] Closed-loop control with encoders
- [ ] Vision system integration
- [ ] ROS compatibility
- [ ] Mobile app control
- [ ] Advanced path planning
- [ ] Machine learning integration
- [ ] Multi-arm coordination

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests, report bugs, or suggest improvements.

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Arduino community for libraries and support
- 3D printing community for design inspiration
- Robotics researchers for kinematic algorithms
- Open-source contributors

**⭐ Star this repository if you find it helpful!**
