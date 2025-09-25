ESP32-S3R8 Sensor & Camera Platform

This project is a compact embedded system based on the ESP32-S3R8 SoC, integrating sensing, imaging, connectivity, and power management for electronics and IoT applications. It serves as a development platform for embedded firmware, sensor interfacing, and peripheral integration.

System Overview

The board combines multiple functional blocks:

Sensors: Time-of-Flight (ToF) distance sensor connected via I²C (SDA: IO5, SCL: IO4).

Camera: OV5640 interface using a 24-pin DVP connector with I²C control for image/video acquisition.

Connectivity: USB Type-C with ESD protection (USBLC6-2) and a U.FL RF antenna connector with Pi-network matching (35+j10 Ω → 50 Ω) for wireless communication.

Power Management: Li-Po battery charging (MCP73831), MOSFET-based VBAT/VBUS path switching, TPS628438 buck converter, and MIC5504 LDOs providing 1.8V and 2.8V rails.

User Interface: LEDs and push-buttons for status indication and control.

Expansion: FPC connector (AFA01-S06FCC-00) for flexible peripheral connections.

Technical Areas

Embedded system design with ESP32-S3R8

I²C sensor interfacing and data acquisition

Camera integration via OV5640 (DVP + I²C)

Power electronics: battery charging, buck converters, LDOs, MOSFET power switching

USB connectivity with ESD protection

RF design and antenna matching

Flexible PCB/FPC design for peripheral integration

Firmware development and peripheral control

Mixed-signal electronics and board-level design

Visuals

Board Top View:
<img width="1242" height="400" alt="image" src="https://github.com/user-attachments/assets/2c513c49-7b21-4f11-a7e0-6418cb2504e2" />



Board Bottom View:
<img width="1228" height="365" alt="image" src="https://github.com/user-attachments/assets/29980292-1464-4b78-998c-93fe1beba37e" />


<img width="1256" height="494" alt="image" src="https://github.com/user-attachments/assets/9def5368-1044-42ec-89cb-fd86f3820d22" />

