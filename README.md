# SnAKE-GAME--USING-C-LANGUAGE
A project , we have already seen and played in our childhood . Made it by using only C programming language.
You can play game by running it in terminal. 1st of all run the code then click on terminal to give input for navigation.
For navigation you can use different keys like
a→ to move left
d→ to move right
s→ to move down
w→ to move up
x→ to end game

SNAKE GAME EXPLANATION:-
----------------------------------------------------------------
1. Global Variables:-
 ------------------------
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
-------------------
2. setup():-
-------------------
Used to define initial position of food and the head of the snake. Here we used
rand() function to generate random numbers to show different position of
food.
--------------------
3. draw():-
--------------------
Used to draw the boundary, the head & tail of the snake and the food in every
frame of the game. Every time to display the new frame, first it will clear the
previous frame on the terminal.
--------------------
4. direction():-
 --------------------
Used to define the direction of the snake. Here we use kbhit() function of
conio.h library. This function will track whether the keyboard keys were hit or
not. If we hit the key then It will take a character input and change the value of
direct according to the input. The value of direct is further used in logic()
function to give direction to the sleep. This function will also define the end of
the game, if we hit the x character on the keyboard, then our game will end.
-----------------------
5. logic():-
------------------------
This function will control the whole logic of the game. The direction & the
movement of the snake, changing the position of every tail in each frame,
adding a new tail to the snake, display new position of the food, deciding the
end of the game, every thing is controlled by this function.
-----------------------
6. main():-
------------------------
This is the main function of the whole game. It will Control how many times the
game will run. When value of end is zero, the game will stop.

---------------------------
7. FULL CODE:-
----------------------------
#include<stdio.h>
#include<string.h>
#include<math.h>
#include<limits.h>
#include<stdlib.h>
#include<conio.h>dd

int width=50,height=20,x,y,fx,fy,direct,score=0,end=0,piece=0;
int tx[100],ty[100],p;

void setup(){
    x=width/2;
    y=height/2;
    fx=rand()%47+2;
    fy=rand()%17+2;
}

void logic(){
    for(int i=piece-1;i>0;i--){
        tx[i]=tx[i-1];
        ty[i]=ty[i-1];
        for(int j=i-2;j>0;j--) if(tx[j]==tx[i] && ty[j]==ty[i]) end=1;
        for(int j=i+1;j<piece-1;j++) if(tx[j]==tx[i] && ty[j]==ty[i]) end=1;
    }
    tx[0]=x;
    ty[0]=y;
    switch(direct){
        case 1:{
            y--;
            break;
        }
        case 2:{
            x++;
            break;
        }
        case 3:{
            y++;
            break;
        }
        case 4:{
            x--;
            break;
        }
    }

    if(x==fx && y==fy){
        fx=rand()%47+2;
        fy=rand()%17+2;
        piece++;
        score++;
    }

    p=direct;

    if(x==1 || x==width || y==1 || y==height) end=1;
}

void direction(){
    if(kbhit()){
        switch(getch()){
            case 'w':{
                if(p!=3) direct=1;
                break;
            }
            case 'd':{
                if(p!=4) direct=2;
                break;
            }
            case 's':{
                if(p!=1) direct=3;
                break;
            }
            case 'a':{
                if(p!=2) direct=4;
                break;
            }
            case 'x':{
                end=1;
                break;
            }
        }
    }
}

void draw(){
    system("cls");
    for(int j=1;j<=height;j++){
        for(int i=1;i<=width;i++){
            if(j==height) printf("%c",-33);
            else if(i==1 || i==width || j==1) printf("%c",-37);
            else if(j==y && i==x) printf("%c",2);
            else if(i==fx && j==fy) printf("%c",-2);
            else{
                int ch=0;
                for(int k=1;k<=piece;k++){
                    if(i==tx[k-1] && j==ty[k-1]){
                        printf(".");
                        ch++;
                    }
                }
                if(ch==0) printf(" ");
            }
        }
        printf("\n");
    }
    printf("Score : %d",score);
}

int main(){
    setup();
    while(end==0){
        direction();
        draw();
        logic();
    }
    return 0;
} 
