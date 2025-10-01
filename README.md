# 🚀 **ESP32-S3 Vision Board with Camera and ToF Sensor**

A custom all-in-one development board for vision and sensing applications.  
This compact **4-layer PCB** integrates the **ESP32-S3** microcontroller, **OV5640** camera module, **VL53L0X Time-of-Flight (ToF)** sensor connector, wireless connectivity, and portable power management. It eliminates the need for separate breakouts and jumper wires, enabling clean setups for prototyping **AI cameras**, gesture-controlled devices, or battery-powered drones.

The design is based on the **ESP32-S3R8 SoC**, featuring dual-core processing up to **240 MHz**, **Wi-Fi 4**, **Bluetooth 5** (including LE), and hardware acceleration for **AI tasks**. It supports edge computing with the camera's **5 MP resolution** (up to **1080p at 30 fps**) and the ToF sensor's precise distance ranging up to **2 m**.

## 🌟 **Key Features**
- **Camera Support**: **24-pin FPC** for OV5640; DVP data (Y2-Y9, HREF, VSYNC, PCLK) + I²C (IO39/IO40); **2.8V LDO** (MIC5504) + enable pin (IO33) for power management.
- **ToF Sensor**: **6-pin FPC** (J3) for VL53L0X; I²C (IO4/IO5) with **4.7 kΩ pull-ups** + drain/power connections.
- **Wireless**: PCB antenna + LNA matching (**35 + j10 Ω**); U.FL (J2) for external antenna; **40 MHz crystal** for stable clocking.
- **Power System**: **USB-C** (5V input/programming); LiPo charger (**MCP73831**, ~**417 mA**, status LED); P-MOSFET switching; buck converter to **3.3V** (U1); LDOs for **1.8V/2.8V**; Schottky diode (**D3**) protection.
- **Storage**: **8 MB QSPI Flash** (**GD25Q64**) for firmware and data logging.
- **User Interface**: 4 switches (**SW1-SW4**: EN reset, BOOT mode, IO8/IO9 buttons); green LEDs (**D2/D5** on IO45/IO46) for status indication.
- **Debug**: USB routed to **U0TXD/RXD** for serial output; **JTAG** pins exposed.
- **Size & Build**: ~**50 x 40 mm** 4-layer FR4 (**1.6 mm thick**, **1 oz Cu**); **ENIG finish**; full decoupling (**100 nF + ceramics**) near power pins.

## ☕ **Quick Setup Overview**
Connect via **USB-C** and press the **BOOT** switch to program using **ESP-IDF** or **Arduino IDE**. The camera captures frames, streaming video over **Wi-Fi** to a connected device. Attach the ToF sensor to measure distances and trigger actions, such as gestures. Insert a **LiPo battery** for untethered operation lasting several hours. This streamlined process supports rapid iteration and reliable performance.

## ⚡ **Design Notes**
- **Power Flow**: USB or battery input to **VIN** (~**4.6 V** after diode), stepped down to **3.3 V** via buck converter for the ESP32; LDOs provide **2.8 V** for the camera and other analog rails. Camera power is gated by **P-FET (U2)** on IO33—high to enable, low for sleep modes.
- **Signal Integrity**: DVP traces length-matched with ~**90 Ω differential impedance**; SPI to Flash kept short (<**50 Ω**); RF section isolated using ground pours.
- **Protections**: **TVS diode (D1)** on USB lines, ferrite beads (**FB1, L4**) for EMI filtering; pull-ups/downs on critical pins (e.g., **10 kΩ** on EN/BOOT).
- **Current Draw**: Idle ~**50 mA**; full camera + Wi-Fi operation ~**250 mA**. Compatible with **3.7 V LiPo cells** up to **1000 mAh**.
- **Tools Used**: Designed in **Altium Designer** (schematic dated **10-01-2025**). SPICE simulations verified charger current (**ICHG = 1000/2.4 k ≈ 417 mA**) and switching behavior.

## 📁 **Repo Contents**
- **Schematics**: Full Altium project (**Sheet.SchDoc**) and exported PDF (**Print.pdf**) covering all sheets (power, camera/ToF, USB, etc.).
- **BOM**: CSV with part numbers, values, and footprints (e.g., **ESP32-S3R8**, **MIC5504-2.8YM5** for camera LDO).
- **Gerbers & Files**: PCB layout, drill files, and Pick & Place data for fabrication.
- **3D Renders**: STEP models and layer views (top/bottom/inners) for detailed inspection.
- **Firmware Snippets**: Basic **ESP-IDF** examples for camera initialization, ToF polling, and Wi-Fi streaming.

![ESP32 with CAM and ToF - Full Schematic](Print.pdf)  
*(Comprehensive schematic from Altium, including battery charger, voltage regulators, power switching, camera/ToF connectors, and supporting circuits.)*

For layer details, refer to the PDF: top layer features **ESP32** and connectors; inner layers handle power and ground planes; bottom layer includes **RF** and passives.

## 📅 **Status & Next Steps**
Design is complete and Gerber-ready as of **October 1, 2025**. Prototypes are in production—expect assembly and validation tests (camera focus, ToF accuracy, battery runtime) by month-end. Version 2 will include the **ToF flex PCB** and potential **IMU expansion**.

Download the files, fabricate a board, and explore applications like drone vision or smart mirrors. Contributions via issues or pull requests are welcome. For questions, reach out.
