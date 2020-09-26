# FlappyBird

This is a program coded in C that runs a Flappy Bird side-scrolling game on two LED 8x8 matrix displays. The program runs on a computer that is interfaced with the matrix displays through the computer's parallel port. The program handles the game logic and outputs the appropriate display data to the parallel port. The output to the parallel port is then converted into signals that can be used to control the displays through the use of 8 bit decoder chips and PNP transistors.

Here is an image of the hardware used to interface the matrix displays with the computer's parallel port.

![flappybird](https://i.imgur.com/cWMs4aL.jpg)

The objective of the game is to fly your "bird", or in this case, a pixel on the matrix, through a series of pillars without crashing.

The program uses a two dimensional array to store data for five possible pillars, each of which has a gap of 4 pixels for the bird to fly through. The program randomly selects pillars from one of these possibilities, places it on the far right side, and moves it to the left after every game tick.

The bird is positioned on the far left side and is controlled by the user - pressing 'w' causes the bird to move upward. The user must maneuver the bird through the pillar without crashing. If a collision is detected, the game is over. If the user succeeds, a new pillar is generated on the far right side and begins moving left.

The game is displayed using a technique called multiplexing. Since it is impossible to directly address 128 individual pixels through the parallel port, the program displays one row at a time, and cycles through the rows extremely quickly to give the illusion that multiple rows are lit up at the same time. The program uses a double loop to accomplish this.

Eight bits of the parallel port output are used to represent the pattern to be displayed on each 8 pixel row. The remaining four bits of the parallel port output are used to represent which of the 16 rows is to be illuminated. The four bit number is converted into one of 16 unique outputs via the decoder chips.

As a final note, here is the schematic for the interface circuit.

![schematic](https://i.imgur.com/XKkXI2w.png)
