from re import X
from tkinter import Y
import tracemalloc
import turtle
import time
import random

speed = 0.15

window = turtle.Screen()
window.title('Snake 2D')
window.bgcolor('lightgreen')
window.setup(width=800, height=600)
window.tracer(0)

head = turtle.Turtle()
head.speed(0)
head.shape('square')
head.color('black')
head.penup()
head.goto(0,0)
head.direction = 'stop'

fruit = turtle.Turtle()
fruit.speed(0)
fruit.shape('circle')
fruit.color('red')
fruit.penup()
fruit.goto(0,50)
fruit.shapesize(0.60, 0.60)

tails = []

score = 0
save = turtle.Turtle()
save.speed(0)
save.shape('square')
save.color('black')
save.penup()
save.goto(0,250)
save.hideturtle()
save.write('Puan: {}'.format(score), align='center', font=('arialblack',24,'normal'))
save.shapesize(0.50,0.50)

def move():
	if head.direction == 'up':
		y = head.ycor()
		head.sety(y + 20)
	if head.direction == 'down':
		y = head.ycor()
		head.sety(y - 20)
	if head.direction == 'right':
		X = head.xcor()
		head.setx(X + 20)
	if head.direction == 'left':
		X = head.xcor()
		head.setx(X	- 20)

def goUp():
	if head.direction != 'down':
		head.direction = 'up'
def goDown():
	if head.direction != 'up':
		head.direction = 'down'
def goRight():
	if head.direction != 'left':
		head.direction = 'right'
def goLeft():
	if head.direction != 'right':
		head.direction = 'left'
		
window.listen()
window.onkey(goUp, 'Up')
window.onkey(goDown, 'Down')
window.onkey(goRight, 'Right')
window.onkey(goLeft, 'Left')

while True:
	window.update()
	
	if head.xcor()>399 or head.xcor()<-399 or head.ycor()>299 or head.ycor()<-299:
		time.sleep(1)
		head.goto(0,0)
		head.direction = 'stop'

		for tail in tails:
			tail.goto(1000,1000)
		
		tails = []

		score = 0
		save.clear()
		save.write('Puan: {}'.format(score), align='center', font=('arialblack',24,'normal'))

		speed = 0.15

	if head.distance(fruit) < 17.5:
		x = random.randint(-350, 350)
		y = random.randint(-250, 250)
		fruit.goto(x, y)

		score = score + 10
		save.clear()
		save.write('Puan: {}'.format(score), align='center', font=('arialblack',24,'normal'))

		speed = speed - 0.001

		newTail = turtle.Turtle()
		newTail.speed(0)
		newTail.shape('square')
		newTail.color('black')
		newTail.penup()
		tails.append(newTail)

	for i in range(len(tails)-1,0,-1):
		x = tails[i-1].xcor()
		y = tails[i-1].ycor()
		tails[i].goto(x,y)

	if len(tails)>0:
		x = head.xcor()
		y = head.ycor()
		tails[0].goto(x,y) 

	move()
	time.sleep(speed)

	for segment in tails:
         if segment.distance(head) < 20:
            time.sleep(1)
            head.goto(0, 0)
            head.direction = "stop"			
            for segment in tails:
                segment.goto(1000, 1000)
            tails = []
            score = 0
            save.clear()
            save.write('Puan: {}'.format(score), align='center', font=('Arial', 24, 'normal'))
            hiz = 0.15
