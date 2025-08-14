# MPU6050 Driver Benchmark

#### STM32F401 driver for MPU6050 accelerometer/gyroscope, implemented three ways: HAL (high-level), LL (low-layer), and bare-metal (register-level). Compares performance, memory usage, and efficiency. Includes UART debug, full docs, and extensible structure for other I2C/SPI sensors.

## HAL vs. LL vs. Bare-Metal I2C Driver for MPU6050 on STM32F401

![alt text](https://img.shields.io/badge/STM32F401-Cortex--M4-blue "STM32F401 Cortex-M4")
![alt text](https://img.shields.io/badge/MPU6050-I2C%252FSPI-green "MPU6050 I2C%2FSPI")
![alt text](https://img.shields.io/badge/License-MIT-orange "License MIT")


#### A hands-on comparison of three embedded driver implementations for the MPU6050 accelerometer/gyroscope on STM32F401:
* _HAL_ (STM32Cube HAL)

* _LL_ (Low-Layer Drivers)

* _Bare-Metal_ (Register-Level)
  
<br />

#### Key Features:
* Three driver implementations for the same sensor (MPU6050).  

* Performance benchmarks (clock cycles, memory usage).

* UART debug output for real-time data visualization.

* Full datasheet analysis (register mapping, I2C protocol).

* Extensible structure (supports other I2C/SPI sensors).

<br />

#### Hardware Setup:
MCU: STM32F401RE (Nucleo-F401RE board)<br />
Sensor: MPU6050 (3-axis accelerometer + gyroscope)<br />

**Connections:**<br />
MPU6050<br />
STM32F401<br />
VCC	3.3V<br />
GND	GND\ 
SDA	PB7<br />
SCL	PB6<br />
Note: Pull-up resistors (4.7kΩ) are required for I2C.<br /><br />

#### Repository Structure:
bash<br />
STM32F401-MPU6050-Driver-Benchmark/<br />
├── HAL_Driver/           # STM32Cube HAL implementation<br />
│   ├── Inc/              # Header files<br />
│   ├── Src/              # Source files<br />
│   └── STM32CubeIDE/     # IDE project files<br />
├── LL_Driver/            # Low-Layer driver implementation<br />
├── Bare_Metal/           # Register-level implementation<br />
├── Docs/                 # Datasheets, schematics, notes<br />
├── Images/               # Setup photos, oscilloscope captures<br />
└── README.md<br /><br />

#### Quick Start
1. Clone the repository
   * git clone ```https://github.com/carresed/MPU6050_DriverBenchmark.git```
2. Open in STM32CubeIDE
   * Import the project folders (HAL_Driver/STM32CubeIDE, LL_Driver, etc.). <br />Build and flash to your Nucleo-F401RE board.

3. Monitor data via UART
   * [HAL] Accel: X=120, Y=-340, Z=980  
   * [LL]  Accel: X=123, Y=-338, Z=978  
   * [BM]  Accel: X=125, Y=-335, Z=975  
* (Baud rate: 115200, 8N1)
<br /><br />
#### Performance Benchmarks:\
* Method	Execution Time (cycles)	Flash Usage	RAM Usage\
* HAL	~1500	12KB	2KB\
* LL	~900	8KB	1KB\
* Bare-Metal	~400	5KB	0.5KB\
* Measured using DWT_CYCCNT on STM32F401 @84MHz.<br /><br />

#### Technical Documentation:
MPU6050 Datasheet: [Download](https://invensense.tdk.com/wp-content/uploads/2015/02/MPU-6000-Datasheet1.pdf) <br />
STM32F401 Reference Manual: [Download](https://www.st.com/resource/en/datasheet/stm32f401cc.pdf) <br /><br />

#### Roadmap & Contributions:
Add interrupt-driven I2C support <br />
Implement Kalman filter for noise reduction <br />
Benchmark power consumption <br />
Contributions welcome! Open an issue or submit a PR. <br />

License MIT © [CarreseD](https://github.com/carresed)