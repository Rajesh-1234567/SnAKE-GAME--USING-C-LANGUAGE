SNAKE GAME EXPLANATION
---------------------------------------------
1. Global Variables:-
-----------------------
1st we have defined some global variables,
width= width of the boundary
height= height of the boundary
x= to define X coordinate of the head of the snake
y= to define Y coordinate of the head of the snake
fx= coordinate of the food
fy= coordinate of the food
direct= to define direction of the snake
score= to define score
end= to indicate ending of the game
piece= To show number of food taken
tx[100]= to store X coordinate of every tail
ty[100]= to store Y coordinate of every tail
p= to store the previous direction of the snake
-------------------------
2. setup():-
---------------------------
Used to define initial position of food and the head of the snake. Here we used
rand() function to generate random numbers to show different position of
food.
-----------------
4. draw():-
------------------
Used to draw the boundary, the head & tail of the snake and the food in every
frame of the game. Every time to display the new frame, first it will clear the
previous frame on the terminal.
---------------------
6. direction():-
----------------------
Used to define the direction of the snake. Here we use kbhit() function of
conio.h library. This function will track whether the keyboard keys were hit or
not. If we hit the key then It will take a character input and change the value of
direct according to the input. The value of direct is further used in logic()
function to give direction to the sleep. This function will also define the end of
the game, if we hit the x character on the keyboard, then our game will end.
-----------------------
8. logic():-
-----------------------
This function will control the whole logic of the game. The direction & the
movement of the snake, changing the position of every tail in each frame,
adding a new tail to the snake, display new position of the food, deciding the
end of the game, every thing is controlled by this function.
------------------------
10. main():-
--------------------------
This is the main function of the whole game. It will Control how many times the
game will run. When value of end is zero, the game will stop.
