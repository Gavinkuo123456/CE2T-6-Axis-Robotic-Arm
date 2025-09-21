# Cost-Effective 6 DOF robotic arm

A cost-effective 6-degree-of-freedom robotic arm offering both precision and a strong load capacity for its price range.

![Robot Arm CAD](/Images/CADdrawing.jpg)
![Robot Arm real](/Images/realthing.jpg)

## 🤖 Overview

This project features a fully functional 6-DOF robotic arm that combines:
- **3D printed mechanical components** for cost-effective construction
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
| Construction | 3D Printed + Hardware |
| Workspace | ? |
| Payload Capacity | ? |
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
   - **Joint 5** NEMA 14x40
   - **Joint 6** NEMA11x34
- **Power Supply** 24V 50W
- **Jumper Wires** and **Breadboard/PCB**
- **Limit Switches** optical endstop x 6

# WIP below

### Mechanical Components
- **3D Printed Parts** (see `/mechanical` folder)
- **Bearings** (608ZZ or similar)
- **Screws and Fasteners** (M3, M4, M5 bolts and nuts)
- **Timing Belts and Pulleys** (GT2)
- **Linear Rods** (8mm diameter)

### Tools Required
- 3D Printer (FDM, 200×200×200mm minimum build volume)
- Screwdrivers
- Allen keys/Hex keys
- Wire strippers
- Multimeter

## 🔧 Assembly Instructions

### 1. 3D Printing
1. Print all parts from the `/mechanical/stl` folder
2. Recommended print settings:
   - Layer Height: 0.2mm
   - Infill: 20-30%
   - Support: As needed
   - Material: PLA or PETG

### 2. Electronics Assembly
1. Connect stepper motor drivers to Arduino
2. Wire stepper motors to drivers
3. Connect power supply (ensure proper current ratings)
4. Add limit switches if using homing functionality

### 3. Mechanical Assembly
1. Assemble the base joint (Joint 1)
2. Install shoulder joint (Joint 2)
3. Attach upper arm assembly (Joint 3)
4. Mount forearm assembly (Joint 4)
5. Install wrist joints (Joints 5 & 6)
6. Attach end effector mount

Detailed assembly instructions with images available in `/docs/assembly.md`

## 💻 Software Setup

### Prerequisites
- Arduino IDE (latest version)
- Required Libraries:
  - `AccelStepper`
  - `MultiStepper`
  - `Servo` (if using servo gripper)

### Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/Gavinkuo123456/6-DOF-Robot-Arm.git
   cd 6-DOF-Robot-Arm
   ```

2. Open the main Arduino sketch:
   ```
   /arduino/robot_arm_control/robot_arm_control.ino
   ```

3. Install required libraries through Arduino IDE Library Manager

4. Upload the code to your Arduino board

### Configuration
1. Adjust motor parameters in `config.h`
2. Calibrate joint limits and step ratios
3. Set communication baud rate (default: 115200)

## 🎮 Usage

### Basic Control
The robot arm can be controlled through:
- **Serial Commands**: Send position commands via serial monitor
- **G-code**: Basic G-code interpreter for coordinated movements
- **Python Interface**: Use provided Python scripts for advanced control

### Command Examples
```
// Move to joint positions (degrees)
J 45 30 -20 0 45 90

// Move to Cartesian position (mm)
P 200 150 100 0 90 0

// Home all joints
H

// Emergency stop
STOP
```

### Python Control Example
```python
import serial
import time

# Connect to Arduino
arm = serial.Serial('/dev/ttyUSB0', 115200)
time.sleep(2)

# Move to position
arm.write(b'J 0 45 -30 0 45 0\n')
time.sleep(3)

arm.close()
```

## 📊 Kinematics

The robot arm uses standard Denavit-Hartenberg parameters for kinematic calculations. Forward and inverse kinematics algorithms are implemented for position control.

### Joint Configuration
- **Joint 1**: Base rotation (±180°)
- **Joint 2**: Shoulder pitch (±90°)
- **Joint 3**: Elbow pitch (±135°)
- **Joint 4**: Wrist roll (±180°)
- **Joint 5**: Wrist pitch (±90°)
- **Joint 6**: Wrist yaw (±180°)

## 📁 Project Structure

```
6-DOF-Robot-Arm/
├── arduino/                 # Arduino code
│   ├── robot_arm_control/   # Main control sketch
│   ├── libraries/           # Custom libraries
│   └── examples/            # Example sketches
├── mechanical/              # 3D models and drawings
│   ├── stl/                # STL files for printing
│   ├── cad/                # Original CAD files
│   └── assembly/           # Assembly drawings
├── software/               # PC software and utilities
│   ├── python/             # Python control scripts
│   ├── matlab/             # MATLAB simulation
│   └── gui/                # Graphical interface
├── docs/                   # Documentation
│   ├── assembly.md         # Assembly instructions
│   ├── calibration.md      # Calibration guide
│   └── troubleshooting.md  # Common issues
├── images/                 # Project images
└── README.md              # This file
```

## 🔍 Troubleshooting

### Common Issues
1. **Motors not moving**: Check wiring and power supply
2. **Inaccurate positioning**: Calibrate steps per degree
3. **Communication errors**: Verify baud rate and connections
4. **Mechanical binding**: Check assembly and lubrication

See `/docs/troubleshooting.md` for detailed solutions.

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

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Gavin Kuo** - [Gavinkuo123456](https://github.com/Gavinkuo123456)

## 🙏 Acknowledgments

- Arduino community for libraries and support
- 3D printing community for design inspiration
- Robotics researchers for kinematic algorithms
- Open-source contributors

## 📞 Support

If you have questions or need help:
- Open an [Issue](https://github.com/Gavinkuo123456/6-DOF-Robot-Arm/issues)
- Check the [Documentation](./docs/)
- Join the discussion in [Discussions](https://github.com/Gavinkuo123456/6-DOF-Robot-Arm/discussions)

---

**⭐ Star this repository if you find it helpful!**

[![GitHub stars](https://img.shields.io/github/stars/Gavinkuo123456/6-DOF-Robot-Arm.svg?style=social&label=Star)](https://github.com/Gavinkuo123456/6-DOF-Robot-Arm/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/Gavinkuo123456/6-DOF-Robot-Arm.svg?style=social&label=Fork)](https://github.com/Gavinkuo123456/6-DOF-Robot-Arm/network)

Made with ❤️ for the robotics community
