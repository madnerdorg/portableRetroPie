# Install Retropie
* https://learn.adafruit.com/pigrrl-zero/software
* https://adafruit-download.s3.amazonaws.com/PiGRRL_Zero_20160912.zip

## Setup retropie

## Add poweroff button script
````
#!/usr/bin/python
import RPi.GPIO as GPIO
import time
import subprocess

GPIO.setmode(GPIO.BCM)

# we will use the pin numbering to match the pins on the Pi, instead of the
# GPIO pin outs (makes it easier to keep track of things)
# use the same pin that is used for the reset button (one button to rule them all!)
GPIO.setup(23, GPIO.IN, pull_up_down=GPIO.PUD_UP)

oldButtonState1 = True

while True:
    #grab the current button state
    buttonState1 = GPIO.input(23)

    # check to see if button has been pushed
    if buttonState1 != oldButtonState1 and buttonState1 == False:
        # shutdown
        subprocess.call("shutdown -h now", shell=True,
          stdout=subprocess.PIPE, stderr=subprocess.PIPE)
        oldButtonState1 = buttonState1

    time.sleep(.5)
````

## Retrogame (gpio buttons)
https://learn.adafruit.com/retro-gaming-with-raspberry-pi/adding-controls-software

```
cd
curl -O https://raw.githubusercontent.com/adafruit/Raspberry-Pi-Installer-Scripts/master/retrogame.sh
sudo bash retrogame.sh
```

Select 1

Modify /boot/retrogame.cfg
````
LEFT      13  # Joypad left
RIGHT      4  # Joypad right
DOWN      26  # Joypad down
UP        16  # Joypad up
Z         20  # 'A' button
X         27  # 'B' button
A         17  # 'X' button
S          6  # 'Y' button
Q          1  # Left shoulder button
W         12  # Right shoulder button
ESC       22  # Exit ROM; PiTFT Button 1
LEFTCTRL   5  # 'Select' button; PiTFT Button 2
ENTER     24  # 'Start' button; PiTFT Button 3
````
