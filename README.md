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

(author has this display sitting around, power from a separate 5V source, Pi 4 is not able to power both Oak-D and display)</br>

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

Depthai-python has excellent examples to learn from:</br>

https://github.com/luxonis/depthai-python

Download zip file with "Code" button to Pi and go into examples directory. Try MonoCamera, ColorCamera, FeatureTracker, SpatialDetection, and StereoDepth.</br>

# Experiment 1</br>

Luxonis' webpage "Stereo neural inference" is a starting point for this experiment.<br>

https://docs.luxonis.com/en/latest/pages/spatial-ai/#stereo-neural-inference

<img src="images/stereoscope.jpg" width="300">

<img src="images/stereoscope2.gif" width="480">

The GIF video is a recording of the stereo mono cameras from Oak-D (separated by baseline of 7.5cm).</br>

Experiment 1 is based on main.py from https://github.com/luxonis/depthai-experiments/tree/master/gen2-triangulation.</br>

Change line ~294</br>

<pre>
        cv2.imshow("Combined frame", np.concatenate((left, combined ,right), axis=1))
</pre>

to</br>

<pre>
        # for 800x480 hdmi display
        cv2.namedWindow("Stereoscope AR", cv2.WND_PROP_FULLSCREEN)
        cv2.setWindowProperty("Stereoscope AR",cv2.WND_PROP_FULLSCREEN,cv2.WINDOW_FULLSCREEN)
        imOut = np.hstack((right, left)) # switch left right for stereoscope AR
        resize = cv2.resize(imOut, (800,480), interpolation = cv2.INTER_LINEAR)
        cv2.imshow("Stereoscope AR", resize)
</pre>

Comment out lines ~258 with "combined"</br>

<pre>
        #cv2.circle(combined, coords2, 3, leftColor)
        #cv2.circle(combined, coords1, 3, rightColor)

        # Visualize disparity line frame
        #cv2.line(combined, coords1, coords2, (0,0,255), 1)
</pre>

Line ~281</br>

<pre>
        textHelper.putText(combined, s, (10, y))
</pre>

to</br>

<pre>
        textHelper.putText(left, s, (10, y))
        textHelper.putText(right, s, (10, y))
</pre>

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

</br>Copyright (c) 2022 Hartwell Fong</br>
