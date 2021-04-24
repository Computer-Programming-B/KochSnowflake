
Koch Snowflake
===============
![](kochflake.gif)   
In this assignment, you will  make a snowflake. But not just any snowflake, you will make a [Koch snowflake](https://en.wikipedia.org/wiki/Koch_snowflake) using a process called recursion. The Koch snowflake is a *fractal* because it consists of three copies of the *Koch curve*, arranged along the sides of a triangle. (You may find slides 235-268 of the [slide presentation](https://docs.google.com/presentation/d/1rICcmNbnGYsB-cV_6EatPyzcOS2sId80Jh2kayUzm4Q/edit#slide=id.ga2b2b98a27_0_165) helpful in completing this assignment)  
![](KochSnowFlake2.PNG)   
The base case is just the line:   
![](KochSnowFlake3.PNG)   
At the next level there is an "outer bend." The straight line is replaced by four lines, each one third the length of the parent, arranged this way:   
![](KochSnowFlake4.PNG)   
Each new level replaces the straight lines of the previous level with bent lines, exactly the same way. The red color was added here to make the previous level more visible. Your version can be all one color.   
![](KochSnowFlake5.PNG)   

Suggested steps to get started:
---------------------------------
1. Here's some starter code to draw one side of the Koch snowflake:
```Python
import turtle
tommy = turtle.Turtle()
def koch(sideLength, level):
    if level > 0:
        for angle in [60, -120, 60, 0]:
            tommy.forward(sideLength/3)
            tommy.left(angle)
    else:
        tommy.forward(sideLength)

# Test
koch(100, 0) #length of side is 100, level of 0 means no outer bend
tommy.pensize(3)
koch(100, 1) #length of side is 100, level of 1 means one outer bend
```

2. Run and test the code. You should see the following output   
![](KochSnowFlake6.PNG)   
3. The problem with the starter code is that it won't work correctly with a `level` greater than one. That is, it won't put another outer bend inside of the first. To do that, we'll need to make the function *recursive*. You will want to replace the commented line of code with a recursive call to `koch` with a side length of `sideLength/3` and an level one less than `level`. By substracting one, our function will progress towards the *base case* of a straight line.
 
 ```Python
import turtle
tommy = turtle.Turtle()
def koch(sideLength, level):
    if level > 0:
        for angle in [60, -120, 60, 0]:
            tommy.forward(sideLength/3) #replace this with a recursive call to koch
            tommy.left(angle)
    else:
        tommy.forward(sideLength)

# Test
tommy.pensize(3)
koch(100, 2) #level of 2 means one outer bend inside of each outer bend
```

4. When you get one side of the snowflake working, combine three of them to make the entire snowflake. To do this, define a new function `snowflake`:
```Python
def snowflake(sideLength, level):
    # loop 3 times
      # call koch to make one side with the given sideLength and level
      # turn tommy to the right by 120 degrees
```
5. Add code to call the `snowflake` function. You should now see a fully formed snowflake!

Extension:
---------
If you have extra time, experiment with color and fill. You can make multiple snowflakes of random colors, levels and side lengths. You can also make snowflakes with 2,4,5 or any other number of sides by dividing 360 by the number of sides to calculate the angle that tommy turns in the `snowflake` function and increasing the number of times the loop runs to match the number of sides.   

You can generate your own version of the Koch Snow Flake by changing the turning angles in the `koch` function to something other than `[60, -120, 60, 0]`. See the examples below and check out http://en.wikipedia.org/wiki/Koch_snowflake for examples and implement your favorite.
![](KochCurve.PNG)   
Your snowflake doesn't have to look like any other, it doesn't even have to be a snowflake. Have fun and be creative!

Samples of Student work
-----------------------
[Gloria](GloriaKochSnowflake.PNG)   
[Tommy](TommyKochSnowflakes.gif)   
[Marissa](Marissa.PNG)   
[Ken](KenKochSnowflake.gif)   
[Rachel](Rachel.PNG)   
[Benjamin](BenjaminKochSnowflake.gif)   

<div align="center">
<i>This assignment is based on Mr. Raymond Chan's Koch Snowflake assignment and <a href="https://python-with-science.readthedocs.io/en/latest/koch_fractal/koch_fractal.html">Python with Science</a></i>
</div>
