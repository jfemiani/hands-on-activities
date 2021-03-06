# Turtles in Python 

The `turtle` module in python allows you to draw figures by moving a turtle around the screen. 

To get started, type the following into the 'main.py' file on the left:

```python
import turtle
t = turtle.Turtle()
t.showturtle()
```

Then press the `Run` button to see an image of the "turtle".  


<iframe src="https://trinket.io/embed/python/4c4e48fedb?runMode=console" width="100%" height="600" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

It actually looks more like an arrow, but you can add the following line if you like:

```python
t.shape('turtle')
```
and then you should see a more "turtly" turtle. 

<iframe src="https://trinket.io/embed/python/f6252aa067" width="100%" height="600" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>



Let's try drawing something. 

You can move the turtle by typing 
```python
t.forward(100)
t.left(90)
t.forward(100)
t.left(90)
```

#### Exercise
*Can you draw a square with the turtle? Try modifying the code below*


<iframe src="https://trinket.io/embed/python/e34bd4c326" width="100%" height="600" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>



You can repeat instructions in a variety of ways; one of them is to use a loop.

The following code will draw an octagon:

```python
for i in range(8):
    t.forward(30)
    t.left(360/8)
```

Try it out below:

<iframe src="https://trinket.io/embed/python/cc4cbbd80e" width="100%" height="600" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>


You can also use a _variable_ to in order to hold data (such as the number of sides). 


```python
n = 8
for i in range(n):
    t.forward(300/n)
    t.left(360.0/n)
```

Try changing the value of `n` in this code:

<iframe src="https://trinket.io/embed/python/d4ba390f66" width="100%" height="600" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>


You can fill in shaped by telling the turtle to start filling (`t.begin_fill()`) and later stop filling (`t.end_fill()`) the shape. 

Tye modifying the code to fill in the shape:

```python
t.fillcolor('red')
n = 3
t.begin_fill()
for i in range(n):
    t.forward(300/n)
    t.left(360.0/n)
t.end_fill()
```
Try changing the fill color of this shape:

<iframe src="https://trinket.io/embed/python/ac7c984827" width="100%" height="600" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>


You can use another variable to to hold the original fill color, so that you can restore it later. 
> NOTE: It is often a good idea for a program to avoid unexpected side-effects, like changing the turtle color

```python
old_color = t.fillcolor()
t.fillcolor('red')
n = 3
t.begin_fill()
for i in range(n):
    t.forward(300/n)
    t.left(360.0/n)
t.end_fill()
t.fillcolor(old_color)
```
Notice that the turtle ends up in the same position and color that it started with:

<iframe src="https://trinket.io/embed/python/fb28cf3f34" width="100%" height="600" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

You can also change the line color using `t.color()` or change it with `t.color('blue')` (or similar). Try it out!

#### Exercise
_Can you modify the code above to draw a 5 pointed star?  It is very similar to the code above, except that you turn right by an angle of `180*(1-1/n)`._




Another way to repeat code is by defining a function. In python you define a function like this:

```python
def star(t):
  sides = 5
  length = 100
  for i in range(sides):
    t.forward(length)
    t.right(180*(1-1/sides))
```
> NOTE: I added some _local variables_ to this function, `sides` and `length`. 
> They are only accessible inside the function, and I tried to pick names for 
> them that would be easy to remember and explain. 

Then you can draw several stars like this:
```python
t.penup(); t.goto(-60, 0); t.pendown()
star(t)

t.penup();  t.goto(60, 0); t.pendown()
star(t)
```

Try it out below -- see if you add some stars at different locations...

<iframe src="https://trinket.io/embed/python/29e3a4d3a4" width="100%" height="600" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>


The function can receive some information (input parameters) that we can use to control its behavior. 

Let's add parameters to set the number of sides, and the position of the star. 

```python
def star(t, x, y, length, sides):
  t.penup()
  t.goto(x, y)
  t.pendown()
  for i in range(sides):
    t.forward(length)
    t.left(180*(1-1/sides))
```

Then we can call this function with a variety of values.

```python
star(t, -30, 20, 30, 5)
star(t,  30, -10, 30, 5)
star(t,  15, -15, 20, 5)
star(t,  0, 0, 20, 9)
t.hideturtle()
```

Let's see what that looks like below:

<iframe src="https://trinket.io/embed/python/7f64bc1805" width="100%" height="600" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>


#### Exercise
_Can you add a parameter to change the fill color of the star?_

#### Exercise 
_What else can you draw with the turtle? Use loops and functions to make interesting shapes._

(I modified it to draw random shapes below)

<iframe src="https://trinket.io/embed/python/a8bffcbebe" width="100%" height="600" frameborder="0" marginwidth="0" marginheight="0" allowfullscreen></iframe>

<hr>
Thank you!