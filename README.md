# Smart LPG Gas Leak Detector

This project is a smart LPG gas leak detector that uses an MQ-2 gas sensor to detect the presence of gases, such as LPG. It utilizes an ESP8266 microcontroller to send real-time sensor data to the Blynk app and provides feedback through LEDs and a buzzer.

## Features

- **Gas Leak Detection:** Detects LPG gas leakage using the MQ-2 sensor.
- **Real-time Data on Blynk App:** Sends sensor data to the Blynk app for real-time monitoring.
- **Visual and Audible Alerts:**
  - Green LED for normal operation.
  - Red LED for gas detection.
  - Buzzer that sounds when gas is detected.
- **LCD Display:** Displays the LPG gas percentage and status messages.

## Hardware Components

- **ESP8266 Wi-Fi Module** (NodeMCU, Wemos D1 mini, etc.)
- **MQ-2 Gas Sensor** (for gas detection)
- **16x2 LCD Display** with I2C interface
- **LEDs:** Green, Red, and Wi-Fi status LED
- **Buzzer**
- **Push button** (Optional: Used for additional control)
  
## Circuit Diagram

- **MQ-2 Sensor:** Connected to analog pin A0.
- **LEDs:**
  - Green LED connected to D5.
  - Red LED connected to D7.
  - Wi-Fi status LED connected to D0.
- **Buzzer:** Connected to D3.
- **Push Button (Optional):** Connected to virtual pin V1 for interaction via the Blynk app.

## Software Requirements

- **Arduino IDE** (with ESP8266 board package installed)
- **Blynk App** (installed on your smartphone)

## Libraries Required

- **Blynk Library:** For interaction with the Blynk platform.
- **LiquidCrystal_I2C:** For controlling the 16x2 LCD display over I2C.
- **ESP8266WiFi:** For connecting the ESP8266 to the Wi-Fi network.
- **BlynkSimpleEsp8266:** For the ESP8266-specific Blynk functionality.

### Install Libraries

1. Go to **Sketch > Include Library > Manage Libraries** in Arduino IDE.
2. Search and install the following libraries:
   - **Blynk**
   - **LiquidCrystal_I2C**

## Setup

1. Open Arduino IDE and select the correct **Board** and **Port** for your ESP8266.
2. Set up your **Wi-Fi SSID** and **Password** in the code (replace `123` and `12345678` with your Wi-Fi credentials).
3. Replace the **Blynk Template ID** and **Auth Token** with the credentials from your Blynk app.
4. Upload the code to your ESP8266.

## Code Explanation

### Key Components:

- **Wi-Fi Connection:** The ESP8266 connects to your Wi-Fi using the credentials provided in the code.
- **Blynk App Communication:** The app receives sensor data and displays it in real-time. It also sends notifications if gas is detected.
- **Sensor Data Collection:** The MQ-2 sensor reads analog data and maps it to a percentage value.
- **LED and Buzzer Feedback:** When gas leakage is detected, the red LED turns on, and the buzzer beeps to alert the user.
- **LCD Display:** Displays the current LPG gas percentage and status (Gas Detected or Normal).

### Functions:

- **getSensorData():** Reads the MQ-2 sensor and updates the LCD and LED status based on the sensor value.
- **sendSensorData():** Sends the sensor value to the Blynk app.
- **checkBlynkStatus():** Periodically checks the connection to the Blynk server and sends data if connected.

## Blynk App Setup

1. Create a new project in the Blynk app.
2. Select **ESP8266** as the device and the correct connection type.
3. Copy the **Auth Token** generated by Blynk and paste it into the code.
4. Add a **Value Display** widget to show the gas sensor data from virtual pin V1.

## Running the Project

1. After uploading the code to the ESP8266, open the Blynk app and check if the sensor data is displayed.
2. If the gas concentration exceeds the threshold, the system will trigger the red LED, and the buzzer will sound, indicating a gas leak.
3. The system will automatically update the gas concentration value on the Blynk app.

## Troubleshooting

- Ensure your Wi-Fi credentials are correct.
- Check that the **Auth Token** is correctly placed in the code.
- Make sure the Blynk app is correctly configured to display sensor data from the correct virtual pin.

## License

This project is open-source and can be modified for personal or educational use.
