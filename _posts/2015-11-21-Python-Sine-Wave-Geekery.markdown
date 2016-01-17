---
layout: post
title: Python Sine Wave Geekery
date: 2015-11-21 11:47 
description: An illustration of the concept of sine wave as rotation 
thumbnail: /img/sineWaveGeekery/sineThumb.png
comments: True
---

<img class = "post-thumb" src="/img/sineWaveGeekery/sineThumb.png">I was messing around with the Python's turtle graphics and wrote a simple program to illustrate the idea that a sine wave is essentially a rotating circle moving through time. The blue line/dot represents the circle viewed from the side, and the yellow arrow is time. 

It may help to imagine a horizontal line moving up and down along with the blue, green and black dots, and a vertical line moving to the right along with the black dot and the yellow arrowhead. 

<iframe width="700" height="394" src="https://www.youtube.com/embed/APAAOGLpYzs" frameborder="0" allowfullscreen></iframe>

<br/>
Another, static way to view the same idea can be seen below. The circles are moving through time, with each one spaced about .284 ms apart. The screenshot shows about 2.73 ms of time in total. As the circle spins, the height of the dot (y component) is the same as the amplitude of the sine wave.

![rotating circle sine wave](/img/phase/rotatingCircleSine.jpg)

Code:

```python
import turtle
import math
# turtleSet function makes the code a bit more compact
def turtleSet(name, shape, speed, color, pen, pos_x, pos_y):
    name.ht()
    name.up()
    name.shape(shape)
    name.speed(speed)
    name.color(color)
    name.pensize(pen)
    name.setposition(pos_x, pos_y)
    name.down()
    name.st()
wn = turtle.Screen()
background = turtle.Turtle()
background.speed(0)
background.up()
background.goto(325, 325)
background.down()
background.right(90)
background.fillcolor("red")
background.begin_fill()
for i in range(4): # Draw a 650 x 650 square
    background.forward(650)
    background.right(90)
background.end_fill()
height = 200 #amplitude
period = 25 # Period, but without any specific unit.
circle = turtle.Turtle()
turtleSet(circle, 'circle', 10, "green", 2, height, 0)
circle.left(90)
sine = turtle.Turtle()
turtleSet(sine, 'circle', 10, "black", 2, -325, 0)
sine.st()
sine.left(45)
line = turtle.Turtle()
turtleSet(line, 'circle', 10, "blue", 2, -286, 0)
line.left(90)
time = turtle.Turtle()
turtleSet(time, 'arrow', 10, "yellow", 2, -325, 0)
time.right(0)
for i in range(650):
    x = height*math.cos(i/period)
    y = height*math.sin(i/period)
    sine.goto(i-325, y)
    circle.goto(x, y)
    line.goto(-286, y)
    time.goto(i-325, 0)
wn.exitonclick()
```