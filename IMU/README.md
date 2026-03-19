🛠️ Prerequisites
Visual Studio Code: Download and install VS Code.

PlatformIO IDE: Inside VS Code, go to the Extensions view (square icon on the left), search for "PlatformIO IDE," and install it.

🚀 Setup Instructions
1. Create a New Project
Open the PlatformIO Home (house icon in the bottom toolbar).

Click + New Project.

Name: IMU_Sword_Tracker

Board: Select your specific board (e.g., Espressif ESP32 Dev Module or Arduino Uno).

Framework: Arduino.

2. Install Required Libraries
PlatformIO manages libraries automatically via the platformio.ini file. Open the platformio.ini file in your project root and replace its content with the following (adjust the board if necessary):

Ini, TOML
[env:your_board_here]
platform = espressif32 ; or atmelavr for Arduino Uno
board = esp32dev       ; change to your specific board
framework = arduino
monitor_speed = 115200

lib_deps =
    adafruit/Adafruit FXAS21002C @ ^2.1.2
    adafruit/Adafruit FXOS8700 @ ^1.4.1
    adafruit/Adafruit Unified Sensor @ ^1.1.14
3. Add the Source Code
Navigate to the src/ folder in your project directory.

Open the existing main.cpp (or create it).

Delete any default code and paste the entire content of the provided src/main.cpp.

⚖️ Calibration & Gravity
The code includes a "Thailand Default" gravity magnitude of 9.82588196.

If you are in a different part of the world, you may want to uncomment the calibrateSensors() function in setup() for the first run to get values specific to your local gravity and sensor bias.

The calibration results will print to the Serial Monitor; you can then hardcode those values into the default vals section of the code for faster startups.

📈 Running the Project
Connect your hardware via USB.

Build: Click the Checkmark icon in the bottom status bar.

Upload: Click the Right Arrow icon to flash the code to your board.

Monitor: Click the Plug icon to open the Serial Monitor.

You should see three comma-separated values (Roll, Pitch, Yaw) streaming at 115200 baud. These are ready to be piped into a visualizer like MATLAB or a custom Python script!

Note on Yaw Accuracy: This code uses a 6-DOF (Degrees of Freedom) Madgwick filter. While it is highly stable for Roll and Pitch, Yaw may drift slightly over time as it lacks a magnetometer heading correction in the current update() implementation.

Would you like me to show you how to write a simple Python script to visualize this sword's movement in real-time?
