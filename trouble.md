---
title: Troubleshooting
layout: default
nav_order: 4
---

## Common Issues and Troubleshooting

### 1. Raspberry Pi Won't Boot
- **Check power supply:** Ensure your power adapter provides enough current (at least 2.5A for most models).
- **SD card issues:** Re-flash the SD card with a fresh image. Make sure the card is properly inserted.
- **Loose connections:** Double-check all cables and connectors.

### 2. Motors Not Responding
- **Wiring:** Verify all motor wires are connected to the correct pins on the motor driver and Raspberry Pi.
- **Power:** Ensure the battery or power source for the motors is charged and connected.

### 3. Camera Not Detected
- **Connection:** Make sure the camera ribbon cable is fully inserted and oriented correctly.
- **Legacy support:** Confirm that legacy camera support is enabled on the RPI
- **Test:** Use `raspistill -o test.jpg` to check if the camera works.

### 4. Wi-Fi/Network Issues
- **Credentials:** Double-check your Wi-Fi SSID and password in the configuration.
- **Signal:** Move closer to the router or use a Wi-Fi dongle with better reception.
- **IP Address:** Use `ifconfig` or `hostname -I` to find the Pi’s IP address.

### 5. Software Installation Errors
- **Dependencies:** Run `sudo apt update && sudo apt upgrade` before installing packages.
- **Python packages:** Use `pip3 install --user <package>` to avoid permission issues.
- **Permissions:** Use `sudo` only when necessary.

### 6. Car Not Driving Straight
- **Calibration:** Use the bais adjustment system on the bottom of the car

If you encounter other issues, consult the [DeepPiCar GitHub Issues page](https://github.com/your-repo/issues) or relevant forums for assistance.