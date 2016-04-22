---
layout: post
title: Simulating Lightning with Python
date: 2015-12-20 21:35 
description: More Turtle Graphics 
thumbnail: /img/lightning/lightning2.png
comments: True
---

<br/>
<img class = "post-thumb"  src="/img/lightning/lightning2.png" height="120" width="120">I wanted to try something different from the spiral figures I had been making earlier, and I thought it would be interesting to try simulating lightening. I initially wrote a branching function and extended it enough times to cover the canvas, but that felt like cheating, since it was limited to a particular image size. I decided instead to write a function that creates a single branch and then calls itself recursively. Since the zig-zagging of the lightning is produced with a pseudorandom element number generator, each image is different, and some of my initial efforts resulted in lightning that turned around and went back towards the sky. To fix that, I added a little if statement to keep things pointed downwards at all times. At first, I came up with stopping conditions that were based on any trace leaving the canvas, but I wasn't happy with the resulting images - they would stop with many branches still "up in the air". I like the idea of all the lightning making contact with the ground, so with a little help from Pythagoras and a recursion counter, I found something to reliably produce an image where the lightning stretches from sky to ground and the program doesn't go into an infinite loop. 
 
Here is the result:
![lightningImage1](/img/lightning/lightning1.png)
I thought it would be nice to have the initial bolt start with a thick pen and become smaller as it approached the ground. I tried various approaches, and came up with the following:

{% highlight python %} 
def clamp(n, minn, maxn):
    return max(min(maxn, n), minn) # thank you stack overflow

...

pen = 10 - clamp(2*math.floor(math.log(len(pos),2)),0,9)
{% endhighlight %}
![lightningImage1](/img/lightning/lightning2.png)
I eventually realized that with a few extra lines of code, you can write vector-based .eps files, which seemed greatly preferable to taking screenshots of the Turtle Graphics window. For some reason, though, the canvas color is lost and replaced with white. So my white lightning on a black background resulted in a blank white image. No matter, Black lightning one a white background looks pretty cool as well:
<br/><br/>
![lightningImage1](/img/lightning/lightning3.png)
<br/><br/>
![lightningImage1](/img/lightning/lightning4.png)
<br/>

Code:

{% highlight python %}

import random
import turtle
import math

# A Lightning generator

def clamp(n, minn, maxn):
    return max(min(maxn, n), minn) # thank you stack overflow

turtle.tracer(0, 0) #runs much faster this way; no image until the whole thing is done
wn = turtle.Screen()
ts = turtle.getscreen() # needed for writing to .eps file
wn.colormode(1)
turtle.bgcolor(1,1,1) #white
alex = turtle.Turtle()
alex.speed(10)
alex.pensize(10)
alex.ht()
alex.up()
alex.goto(-200, 340) # initial seed position
alex.seth(random.uniform(255, 285)) # set heading
h1 = alex.heading() # get heading
alex.color(0,0,0)  # White

# Initial bolt
for i in range(50):
    alex.down()
    alex.forward(abs(round(random.gauss(2, 5), 0))) # abs limits motion to forward
    alex.seth(h1 + random.gauss(7, 30))
    x = alex.xcor()
    y = alex.ycor()
h2 = alex.heading()
pos = [[x,y]] # list - new initial position
head = [h2] # list - new initial position

recursions = 0

def lightning(pos, head,spread):
    """pos is a list [[x,y]] by default inherited from the end position of the initial bolt
    head is a value from 0-360 degrees. Spread controls how wide the branches are"""
    global recursions
    recursions += 1
    for i in range(len(pos)):
        pen = 10 - clamp(2*math.floor(math.log(len(pos),2)),0,9)
        alex.up()
        alex.goto(pos[i])
        alex.down()
        for j in range(random.randint(20,40)):
            alex.pensize(pen)
            head1 = head[i] + random.gauss(spread,15)
            if(180 > head1 > 0): # keep lightning pointing downwards
                alex.seth(-head1)
            else:
                alex.seth(head1)
            alex.forward(abs(round(random.gauss(1,4),0))) # abs limits motion to forward
            x1 = alex.xcor()
            y1 = alex.ycor()
            h3 = alex.heading()
        alex.up()
        alex.goto(pos[i])
        alex.down()
        pos.append([x1,y1])
        head.append(h3)
        for k in range(random.randint(20,40)):
            alex.pensize(pen)
            head2 = (head[i] + random.gauss(spread,15))
            if(180 > head2 > 0):
                alex.seth(-head2)
            else:
                alex.seth(head2)
            alex.forward(abs(round(random.gauss(2,4),0))) 
            x2 = alex.xcor()
            y2 = alex.ycor()
            h4 = alex.heading()
        pos.append([x2,y2])
        head.append(h4)
    dist = [[math.sqrt(x**2 + y**2)] for [x,y] in pos]
    if(recursions < 11 and min([x for sublist in dist for x in sublist]) < 460):
        lightning(pos[(i+1):], head[(i+1):],spread)

lightning(pos,head,5)
ts.getcanvas().postscript(file='lightning10.eps')
turtle.update()
wn.exitonclick()
{% endhighlight %}
