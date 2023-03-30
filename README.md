# CircuitPython
This repository will actually serve as a aid to help you get started with your own template.  You should copy the raw form of this readme into your own, and use this template to write your own.  If you want to draw inspiration from other classmates, feel free to check [this directory of all students!](https://github.com/chssigma/Class_Accounts).
## Table of Contents
* [Table of Contents](#TableOfContents)
* [Hello_CircuitPython](#Hello_CircuitPython)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_LCD](#CircuitPython_LCD)
* [Motor Control](#Motor_Control)
* [Tempature Sensor](#Tempature_Sensor)
* [Rotary Encoder](#Rotary_Encoder)
* [Photointerrupters](#Photointerrupters)

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
![ Servo Button Turning](https://im2.ezgif.com/tmp/ezgif-2-585eafa382.gif)


### Wiring
![servobuttonwiring](https://user-images.githubusercontent.com/71402974/193278017-65c1b453-b385-4bbb-be26-60461b81be42.png)

### Reflection
This assignment was more challenging. At first, I had to get one button to controll the servo and then after add and wire the other one.



## CircuitPython_distancesensor
Credit of this whole assignment goes to [Gaby D](https://github.com/gdaless20/Circuitpython))
### Description & Code
 The goal of this assignment was to use a ultrasonic sensor to control the built in LED in the Metro m4.

```python
import time
import board
import adafruit_hcsr04
import neopixel
import simpleio

sonar = adafruit_hcsr04.HCSR04(trigger_pin=board.D5, echo_pin=board.D6)
dot = neopixel.NeoPixel(board.NEOPIXEL, 10, brightness=0.5)

r = 0
g = 0
b = 0


while True:

    try:
        distance = sonar.distance
        print((distance,))

        if distance < 5:
            r = 255
            g = 0
            b = 0
        elif distance > 5 and distance < 20:
            r = simpleio.map_range(distance, 5, 20, 255, 0)
            b = simpleio.map_range(distance, 5, 20, 0, 255)
            g = 0
            r = int(r)
            g = int(g)
            b = int(b)
        elif distance > 20 and distance < 35:
            r = 0
            b = simpleio.map_range(distance, 20, 35, 255, 0)
            g = simpleio.map_range(distance, 20, 35, 0, 255)
            r = int(r)
            g = int(g)
            b = int(b)
        elif distance > 35:
            r = 0
            b = 0
            g = 255
            r = int(r)
            g = int(g)
            b = int(b)
        print(r, g, b)
        time.sleep(0.05)

    except RuntimeError:
        print("Retrying!")
        r = 0
        g = 0
        b = 255
        time.sleep(0.1)

    print(r, g, b)
    dot.fill((r, g, b))
    time.sleep(0.05)
```

### Evidence
![134724959-4f1d69a2-bb28-4c98-8dd7-6bff58e07b80](https://user-images.githubusercontent.com/71402974/193281062-a0f293f0-4dd3-4d89-aa3b-3da11c3ac38b.gif)


### Wiring
![134725601-72db0fcb-0d50-486c-aff5-9e0ec1772057](https://user-images.githubusercontent.com/71402974/193280921-27e1fb58-eb80-486e-9955-84a4aa6fe4a1.png)

### Reflection

I copied this whole assignment from gaby(thanks) but the only problem I had was I had to move 2 files into my lib folder to get it to work.



## Circuitpython_LCD

### Description & Code
The goal of this assignment was to display the inputs of a button using the LCD screen.
 credit goes to [Elias Garcia(https://github.com/egarcia28/CircuitPython)
```python
#Elias Garcia
#When a button is presses it increses or decreases the count based on the position of a switch
#Code from Grant Gastinger

import board
from lcd.lcd import LCD
from lcd.i2c_pcf8574_interface import I2CPCF8574Interface
import time
from digitalio import DigitalInOut, Direction, Pull

# get and i2c object
i2c = board.I2C()
btn = DigitalInOut(board.D2)
btn.direction = Direction.INPUT
btn.pull = Pull.UP
clickCount = 0

switch = DigitalInOut(board.D7)
switch.direction = Direction.INPUT
switch.pull = Pull.UP
# some LCDs are 0x3f... some are 0x27...
lcd = LCD(I2CPCF8574Interface(i2c, 0x3f), num_rows=2, num_cols=16)
 
while True:
    if not switch.value:
        if not btn.value:
            lcd.clear()
            lcd.set_cursor_pos(0, 0)
            lcd.print("Click Count:")
            lcd.set_cursor_pos(0,13)
            clickCount = clickCount + 1
            lcd.print(str(clickCount))
        else:
            pass
    else:
        if not btn.value:
            lcd.clear()
            lcd.set_cursor_pos(0, 0)
            lcd.print("Click Count:")
            lcd.set_cursor_pos(0,13)
            clickCount = clickCount - 1
            lcd.print(str(clickCount))
        else:
            pass
    time.sleep(0.1) # sleep for debounce   
```

### Evidence
![193040969-56204239-2e81-486f-a2e2-43e14046091b](https://user-images.githubusercontent.com/71402974/193838626-7bbb85e5-039f-477c-a859-12f824a63c1b.gif)

### Wiring
![193033429-e5198fd6-79fd-4952-a702-64e0c3bba90c](https://user-images.githubusercontent.com/71402974/193838696-c56f5b74-1827-43ed-a351-398749fb5195.png)

### Reflection
This assignment was also easy since ELias gave me all the information I needed. The only think that I had to figure out was how to make an lcd folder and drag the files into it. 


## Motor_Control

### Description & Code
The goal of this assignment was to use a potentiometer to control the speed of a moter 

 credit for code goes to [Nicholas Bednar](https://github.com/nbednar2929/CircuitPython)

```python
import board 
#import files
import time
from analogio import AnalogOut, AnalogIn
import simpleio

motor = AnalogOut(board.A1) #motor ouput 
ptmr = AnalogIn(board.A0) #potentiometer input

while True:
    print(simpleio.map_range(ptmr.value, 96, 65520, 0, 65535)) #print my potentiometer value
    motor.value = int(simpleio.map_range(ptmr.value, 96, 65520, 0, 65535)) #push potentiometer value to motor
    time.sleep(.1) #print delay
```

### Evidence
![ezgif-2-1aee011b5e](https://user-images.githubusercontent.com/71402974/200867433-fe2f8763-22c7-4f56-9893-d5aa820d0d79.gif)


### Wiring
![moter control](https://user-images.githubusercontent.com/71402974/200862994-083d5501-a44c-46cc-9a53-fe3805c9c849.png)

### Reflection 
The main peice of advice would be double checking your wiring before you plug in the bateries so you dont fry any transistors or diodes. For the diodes the power flows in the direction of the silver cap. For the transistor, facing the flat side the power flows from left to right.

## Tempature_Sensor 
The goal of this project is to use a tempature sensor to detect the temp and read it onto an LED screen.

all images and code and videos are from [Cooper M](https://github.com/Cooper-Moreland/EngNotebook3#video)
### Code 

```python
#Code from cooper moreland 
import board
import analogio
import time
from lcd.lcd import LCD
from lcd.i2c_pcf8574_interface import I2CPCF8574Interface


TMP36_PIN = board.A0  # Analog input connected to TMP36 output.

i2c = board.I2C()
lcd = LCD(I2CPCF8574Interface(i2c, 0x27), num_rows=2, num_cols=16) #0x27 or 0x3f depending on which one works

# Function to simplify the math of reading the temperature.
def tmp36_temperature_C(analogin):
    millivolts = analogin.value * (analogin.reference_voltage * 1000 / 65535)
    return (millivolts - 500) / 10

# Create TMP36 analog input.
tmp36 = analogio.AnalogIn(TMP36_PIN)
desired_temp_min = 70
desired_temp_max = 78

while True:
    # Read the temperature in Celsius.
    temp_C = tmp36_temperature_C(tmp36)
    # Convert to Fahrenheit.
    temp_F = (temp_C * 9/5) + 32
    # Print out the value and delay a  few seconds before looping again.
    print("Temperature: {}C {}F".format(temp_C, temp_F))
    time.sleep(3.0)
    if temp_F >= desired_temp_min and temp_F <= desired_temp_max:
        lcd.clear()
        lcd.print("It feels great  in here")
    if temp_F < desired_temp_min:
        lcd.clear()
        lcd.print("brrr too cold")
    if temp_F > desired_temp_max:
        lcd.clear()
        lcd.print("Too hot")
    time.sleep(1.0)
```
### Evidence

https://user-images.githubusercontent.com/71402974/225631724-82ae58b7-29bc-4873-a648-17407a4583d4.mov

![Screenshot 2023-03-14 100722](https://user-images.githubusercontent.com/71402974/225633140-fc2a251c-1eeb-4607-bcae-094a2afb7475.png)


### Reflection
At first this asignment was kind of hard because I tried to use chat gbt for my code and wiring and that did not work good. Then I just looked on coopers document and then I figured it out.


## Rotary_Encoder

The goal of this asignment is to write code that controlls a mini traffic light 

all images and code and videos are from [Grant G](https://github.com/ggastin30/CPython)

### code 

```python
import time
import rotaryio
import board
from lcd.lcd import LCD
from lcd.i2c_pcf8574_interface import I2CPCF8574Interface
from digitalio import DigitalInOut, Direction, Pull
import digitalio

lcdPower = digitalio.DigitalInOut(board.D7) #connects the lcd to pin 8
lcdPower.direction = digitalio.Direction.INPUT #sets the lcd power flow as input
lcdPower.pull = digitalio.Pull.DOWN #Pulls the power of the lcd down to ground

while lcdPower.value is False: #creates an infinite loop that repeats until the lcd turns on
    print("zzz")
    time.sleep(0.1)

print("I'm awake")

encoder = rotaryio.IncrementalEncoder(board.D3, board.D2)
last_position = 0
btn = DigitalInOut(board.D1)
btn.direction = Direction.INPUT
btn.pull = Pull.UP
state = 0
Buttonyep = 1

i2c = board.I2C()
lcd = LCD(I2CPCF8574Interface(i2c, 0x27), num_rows=2, num_cols=16)

ledGreen = DigitalInOut(board.D8)
ledYellow = DigitalInOut(board.D9)
ledRed = DigitalInOut(board.D10)
ledGreen.direction = Direction.OUTPUT
ledYellow.direction = Direction.OUTPUT
ledRed.direction = Direction.OUTPUT

while True:
    position = encoder.position
    if position != last_position:
        if position > last_position:
            state = state + 1
        elif position < last_position:
            state = state - 1
        if state > 2:
            state = 2
        if state < 0:
            state = 0
        print(state)
        if state == 0: 
            lcd.set_cursor_pos(0, 0)
            lcd.print("GOOOOO")
        elif state == 1:
            lcd.set_cursor_pos(0, 0)
            lcd.print("yellow")
        elif state == 2:
            lcd.set_cursor_pos(0, 0)
            lcd.print("STOPPP")
    if btn.value == 0 and Buttonyep == 1:
        print("buttion")
        if state == 0: 
                ledGreen.value = True
                ledRed.value = False
                ledYellow.value = False
        elif state == 1:
                ledYellow.value = True
                ledRed.value = False
                ledGreen.value = False
        elif state == 2:
                ledRed.value = True
                ledGreen.value = False
                ledYellow.value = False
        Buttonyep = 0
    if btn.value == 1:
        time.sleep(.1)
        Buttonyep = 1
    last_position = position
```

### Evidence 

https://user-images.githubusercontent.com/91094422/228268440-82672a8a-6c48-4d38-b2ec-45b21c218bff.mp4

### Wiring

![228265020-5b9756c1-e736-4655-9ca5-9d1b01f2ac95](https://user-images.githubusercontent.com/71402974/228564364-369c240d-178f-416c-ad1b-2ebe87353981.png)

### Reflection
I think that was the easiest asignment yet. All I did was look at Grants notebook to find the code and wiring. After that, I had some problems making sure rhe wiring was in the right pins but that was the only issue.



## Photointerrupters

The goal of this assignment was to wire a photointeruptror to count how many times it senses something.

all images and code and videos are from [Graham](https://github.com/VeganPorkChop/Engineering-3-Documentation/tree/master/IntermediateCoding-Engineering%203#CircuitPy_PhotoInterruptors)

### Code

```python
import time
import digitalio
import board

photoI = digitalio.DigitalInOut(board.D7)
photoI.direction = digitalio.Direction.INPUT
photoI.pull = digitalio.Pull.UP

last_photoI = True
last_update = -4

photoICrosses = 0

while True:
    if time.monotonic()-last_update > 4:
        print(f"The number of crosses is {photoICrosses}")
        last_update = time.monotonic()
    
    if last_photoI != photoI.value and not photoI.value:
        photoICrosses += 1
    last_photoI = photoI.value
  ```


### Wiring

![68747470733a2f2f726976717565732e6769746875622e696f2f646f63732f70686f746f696e74636972637569742e706e67](https://user-images.githubusercontent.com/71402974/228853000-0386756c-e703-4e5f-900d-47fde7acd421.png)



### Evidence


![226713736-399d0f22-aff7-4dd4-8ebb-a26b9d3674bc](https://user-images.githubusercontent.com/71402974/228853039-7a0f765f-388a-4611-87a3-1eb54d766b5f.gif)



### Reflection 
This assignment was pretty easy because I had the wiring and code already and I had no problems doing it.
