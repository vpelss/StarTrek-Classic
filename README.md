# StarTrek-Classic
StarTrek Classic

Play it here:
https://www.somewhereincanada.com/games/StarTrek_Classic/

This is a line for line conversion from one of the many 70’s BASIC version of Star Trek into JavaScript.

I love finding projects I am passionate about.
A friend was showing off all his Star Trek games which reminded me of one of the very first computer Star Trek games.  I remember playing it on the PET computer. It was written in BASIC.

https//:en.wikipedia.org/wiki/Star_Trek_(1971_video_game)

https://www.youtube.com/watch?v=e6f9_9kzuzk

I was surprised to discover almost no (good) ports of the code to JavaScript. JavaScript would allow it to run on any pc.

I heard a voice in my head say, 'Thou shalt do this'.

This is a faithful conversion of a StarTrek BASIC program from the early 70's into JavaScript. (Disclaimer: I made the universe closed, so you can't fly out of the 8x8 quadrants. Sue me.)
Yes, it could have been rewritten from scratch, but I wanted to be as faithful to the original as possible

Challenges:

BASIC pauses at INPUT command. It awaits user input then continues.
JavaScript cannot pause.
The DOM can only update when the code has completed.
Input can only come from a text box event, which starts the JS running code again.

To simulate / mimic the BASIC INPUT command, we end our code in JS just before the BASIC input code while also setting a 'nextLine' variable. var 'nextLine' indicates where the code should resume after a user input event
nextLine = 1270; return; (or equivalent) accomplishes this
A user input event will store the user input in a variable 'globalComandStorage'. Then we call the function switch_board() which looks at nextLine and then calls function Line'nextLine'()
Code runs again until we require user input

The BASIC GOTO command is a menace. It makes it easy to write poorly structured code.
In some cases, I just restructured the code, in others, I did not.
GOTO can be simulated with something similar to GOTO6543(); return;
Eventually we will come to an INPUT command.
As stated before, to simulate INPUT, we return from and stop all JS code.
If there is a big call stack, because of our many GOTOXXXX calls,
all the return; commands placed after our GOTOXXXX calls will clean the call stack

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

