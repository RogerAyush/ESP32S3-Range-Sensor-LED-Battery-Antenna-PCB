**ESP32-S3 Vision Board with Camera and ToF Sensor**

This is a custom PCB design for an all-in-one ESP32-S3 development board focused on vision and sensing projects. It integrates the ESP32-S3 microcontroller with an OV5640 camera module, a VL53L0X Time-of-Flight (ToF) sensor connector, wireless capabilities, and portable power management—all on a compact 4-layer board. No more juggling separate breakouts and jumper wires; everything's wired up cleanly for quick prototyping, like building AI cameras, gesture-controlled devices, or battery-powered drones.
The design is based on the ESP32-S3R8 SoC, which brings dual-core processing (up to 240MHz), Wi-Fi 4, Bluetooth 5 (including LE), and hardware acceleration for AI tasks. It's perfect for edge computing with the camera's 5MP resolution (up to 1080p@30fps video) and the ToF sensor's precise distance ranging (up to 2m).


**Key Features**

Camera Support: 24-pin FPC for OV5640; DVP (Y2-Y9, HREF, VSYNC, PCLK) + I²C (IO39/IO40); 2.8V LDO (MIC5504) + enable (IO33).
ToF Sensor: 6-pin FPC (J3) for VL53L0X; I²C (IO4/IO5) with 4.7kΩ pull-ups + drain/power.
Wireless: PCB antenna + LNA (35+j10Ω); U.FL (J2) for external; 40MHz crystal.
Power System: USB-C (5V/program); LiPo charger (MCP73831, ~417mA, LED); P-MOSFET switching; buck to 3.3V (U1); LDOs for 1.8V/2.8V; Schottky (D3) protection.
Storage: 8MB QSPI Flash (GD25Q64) for firmware/data.
User Interface: 4 switches (SW1-SW4: EN, BOOT, IO8/IO9 buttons); green LEDs (D2/D5 on IO45/IO46).
Debug: USB to U0TXD/RXD; JTAG exposed.
Size & Build: ~50x40mm 4-layer FR4 (1.6mm, 1oz Cu); ENIG finish; full decoupling (100nF + ceramics).


**Quick Setup Scene**

Plug in USB-C, hit the BOOT switch to flash via ESP-IDF or Arduino. The camera captures a frame—steam rising from your mug streams live over Wi-Fi to your phone. Tap the ToF connector, and it pings the distance to your hand, triggering a gesture command. With the LiPo slotted in, unplug and watch it run untethered for hours. Simple, solid, and ready to hack.


**Design Notes**

Power Flow: USB or battery feeds VIN (~4.6V after diode). Buck to 3.3V for ESP32; LDOs for camera (2.8V) and other analog. Camera power gated via P-FET (U2) controlled by IO33—high to enable, low to shut off for sleep modes.
Signal Integrity: Camera DVP traces length-matched, ~90Ω impedance. SPI to Flash kept short (<50Ω). RF section isolated with ground pours.
Protections: TVS diode (D1) on USB, ferrite beads (FB1, L4) for noise filtering. Pull-ups/downs on key pins (e.g., 10kΩ on EN/BOOT).
Current Draw: Idle ~50mA; full camera + Wi-Fi ~250mA. LiPo supports 3.7V cells up to 1000mAh.
Tools Used: Designed in Altium (schematic dated 10-01-2025). SPICE sims confirmed charger (ICHG = 1000/2.4k ≈ 417mA) and switching logic.


**Repo Contents**

Schematics: Full Altium project (Sheet.SchDoc) and exported PDF (Print.pdf) with all sheets (power, camera/ToF, USB, etc.).
BOM: CSV with part numbers, values, and footprints (e.g., ESP32-S3R8, MIC5504-2.8YM5 for camera LDO).
Gerbers & Files: PCB layout, drill files, and Pick & Place for fab.
3D Renders: STEP models and layer views (top/bottom/inners) for inspection.
Firmware Snippets: Basic ESP-IDF examples for camera init, ToF polling, and Wi-Fi streaming.
