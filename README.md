# Raspberry-Pi-Stereoscope-AR
Exploring Luxonis' Oak-D on a Raspberry Pi with a stereoscope.</br>
 
# Hardware
Raspberry Pi 4 Model B (tested 4GB version)</br>
Raspberry Pi 3 Model B+ (tested 1GB version)</br>
Pi Zero W (worked but lower performance, should test on Pi Zero 2 W)</br>

Luxonis' Oak-D</br>

(Oak-D was available early December 2021 to start learning. Oak-D-Lite is expected to ship April 2022 at a lower cost and a smaller size.)</br>

OWL Stereoscopic Viewer from The London Stereoscopic Company Ltd</br>

Adafruit HDMI 5" 800x480 Display Backpack (resistive touchscreen not used)</br>

(author has this display sitting around, powered from a separate 5V power supply, Pi 4 is not able to power both Oak-D and display)</br>

# Software
Raspberry Pi OS with desktop</br>
Release date: October 30th 2021</br>
Kernel version: 5.10</br>
Size: 1,148MB</br>

# Installation

https://docs.luxonis.com/projects/api/en/latest/install/?highlight=raspberry%20pi#raspberry-pi-os

<pre>
sudo curl -fL https://docs.luxonis.com/install_dependencies.sh | bash
</pre>

# Experiment 1</br>

# References</br>

https://www.luxonis.com/

https://www.raspberrypi.com/

https://www.londonstereo.com/

https://docs.luxonis.com/en/latest/

https://docs.luxonis.com/projects/api/en/latest/install/?highlight=raspberry%20pi#raspberry-pi-os

https://github.com/luxonis/depthai-python

https://github.com/luxonis/depthai-experiments

Adafruit still make this display since 2014.</br>

https://www.adafruit.com/product/2260

Pi 4 auto setup hdmi without manually changing /boot/config.txt. Not sure if it's the hardware or software detecting display connected to it. So, no need to follow instruction below.</br>

https://learn.adafruit.com/adafruit-5-800x480-tft-hdmi-monitor-touchscreen-backpack/raspberry-pi-config
