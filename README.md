# Classic-snake-game

My project name is snake game. 
The snake game firstly introduces in 1976 and developed by an American company name gremlin industry.
It is a very popular and famous game. since a long time when we used the Nokia keypad-phone.
It is a single-player game. There are two main elements which one is a snake and the other is food.
The player controls a snake by pressing the arrow key. Snake move around the screen and eating food.
With each food eaten the tail is grown by one unit. The goal of this game is to eat as many foods as possible. And achieve maximum points.
Six important rules for this game are:-
1. Snake moves at a constant speed
2. Snake moves only in direction north, south, east, west.
3. Direction of snake control by arrow key 
4. Food appears at a random location 
5. When a snake eats food its tail gets longer.
6. When the snake crosses itself or touches a wall then the game will be over.

I created a snake game using a python programming language. I use some python libraries like 
Turtle, Random, Time for this simple game.
Turtle:Turtle module is like a drawing board, which lets us the command to drow all over it.it is used to creating shapes pictures & games. Random module is used to generate random numbers in python. Time-it provides the functionality of time
 
I divided this project into 5 steps:
1. Importing modules and declare default variable
2. Setup screen, creating snakehead, snake food and scoreboard.
3. Creating some functions for snake movement.
4. Created a keyboard shortcut to control snake movement through the keyboard.
5. Created the main loop which repeats an infinite number of repeats until the loop is broken.







Step1:
Firstly we will import all the necessary modules into the program and will give the default value for the game. Like score=0, high score=0.

Step2:
We will create the windows screen for the game. 
The function turtle.screen() is used to create a window. 
in this code, our window screen variable is “wn”.
we have to give the window a name with function wn.title(“Classic-snake-game”). 
To set the background colour for the windows we have used ‘wn.bgcolor(‘yellow’).
Set the windows height and width with the function “wn.setup(width=x,hight=y)”, here width=600 and height=600.
As we do not need any screen other than the screen board, so the function wn.tracer(0) turn off the screen updates.

#snake head
Now, we will create a snakehead it is basically a turtle that will be a snake and it will move around.
For creating a Tuttle we will use “turtle.turtle()” and assign the name head.
The head speed is set to 0 as we just initialize and the head does not need to move.
Let initialize the head shape and colour by using a head.shap(“square”) and head.colour (“black”).
The function “head.penup()” makes sure that the path taken by the snake is not drow on the screen.

The head.goto(0,0) is used for snake position to be the centre of the windows and the direction to stop we will use head.direction=”stop” 

#snake food
Now we will creat snake food 





#segments=[]
We need the functionality that increase thr snake boday every time it touches food . so, we used array for this we create an array called segments, which is intialized empty.


#Scoreboard 

Sc.write function is used to write the text at the current turtle potion.

Step 3:
Firstly, we need to define a function for each of these directions and set the head. direction to up, down, left and right.
After that, we will go ahead and make the snake move.
So, we will define a function called moves().
If the head goes up, the “y” coordinate is increased.
If the head goes down, the “y” coordinate decreases.
If the head moves right, the “x” coordinate increase and 
If the head moves left, the “x” coordinate decrease


Step4:
We will assign a key to the snake movements.
By clicking the keyboard, we can move the snake up, down left and right directions.
We need the system to listen to our control keypress, so we will add a function called “wn.listen()” that listens to the key pressed.
Every keypress needs to be bound to a function that carries out an action.
We will use the function “wn.onkeypress(function,”key”)” for all four.
Here, I used the arrow key for movement.



And the last step5:
So, now the function does nothing until it’s called. We need to call the function every time we update the screen or the window.
We have to be sure that the snake dies when it collides with the border. We already have the co-ordinate of the border. So, we just need to reset the snakehead position when it touches the coordinates. Also, the snake needs to stop moving and hence the direction to stop.

To slow down the snake movement we need to use the time module otherwise the default behaviour for the move function is very fast. So, we will use the function time.sleep() to reduce turtle speed. The segment needs to disappear when the snake dies.
So, now we need to set the position of the segments outer the window coordinates. The game restarts and hence clear the segment list. 
 We need to add a segment to the snake body every time it touches the food. So, we have the condition that checks for the head’s collision with food.
Create a new segment, define its speed, and colour and append it to segments array.
Now, adding the segment to the snakehead is not enough. These segments need to move when the snake moves. 
To move the last segments which is the position x to x-1, x-1 to x-2 and so on.

At last 
We need to see the situation when the score increase. The first one is when the head collides with the food. Increase and update the high score.
We used sc.write() function to write the score on the screen.
We need to reset the score when the snake collides with the border and with its own tail
And then called the function time sleep(delay) to reduce turtle speed.




#imports
import turtle
import time
import random

delay = 0.1

#scores
score = 0
high_score = 0

#set up screen
wn = turtle.Screen()
wn.title("Snake Game")
wn.bgcolor('yellow')
wn.setup(width=600, height=600)
wn.tracer(0)

#snake head
head = turtle.Turtle()
head.speed(0)
head.shape("square")
head.color("black")
head.penup()
head.goto(0,0)
head.direction = "stop"

#snake food
food= turtle.Turtle()
food.speed(0)
food.shape("square")
food.color("red")
food.penup()
food.goto(0,100)

segments = []

#scoreboards
sc = turtle.Turtle()
sc.speed(0)
sc.shape("square")
sc.color("black")
sc.penup()
sc.hideturtle()
sc.goto(0,260)
sc.write("score: 0  High score: 0", align = "center", font=("ds-digital", 24, "normal"))

#Functions
def go_up():
    if head.direction != "down":
        head.direction = "up"
def go_down():
    if head.direction != "up":
        head.direction = "down"
def go_left():
    if head.direction != "right":
        head.direction = "left"
def go_right():
    if head.direction != "left":
        head.direction = "right"
def move():
    if head.direction == "up":
        y = head.ycor()
        head.sety(y+20)
    if head.direction == "down":
        y = head.ycor()
        head.sety(y-20)
    if head.direction == "left":
        x = head.xcor()
        head.setx(x-20)
    if head.direction == "right":
        x = head.xcor()
        head.setx(x+20)

#keyboard bindings
wn.listen()
wn.onkeypress(go_up, "Up")
wn.onkeypress(go_down, "Down")
wn.onkeypress(go_left, "Left")
wn.onkeypress(go_right, "Right")

#MainLoop
while True:
    wn.update()

    #check collision with border area
    if head.xcor()>290 or head.xcor()<-290 or head.ycor()>290 or head.ycor()<-290:
        time.sleep(1)
        head.goto(0,0)
        head.direction = "stop"

        #hide the segments of body
        for segment in segments:
            segment.goto(1000,1000) #out of range
        #clear the segments
        segments.clear()

        #reset score
        score = 0

        #reset delay
        delay = 0.1

        sc.clear()
        sc.write("score: {}  High score: {}".format(score, high_score), align="center", font=("ds-digital", 24, "normal"))

    #check collision with food
    if head.distance(food) <20:
        # move the food to random place
        x = random.randint(-290,290)
        y = random.randint(-290,290)
        food.goto(x,y)

        #add a new segment to the head
        new_segment = turtle.Turtle()
        new_segment.speed(0)
        new_segment.shape("square")
        new_segment.color("black")
        new_segment.penup()
        segments.append(new_segment)

        #shorten the delay
        delay -= 0.001
        #increase the score
        score += 10

        if score > high_score:
            high_score = score
        sc.clear()
        sc.write("score: {}  High score: {}".format(score,high_score), align="center", font=("ds-digital", 24, "normal")) 

    #move the segments in reverse order
    for index in range(len(segments)-1,0,-1):
        x = segments[index-1].xcor()
        y = segments[index-1].ycor()
        segments[index].goto(x,y)
    #move segment 0 to head
    if len(segments)>0:
        x = head.xcor()
        y = head.ycor()
        segments[0].goto(x,y)

    move()

    #check for collision with body
    for segment in segments:
        if segment.distance(head)<20:
            time.sleep(1)
            head.goto(0,0)
            head.direction = "stop"

            #hide segments
            for segment in segments:
                segment.goto(1000,1000)
            segments.clear()
            score = 0
            delay = 0.1

            #update the score     
            sc.clear()
            sc.write("score: {}  High score: {}".format(score,high_score), align="center", font=("ds-digital", 24, "normal"))
    time.sleep(delay)
wn.mainloop()  
