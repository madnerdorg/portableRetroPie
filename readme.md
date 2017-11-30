Work In Progress
----------------

# Buy
(Shipping included)
Prices for france.

* TFT LCD pi hat v0.2a : 10.74€ (aliexpress)
* Raspberry Pi Zero:  11.17€ (pi hut)
* Stripboard * 10 : 1.64€ (aliexpress)
* Buttons : 3.23€ (aliexpress)
* Sandisk Ultra 16go : 9,38€ (amazon)
---------------------------------------------
36.16€

* Adafruit PowerBoost 1000c charger : 25.19€ (amazon)
* Lithium Battery 2000-2500mah : 19.80€ (semageek)
-----------------------------------------------
44.99€
Total: 81.15€

# Install Retropie
https://learn.adafruit.com/pigrrl-zero/software
https://adafruit-download.s3.amazonaws.com/PiGRRL_Zero_20160912.zip
# 3D print case

# Wiring PowerBoost 1000c
https://learn.adafruit.com/pigrrl-zero/software?view=all#power
# Wiring buttons

| IN/OUT | POSITION | TOP/BOTTOM | COLOR  | GPIO | NAME             |
|--------|----------|------------|--------|------|------------------|
| IN     | 1        | BOT        | BLACK  | GND  | GROUND (Pad)     |
| OUT    | 4        | BOT        | BLACK  | GND  | GROUND (Buttons) |
| IN     | 4        | TOP        | BLUE   | 4    | LEFT             |
| IN     | 4        | BOT        | PURPLE | 13   | RIGHT            |
| OUT    | 3        | BOT        | ORANGE | 16   | UP               |
| IN     | 2        | BOT        | BROWN  | 26   | DOWN             |
| IN     | 5        | BOT        | RED    | 6    | A                |
| IN     | 7        | TOP        | YELLOW | 27   | B                |
| OUT    | 2        | BOT        | BLUE   | 20   | Y                |
| IN     | 6        | TOP        | GREEN  | 17   | X                |
| OUT    | 5        | BOT        | ORANGE | 12   | LEFT TRIGGER     |
| IN     | 4        | BOT        | RED    | 13   | RIGHT TRIGGER    |
```
# Sample configuration file for retrogame.
# Really minimal syntax, typically two elements per line w/space delimiter:
# 1) a key name (from keyTable.h; shortened from /usr/include/linux/input.h).
# 2) a GPIO pin number; when grounded, will simulate corresponding keypress.
# Uses Broadcom pin numbers for GPIO.
# If first element is GND, the corresponding pin (or pins, multiple can be
# given) is a LOW-level output; an extra ground pin for connecting buttons.
# A '#' character indicates a comment to end-of-line.
# File can be edited "live," no need to restart retrogame!

# Here's a pin configuration for the PiGRRL Zero project:

LEFT       4  # Joypad left
RIGHT     13  # Joypad right
DOWN      26  # Joypad down
UP        16  # Joypad up
Z          6  # 'A' button
X         27  # 'B' button
A         20  # 'X' button
S         17  # 'Y' button
Q         12  # Left shoulder button
W         13  # Right shoulder button
ESC       22  # Exit ROM; PiTFT Button 1
LEFTCTRL   5  # 'Select' button; PiTFT Button 2
ENTER     24  # 'Start' button; PiTFT Button 3
4         23  # PiTFT Button 4 (PowerOff)

# For configurations with few buttons (e.g. Cupcade), a key can be followed
# by multiple pin numbers.  When those pins are all held for a few seconds,
# this will generate the corresponding keypress (e.g. ESC to exit ROM).
# Only ONE such combo is supported within the file though; later entries

# Add poweroff button script
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
```


# Settings Retropie
## Settings gpio buttons
https://learn.adafruit.com/retro-gaming-with-raspberry-pi/adding-controls-software

```
cd
curl -O https://raw.githubusercontent.com/adafruit/Raspberry-Pi-Installer-Scripts/master/retrogame.sh
sudo bash retrogame.sh
```

Select 1

Modify /boot/retrogame.cfg
```
```

# Add gyro/compass
## Install I2C
http://kingtidesailing.blogspot.fr/2016/02/how-to-setup-mpu-9250-on-raspberry-pi_25.html



## Calibrate MPU 9250

## Using it
```
apt-get install  python-rtimulib
```

# Install libreconnect
