# The minesweeper

## How to play? 
Given to the player is a square grid consisting of "n x n" hidden cells. Any hidden cell contains one of the following:  
- A Mine  
- Blank cell  
- A number (say X) indicating that the cell has X mines in its neighborhood. Note that a blank cell could be represented by number “0”.  

The mines are randomly placed on the grid.  

## The rules of the game are as follows:  
- If the player chooses a cell that has a hidden mine, the game is over. Explode!  
- If the player chooses a cell that has a hidden number, then the spot is uncovered, and the number is now visible to the player.  
- If the player chooses a cell that doesn't have a mine or number, then ripple effect takes place (see section "Ripple effect" below) uncovering all the blanks in the neighborhood until either the grid boundary is reached or a number is reached along its path. The objective of the game is to identify, logically, all the mines on the grid. 

## Program Specifications: 
- To reduce the complexity of the program, let us fix the size of the grid to be “5x5” and let the number of mines on the grid be 5.  
- On the grid, the blank cells can be represented with a number 0; indicating that the cell has zero mines in its neighborhood. The neighborhood of a cell consists of all the cells that are immediately adjacent to the given cell horizontally, vertically or diagonally.  
- Program should have all error checks like:
  - If a user chooses a cell that’s not on the grid, report an error and ask the user for a valid cell. 
  - If a user gives non-integer inputs for the row and column positions, notify the user that the input is incorrect and prompt again. Any others that you could think of…  
  - If the player gives the position of a cell on the grid that’s already open, do nothing.  

## High Level Algorithm:  
- Create a class for the Minesweeper game. Within the class, create a "n x n" data structure to represent the grid. You will use a list of lists for this.  
- Randomly place the mines on the grid. For placing the mines, you could have a function called placeMines(). After that, get the counts for each non-mine cell on the grid. You could have a function called getCounts() for this. 

At this stage, the grid (“Actual Grid” below) is ready with the mines and numbers, and the player could start playing.  


### Initial State: 

H   H   H   H   H 

H   H   H   H   H 

H   H   H   H   H 

H   H   H   H   H 

H   H   H   H   H  


### Player View: 

0    1   1   H   H 

1   M   1   H   H 

H   H   H   H   H 

H   H   H   H   H 

H   H   H   H   H 


### Actual Grid: 

0    1    1    1    1  

1   M    1    2   M 

3    3    2    2   M 

M  M   1    1   1  

2    2    1    0    0 

 

- Display the grid in the form of the “Player View”, in the beginning it will all be H’s, and as the player uncovers cells you will update this view to reflect that, include row and column numbers to make it easier for the user to play.  
- Prompt the player for the position (row, column) on the grid that he/she wants to explore. Note the rows are 1-5 from top to bottom, the columns are 1-5 from left to right.  
- If the player hits a mine, give a message that a mine was hit, and the game is over. 
- If the player hits a number, just show the number.  
- If the player hits a blank, then show the ripple effect (see section "Ripple effect" below) 
- Repeat steps 3-7 until game is over (i.e. all the mine locations have been successfully located) or the player has lost.  
- Ask if the player would like to play again, if so continue, otherwise, exit. 

## Ripple effect:  
This is expected in your program: If the player chooses a blank cell on the grid, consider only the row and column to which the cell belongs. Starting from the cell, move horizontally and vertically away from the cell until you encounter a number or the edge of a grid, whichever comes first. If a number is encountered, it should be uncovered and then the ripple effect should stop. 
