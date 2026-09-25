# ==============================================================================
# WHAT IS TIC-TAC-TOE?
# Tic-Tac-Toe is a simple grid game played between two players: X and 0.
# The game is played on a 3x3 grid containing 9 spaces in total.
#
# HOW TO PLAY:
# 1. The game starts with an empty board showing numbers from 0 to 8.
# 2. Players take turns choosing a number to place their mark (X or 0).
# 3. Type the number of the grid space you want and press Enter.
#
# RULES:
# 1. Only one mark can be placed in a single grid square.
# 2. The first player to get 3 of their marks in a straight row, column, 
#    or diagonal line wins the game.
# 3. If all 9 squares are filled and no player has 3 marks in a line, 
#    the game ends in a tie.
# ==============================================================================

# welcome to tictactoe game

# This function adds three numbers together to see if a player has won
def sum(a, b, c):
    return a + b + c

# This function displays the current state of the game board
def printboard(xstate, ystate):
    # Check what should be printed at each position (0 to 8)
    # If X played there, show 'X'. If 0 played there, show '0'. Otherwise, show the position number.
    zero = 'X' if xstate[0] else ('0' if ystate[0] else 0)
    one = 'X' if xstate[1] else ('0' if ystate[1] else 1)
    two = 'X' if xstate[2] else ('0' if ystate[2] else 2)
    three = 'X' if xstate[3] else ('0' if ystate[3] else 3)
    four = 'X' if xstate[4] else ('0' if ystate[4] else 4)
    five = 'X' if xstate[5] else ('0' if ystate[5] else 5)
    six = 'X' if xstate[6] else ('0' if ystate[6] else 6)
    seven = 'X' if xstate[7] else ('0' if ystate[7] else 7)
    eight = 'X' if xstate[8] else ('0' if ystate[8] else 8)
    
    # Print the actual grid structure on the screen
    print(f" {zero} | {one} | {two} ")
    print("---|---|---")
    print(f" {three} | {four} | {five} ")
    print("---|---|---")
    print(f" {six} | {seven} | {eight} ")

# This function checks if anyone has won the game yet
def checkwin(xstate, ystate):
    # These are all the combinations of 3 positions that make a win
    wins = [, [3, 4, 5], [6, 7, 8], # Rows, [1, 4, 7], [2, 5, 8], # Columns, [2, 4, 6]             # Diagonals
    ]
    
    # Loop through each winning combination
    for win in wins:
        # Check if X has 3 marks in a line (sum equals 3)
        if sum(xstate[win[0]], xstate[win[1]], xstate[win[2]]) == 3:
            print("X won the match")
            return 1
        # Check if 0 has 3 marks in a line (sum equals 3)
        if sum(ystate[win[0]], ystate[win[1]], ystate[win[2]]) == 3:
            print("0 won the match")
            return 0
            
    # Return -1 if no one has won yet
    return -1

# This is where the main game loop runs
if __name__ == "__main__":
    # Create empty tracks for X and 0 movements (0 means empty, 1 means occupied)
    xstate = [0, 0, 0, 0, 0, 0, 0, 0, 0]
    ystate = [0, 0, 0, 0, 0, 0, 0, 0, 0]
    print("welcome to tic tac toe game")
    
    # turn = 1 means it is X's turn, turn = 0 means it is 0's turn
    turn = 1
    
    # Keep the game running continuously
    while True:
        # Show the updated board to the players
        printboard(xstate, ystate)
        
        # Take input from the current player
        if (turn == 1):
            print("X chance")
            value = int(input("enter a number from (0-8): "))
            xstate[value] = 1 # Mark the position for X
        else:
            print("0 chance")
            value = int(input("enter number (0-8): "))
            ystate[value] = 1 # Mark the position for 0
            
        # Check if the last move won the game
        cwin = checkwin(xstate, ystate)
        if (cwin != -1):
            printboard(xstate, ystate) # Show the final board
            print("game over")
            break # Stop the loop and end the game
            
        # Switch the turn to the other player (1 becomes 0, 0 becomes 1)
        turn = 1 - turn
