---
title: Build
layout: default
nav_order: 2
---

# Building your DeepPiCar
----
## I. Bill of Materials
- For this project you will need the following materials

<div style="margin-left: 2em;">
  <table border="1" cellpadding="8" cellspacing="0">
    <thead>
      <tr>
        <th>Component</th>
        <th>Link</th>
        <th>Price (USD)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>Male to Female Jumper</strong></td>
        <td><a href="https://www.amazon.com/Elegoo-EL-CP-004-Multicolored-Breadboard-arduino/dp/B01EV70C78/">Link</a></td>
        <td>$7</td>
      </tr>
      <tr>
        <td><strong>MicroSD Card (32 GB)</strong></td>
        <td><a href="https://www.amazon.com/dp/B07R8GVGN9/">Link</a></td>
        <td>$7</td>
      </tr>
      <tr>
        <td><strong>New Bright 1:24 Scale RC Car</strong></td>
        <td><a href="https://www.walmart.com/ip/seort/5249297702">Link</a></td>
        <td>$20</td>
      </tr>
      <tr>
        <td><strong>Pololu DRV8835 Motor Driver</strong></td>
        <td><a href="https://www.pololu.com/product/2753">Link</a></td>
        <td>$15</td>
      </tr>
      <tr>
        <td><strong>Pololu Power Cable</strong></td>
        <td><a href="https://www.adafruit.com/product/4448">Link</a></td>
        <td>$2</td>
      </tr>
      <tr>
        <td><strong>Power Bank</strong></td>
        <td><a href="https://www.amazon.com/INIU-Portable-High-Speed-Flashlight-Compatible/dp/B08MZG8TN8/">Link</a></td>
        <td>$17</td>
      </tr>
      <tr>
        <td><strong>Raspberry Pi Zero 2 W</strong></td>
        <td><a href="https://www.amazon.com/Pi-Zero-WH-Quad-Core-Bluetooth/dp/B0DKKXS4RV/">Link</a></td>
        <td>$25</td>
      </tr>
      <tr>
        <td><strong>Raspberry Pi Zero Camera v1.3</strong></td>
        <td><a href="https://www.amazon.com/Arducam-Megapixels-Sensor-OV5647-Raspberry/dp/B012V1HEP4/">Link</a></td>
        <td>$7</td>
      </tr>
      <tr>
        <td><strong>USB Micro to USB</strong></td>
        <td><a href="https://www.amazon.com/Android-Compatible-Smartphones-Charging-Stations/dp/B095JZSHXQ/">Link</a></td>
        <td>$7</td>
      </tr>
      <tr>
        <td><strong>Total</strong></td>
        <td></td>
        <td><strong>$107</strong></td>
      </tr>
    </tbody>
  </table>
</div>
- Additionally, you will need to 3D print these CAD models to mount the hardware to the car.  
    - [Main hardware mount](https://github.com/Tyler-Oswald/DeepPiCarDocs/blob/main/models/Main_hardware_mount.stl)  
    - [Thread plate](https://github.com/Tyler-Oswald/DeepPiCarDocs/blob/main/models/Threaded%20plate.stl) (NOTE: This thread plate is designed for m2.5 screws. Feel free to create other plates if you wish to use different screw types.)   
    - [Camera mount](https://github.com/Tyler-Oswald/DeepPiCarDocs/blob/main/models/Camera_mount.stl)  
    - [Camera cover](https://github.com/Tyler-Oswald/DeepPiCarDocs/blob/main/models/Camera_cover.stl)  


## II. Construction
<style>
  .video-container {
    position: relative;
    left: 40px;
  }
</style>
<div style="margin-left: 40px;">
    Once you have gather all required materials, follow the build video below to assemble the car.
</div>

<div class="video-container">
    <iframe width="560" height="315" src="https://www.youtube.com/embed/ZYj04fSd8X0?si=gnulWbk-IZapVlMX" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

</div>
## III. Software Setup
> The DeepPicar repository is built and tested on the Raspberry Pi OS (Legacy) Bullseye. You can flash your Raspberry Pi Zero using the official Raspberry Pi Imager, available [here](https://www.raspberrypi.com/software/).
>
> ### Install DeepPicar Repo
>
> Clone the DeepPicar repository and install dependencies:
>
> ```bash
> git clone --recurse-submodules --depth 1 https://github.com/CSL-KU/DeepPicar-v3
> cd DeepPicar-v3 
> sudo apt update
> sudo apt install libatlas-base-dev
> sudo apt install libopenblas0
> sudo apt-get install python3-opencv
> sudo pip3 install -r requirements.txt
> ```
>
> ---
>
> ### Configure Drivers
>
> Edit the `params.py` file to select the correct **camera** and **actuator** drivers.  
> If you are using parts from the build list, you can skip this.
>
> ```python
> camera = "camera-webcam"
> actuator = "actuator-drv8835"
> ```
>
> ---
>
> ### Setup Driver for Pololu DRV8835
>
> To install the Python driver for the Pololu DRV8835 motor controller:
>
> ```bash
> cd drv8835-motor-driver-rpi
> sudo python3 setup.py install
> ```
>
> ---
>
> ### Setup Gamepad Support (Logitech F710)
>
> If you'd like to use a gamepad for data collection, set up the `inputs` Python package:
>
> ```bash
> cd inputs
> sudo pip3 install .
> ```


## IV. Test
> ### Login to your Pi
> SSH into your Pi over local WIFI  
>
> Before you start driving your car, make sure to enable legacy camera support.  
> ```
> $ sudo raspi-config
> ```
> Navigate to interface options, select legacy camera, and click on yes.
> 
> ### Start the control script
> 
> ```
> $ cd DeepPicar-v3
> $ sudo nice --20 python3 deeppicar.py -n 4 -f 30
> ```
> 
> Keyboard controls:  
> **A**: move forward   
> **Z**: move backward  
> **S**: stop  
> **J**: turn left  
> **K**: center  
> **L**: turn right   
> **R**: start/stop recording  
> **D**: turn on DNN  
> 
> Use the keys to manually control the car. Once you become confident in controlling the car, collect the data to be used for training the DNN model. 
> 
> The data collection can be enabled and stopped by pressing `R`. Once recording is enabled, the video feed and the corresponding control inputs are stored in `out-video.avi` and `out-key.csv` files, respectively. Later, we will use these files for training. It can be downloaded using scp commands.
> 
> Each recording attempt will overwrite the previous.
> 
> Compress all the recorded files into a single zip file, say Dataset.zip for Colab.
> 
> ```
> $ zip Dataset.zip out-*
> ```
> 
> ## Train the model
>     
> Open the colab notebook. Following the notebook, you will upload the dataset to the colab, train the model, and download the model back to your PC. 
> 
> [Open In Colab](https://colab.research.google.com/drive/1sC2sLeO5HAbc5oXotxMGp0SUncoDP4AF?usp=sharing)
> 
> After you are done training, you need to copy the trained tflite model file (`large-200x66x3.tflite` by default) to the Pi using scp commands.
> 
> ## Autonomous control
> 
> Copy the trained model to the DeepPicar. 
> 
> ```
> $ cd DeepPicar-v3
> $ sudo nice --20 python3 deeppicar.py -n 4 -f 30
> ```
> 
> Enable autonomous driving by pressing **A** to go forward then **D** to start the DNN.
