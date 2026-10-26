# StarTrek-Classic
StarTrek Classic

Play it here:
https://vpelss.github.io/StarTrek-Classic/

also here: https://codepen.io/vpelss/pen/LYNgwqK

This is a line for line conversion from one of the many 70’s BASIC version of Star Trek into JavaScript.

I love finding projects I am passionate about.
A friend was showing off all his Star Trek games which reminded me of one of the very first computer Star Trek games.  I remember playing it on the PET computer. It was written in BASIC.


[https://en.wikipedia.org/wiki/Star_Trek_(1971_video_game)](https://en.wikipedia.org/wiki/Star_Trek_(1971_video_game))

https://www.youtube.com/watch?v=e6f9_9kzuzk

I was surprised to discover almost no (good) ports of the code to JavaScript. JavaScript would allow it to run on any pc.

I heard a voice in my head say, 'Thou shalt do this'.

This is a faithful conversion of a StarTrek BASIC program from the early 70's into JavaScript. (Disclaimer: I made the universe closed, so you can't fly out of the 8x8 quadrants.)
Yes, it could have been rewritten from scratch, but I wanted to be as faithful to the original as possible

Challenges:

BASIC pauses at INPUT command. It awaits user input then continues.
JavaScript cannot pause.
The DOM can only update when the code has completed.
With JS, text input can only come from a text box event, which starts the JS running code again.

To simulate / mimic the BASIC INPUT command, we set a 'nextLine' variable. 'nextLine' indicates where the code should resume after a user input text event. 
After all JS input text events storeCommand() is called. 
It sets the text input to a global variable then calls switch_board(nextLine) to resume our code and process this input.
For all BASIC code after BASIC INPUT commands, I have created functions called Line1270() (etc). 
The JS code in Line1270() is equivalent to what would have been at basic line 1270, right after the previous BASIC INPUT command. 
These functions are called by switch_board(nextLine).

The BASIC GOTO command is a menace. It makes it easy to write poorly structured code.
In some cases, where a GOTO was called from only one line, the GOTO could be removed and converted to inline code.
In cases where the GOTO was called from multiple lines I had to create GOTO functions. eg: GOTO6543()

I soon needed to create multidimensional arrays. Basic uses a simple G= DIM[7,9,3] format creating an array called G, with dimensions of 7x9x3. JavaScript, oddly enough, does not have an easy, built in, way to create an array like BASIC. So I had to code a JavaScript version of DIM using a recursive function. 

-------------------------------

some var and function references

D - damage array

FND(D) : distance

K[kingon1-3][x,y,damage]

S1,S2 sector loc

Q1,Q2 quadrant

Line1270() : command loop

Line1410() : course

Line1460() : warp, check damage , check E check S, if K3, fight

Line1610() : needed to keep goto flow working

Line2330() : long range sensors

GOSUB4120() : short range

GOSUB5820() : instructions

GOSUB5380() : random spot chosen in quadrant that is empty

GOSUB5680() : STRING COMPARISON IN QUADRANT ARRAY

GOSUB5510() : insert string in quadrant

GOSUB3790() : klingons attack

GOTO3920() : lose scenarios : was goto

