---
title: Build
layout: build
---

# Building your DeepPiCar
----
## I. Bill of Materials
- For this project you will need the following materials

<iframe 
    src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQepIaRDiILXEG443XxgSJ8Zn8Qyyi7KHHboHYsno2q1ontNMV2K8tLB6Wq_hJZteyI1Sff9p2w5LmI/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false" 
    width="320" 
    height="250"    
></iframe>


## II. Construction
## III. Software Setup
## IV. Test
## Common Issues and Troubleshooting

### 1. Raspberry Pi Won't Boot
- **Check power supply:** Ensure your power adapter provides enough current (at least 2.5A for most models).
- **SD card issues:** Re-flash the SD card with a fresh image. Make sure the card is properly inserted.
- **Loose connections:** Double-check all cables and connectors.

### 2. Motors Not Responding
- **Wiring:** Verify all motor wires are connected to the correct pins on the motor driver and Raspberry Pi.
- **Power:** Ensure the battery or power source for the motors is charged and connected.
- **Code:** Test with a simple motor control script to isolate hardware vs. software issues.

### 3. Camera Not Detected
- **Connection:** Make sure the camera ribbon cable is fully inserted and oriented correctly.
- **Enable camera:** Run `sudo raspi-config` and enable the camera interface.
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
- **Calibration:** Adjust motor calibration values in your control script.
- **Mechanical:** Check for obstructions or misaligned wheels.

### 7. Unexpected Shutdowns or Freezes
- **Overheating:** Ensure the Pi has proper ventilation or a heatsink.
- **Power:** Use a reliable power supply and check for voltage drops.

### 8. No Video Stream
- **Firewall:** Ensure no firewall is blocking the streaming port.
- **Browser:** Try a different browser or clear cache.
- **Service:** Restart the streaming service or check logs for errors.

If you encounter other issues, consult the [DeepPiCar GitHub Issues page](https://github.com/your-repo/issues) or relevant forums for assistance.