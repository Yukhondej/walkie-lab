# IMU Orientation Tracker (Madgwick Filter)

This project implements a high-precision orientation tracker for 3D objects (like the sword shown in this repository) using the **Adafruit FXOS8700 / FXAS21002C** sensor fusion set. It utilizes a custom **Madgwick Filter** optimized with `double` precision and an adaptive gain to handle linear acceleration noise.

## 🛠️ Prerequisites

1.  **Visual Studio Code**: [Download here](https://code.visualstudio.com/).
2.  **PlatformIO IDE Extension**: Install this from the VS Code Extensions marketplace.
3.  **Hardware**: FXOS8700 Accelerometer/Magnetometer and FXAS21002C Gyroscope.

---

## 🚀 Setup Instructions

### 1. Create the Project
* Open **PlatformIO Home** in VS Code.
* Click **+ New Project**.
* **Board**: Select your board (e.g., `Espressif ESP32 Dev Module` or `Arduino Uno`).
* **Framework**: `Arduino`.

### 2. Configure Libraries
Open your `platformio.ini` file in the project root and replace its contents with the configuration below. This ensures all dependencies are automatically downloaded.

```ini
[env:your_board_name]
platform = espressif32 ; Change to 'atmelavr' for Arduino Uno
board = esp32dev       ; Change to your specific board ID
framework = arduino
monitor_speed = 115200

lib_deps =
    adafruit/Adafruit FXAS21002C @ ^2.1.2
    adafruit/Adafruit FXOS8700 @ ^1.4.1
    adafruit/Adafruit Unified Sensor @ ^1.1.14
