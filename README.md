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
```python

<pre style="color:#000000;background:#ffffff;"><span style="color:#696969; "># SPDX-FileCopyrightText: 2018 Kattni Rembor for Adafruit Industries</span>
<span style="color:#696969; ">#</span>
<span style="color:#696969; "># SPDX-License-Identifier: MIT</span>

<span style="color:#696969; ">"""CircuitPython Essentials Servo standard servo example"""</span>
<span style="color:#800000; font-weight:bold; ">from</span> curses <span style="color:#800000; font-weight:bold; ">import</span> BUTTON1_PRESSED
<span style="color:#800000; font-weight:bold; ">import</span> time
<span style="color:#800000; font-weight:bold; ">from</span> tkinter <span style="color:#800000; font-weight:bold; ">import</span> Button
<span style="color:#800000; font-weight:bold; ">import</span> board
<span style="color:#800000; font-weight:bold; ">import</span> pwmio
<span style="color:#800000; font-weight:bold; ">from</span> adafruit_motor <span style="color:#800000; font-weight:bold; ">import</span> servo

<span style="color:#696969; "># create a PWMOut object on Pin A2.</span>
pwm <span style="color:#808030; ">=</span> pwmio<span style="color:#808030; ">.</span>PWMOut<span style="color:#808030; ">(</span>board<span style="color:#808030; ">.</span>D2<span style="color:#808030; ">,</span> duty_cycle<span style="color:#808030; ">=</span><span style="color:#008c00; ">2</span> <span style="color:#44aadd; ">**</span> <span style="color:#008c00; ">15</span><span style="color:#808030; ">,</span> frequency<span style="color:#808030; ">=</span><span style="color:#008c00; ">50</span><span style="color:#808030; ">)</span>

<span style="color:#696969; "># Create a servo object, my_servo.</span>
my_servo <span style="color:#808030; ">=</span> servo<span style="color:#808030; ">.</span>Servo<span style="color:#808030; ">(</span>pwm<span style="color:#808030; ">)</span>

<span style="color:#800000; font-weight:bold; ">while</span> <span style="color:#074726; ">True</span><span style="color:#808030; ">:</span>
    
    <span style="color:#800000; font-weight:bold; ">for</span> angle <span style="color:#800000; font-weight:bold; ">in</span> <span style="color:#400000; ">range</span><span style="color:#808030; ">(</span><span style="color:#008c00; ">0</span><span style="color:#808030; ">,</span> <span style="color:#008c00; ">180</span><span style="color:#808030; ">,</span> <span style="color:#008c00; ">5</span><span style="color:#808030; ">)</span><span style="color:#808030; ">:</span>  <span style="color:#696969; "># 0 - 180 degrees, 5 degrees at a time.</span>
        my_servo<span style="color:#808030; ">.</span>angle <span style="color:#808030; ">=</span> angle 
        time<span style="color:#808030; ">.</span>sleep<span style="color:#808030; ">(</span><span style="color:#008000; ">0.05</span><span style="color:#808030; ">)</span>


    <span style="color:#800000; font-weight:bold; ">for</span> angle <span style="color:#800000; font-weight:bold; ">in</span> <span style="color:#400000; ">range</span><span style="color:#808030; ">(</span><span style="color:#008c00; ">180</span><span style="color:#808030; ">,</span> <span style="color:#008c00; ">0</span><span style="color:#808030; ">,</span> <span style="color:#44aadd; ">-</span><span style="color:#008c00; ">5</span><span style="color:#808030; ">)</span><span style="color:#808030; ">:</span> <span style="color:#696969; "># 180 - 0 degrees, 5 degrees at a time.</span>
        my_servo<span style="color:#808030; ">.</span>angle <span style="color:#808030; ">=</span> angle
        time<span style="color:#808030; ">.</span>sleep<span style="color:#808030; ">(</span><span style="color:#008000; ">0.05</span><span style="color:#808030; ">)</span> 
</pre>


```

### Evidence

### Wiring

### Reflection




## CircuitPython_LCD

### Description & Code

```python
Code goes here

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
