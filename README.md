STM32F401-MPU6050-Driver-Benchmark
HAL vs. LL vs. Bare-Metal I2C Driver for MPU6050 on STM32F401

![alt text](https://img.shields.io/badge/STM32F401-Cortex--M4-blue "STM32F401 Cortex-M4")
![alt text](https://img.shields.io/badge/MPU6050-I2C%252FSPI-green "MPU6050 I2C%2FSPI")
![alt text](https://img.shields.io/badge/License-MIT-orange "License MIT")

A hands-on comparison of three embedded driver implementations for the MPU6050 accelerometer/gyroscope on STM32F401:
HAL (STM32Cube HAL)
LL (Low-Layer Drivers)
Bare-Metal (Register-Level)
Ideal for embedded engineers learning STM32 or preparing for technical interviews!

Key Features:
Three driver implementations for the same sensor (MPU6050)
Performance benchmarks (clock cycles, memory usage)
UART debug output for real-time data visualization
Full datasheet analysis (register mapping, I2C protocol)
Extensible structure (supports other I2C/SPI sensors)

Hardware Setup:
MCU: STM32F401RE (Nucleo-F401RE board)
Sensor: MPU6050 (3-axis accelerometer + gyroscope)
Connections:
MPU6050	STM32F401
VCC	3.3V
GND	GND
SDA	PB7
SCL	PB6
Note: Pull-up resistors (4.7kΩ) are required for I2C.

Repository Structure:
bash
STM32F401-MPU6050-Driver-Benchmark/
├── HAL_Driver/           # STM32Cube HAL implementation
│   ├── Inc/              # Header files
│   ├── Src/              # Source files
│   └── STM32CubeIDE/     # IDE project files
├── LL_Driver/            # Low-Layer driver implementation
├── Bare_Metal/           # Register-level implementation
├── Docs/                 # Datasheets, schematics, notes
├── Images/               # Setup photos, oscilloscope captures
└── README.md

Quick Start

1. Clone the repository

bash
git clone https://github.com/yourusername/MPU6050_DriverBenchmark.git

2. Open in STM32CubeIDE

Import the project folders (HAL_Driver/STM32CubeIDE, LL_Driver, etc.).
Build and flash to your Nucleo-F401RE board.

3. Monitor data via UART

plaintext
[HAL] Accel: X=120, Y=-340, Z=980  
[LL]  Accel: X=123, Y=-338, Z=978  
[BM]  Accel: X=125, Y=-335, Z=975  
(Baud rate: 115200, 8N1)

Performance Benchmarks:
Method	Execution Time (cycles)	Flash Usage	RAM Usage
HAL	~1500	12KB	2KB
LL	~900	8KB	1KB
Bare-Metal	~400	5KB	0.5KB
Measured using DWT_CYCCNT on STM32F401 @84MHz.

Technical Documentation:
MPU6050 Datasheet: Download
STM32F401 Reference Manual: Download
I2C Register Map: See Docs/I2C_Register_Map.md

Roadmap & Contributions:
Add interrupt-driven I2C support
Implement Kalman filter for noise reduction
Benchmark power consumption
Contributions welcome! Open an issue or submit a PR.

License MIT © [CarreseD]