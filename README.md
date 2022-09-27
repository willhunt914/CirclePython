# CircuitPython
This repository will actually serve as a aid to help you get started with your own template.  You should copy the raw form of this readme into your own, and use this template to write your own.  If you want to draw inspiration from other classmates, feel free to check [this directory of all students!](https://github.com/chssigma/Class_Accounts).
## Table of Contents
* [Table of Contents](#TableOfContents)
* [Hello_CircuitPython](#Hello_CircuitPython)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_LCD](#CircuitPython_LCD)
* [NextAssignmentGoesHere](#NextAssignment)
---

## Hello_CircuitPython

### Description & Code
The goal of this asignment was to make the Led change colors  

```python
import board
import neopixel
import time

dot = neopixel.NeoPixel(board.NEOPIXEL, 1)  # attach MetroExpress and led
dot.brightness = 0.2

print("make it rainbow!")

while True:  # makes the led change colours using colour codes 
    dot.fill((255, 0, 0))  # red
    time.sleep(0.5)
    dot.fill((255, 128, 0))  # orange
    time.sleep(0.5)
    dot.fill((255, 255, 0))  # yellow
    time.sleep(0.5)
    dot.fill((0, 255, 0))  # green
    time.sleep(0.5)
    dot.fill((0, 0, 255))  # blue
    time.sleep(0.5)
    dot.fill((255, 0, 255))  # purple
    time.sleep(0.5)

```
code  credit goes to [lucy G](https://github.com/lgray52/CircuitPython#evidence)

### Evidence
![rainbow light blinking](https://github.com/lgray52/CircuitPython/blob/main/evidence/hello_circuitpython.gif)

image credit goes to [lucy G](https://github.com/lgray52/CircuitPython#evidence)
### Wiring
There is no code required for this assignment 
Make an account with your google ID at [tinkercad.com](https://www.tinkercad.com/learn/circuits), and use "TinkerCad Circuits to make a wiring diagram."  It's really easy!  
Then post an image here.   [here's a quick tutorial for all markdown code, like making links](https://guides.github.com/features/mastering-markdown/)

### Reflection
I had no real problems with this asignment. It helped me understand how to use circuitpython and how it worked.




## CircuitPython_Servo

### Description & Code
The goal of this assignment was to control a servo using 2 buttons 
```</span> 
</pre>


```

### Evidence

### Wiring

### Reflection




## CircuitPython_LCD

### Description & Code

```python
# SPDX-FileCopyrightText: 2018 Kattni Rembor for Adafruit Industries
#
# SPDX-License-Identifier: MIT

"""CircuitPython Essentials Servo standard servo example"""
from curses import BUTTON1_PRESSED
import time
from tkinter import Button
import board
import pwmio
from adafruit_motor import servo

# create a PWMOut object on Pin A2.
pwm = pwmio.PWMOut(board.D2, duty_cycle=2 ** 15, frequency=50)

# Create a servo object, my_servo.
my_servo = servo.Servo(pwm)

while True:
    
    for angle in range(0, 180, 5):  # 0 - 180 degrees, 5 degrees at a time.
        my_servo.angle = angle 
        time.sleep(0.05)


    for angle in range(180, 0, -5): # 180 - 0 degrees, 5 degrees at a time.
        my_servo.angle = angle
        time.sleep(0.05) 
```

### Evidence

### Wiring

### Reflection





## NextAssignment

### Description & Code

```python
Code goes here

```

### Evidence

### Wiring

### Reflection
