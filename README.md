# ==============================================================================
# Project Title : Console-Based Tic-Tac-Toe Game
# Author        : Muhammad Abdullah Haroon(2025-MC-01)
# Department    : Mechatronics and Control Engineering
# Institute     : University of Engineering and Technology (UET), Lahore
# Date          : July 2026
#
# Description
# ------------------------------------------------------------------------------
# This project is a Python-based console Tic-Tac-Toe game that simulates the
# classic two-player game. The application allows users to play against another
# player or a computer opponent.
#
# The program uses a 2D list to represent the game board and implements core
# programming concepts including functions, conditional logic, loops, input
# validation, and game state management.
#
# Features
# ------------------------------------------------------------------------------
# - Player vs Player mode
# - Player vs Computer mode
# - Interactive console-based gameplay
# - Input validation for user moves
# - Automatic win detection
# - Draw detection
# - Random move selection for computer opponent
#
# Technologies Used
# ------------------------------------------------------------------------------
# - Python 3
# - Built-in random module
#
# Purpose
# ------------------------------------------------------------------------------
# This project was developed to strengthen Python programming fundamentals and
# improve problem-solving skills through the implementation of a complete
# interactive game.
#
# ==============================================================================
import random
Board = [
    [0,1,2],
    [3,4,5],
    [6,7,8]
]
def DisplayBoard():
    print(f'{Board[0][0]:>2} |{Board[0][1]:>2} |{Board[0][2]:>2}')
    print(f'-'*10)
    print(f'{Board[1][0]:>2} |{Board[1][1]:>2} |{Board[1][2]:>2}')
    print(f'-'*10)
    print(f'{Board[2][0]:>2} |{Board[2][1]:>2} |{Board[2][2]:>2}')
def Turn(mark):
    while True:
        P1 = input("Enter the slot of your choice(0-8) : ")
        if not P1.isdigit():
            print("Wrong Choice")
            continue
        P1 = int(P1)
        if P1 not in range(0,9):
            print("Wrong Choice")
            continue
        row = P1//3
        col = P1%3
        if(Board[row][col] == P1):
            Board[row][col] = mark
            break
        else:
            print("Slot Already Filled")
def ComputerTurn():
    """
    Generates a random valid move for computer player.
    """
    while True:
        P1 = random.randint(0,8)
        row = P1//3
        col = P1%3
        if(Board[row][col] == P1):
            Board[row][col] = 'O'
            break
def CheckWin():
    if(Board[0][0]==Board[0][1]==Board[0][2] == 'X' or 
       Board[1][0]==Board[1][1]==Board[1][2] == 'X' or
       Board[2][0]==Board[2][1]==Board[2][2] =='X' or
       Board[0][0]==Board[1][0]==Board[2][0] =='X' or
       Board[0][1]==Board[1][1]==Board[2][1] =='X' or
       Board[0][2]==Board[1][2]==Board[2][2] =='X' or
       Board[0][0]==Board[1][1]==Board[2][2] =='X' or
       Board[0][2]==Board[1][1]==Board[2][0] =='X'
       ):
        return 1
    elif(Board[0][0]==Board[0][1]==Board[0][2] == 'O' or 
       Board[1][0]==Board[1][1]==Board[1][2] == 'O' or
       Board[2][0]==Board[2][1]==Board[2][2] =='O' or
       Board[0][0]==Board[1][0]==Board[2][0] =='O' or
       Board[0][1]==Board[1][1]==Board[2][1] =='O' or
       Board[0][2]==Board[1][2]==Board[2][2] =='O' or
       Board[0][0]==Board[1][1]==Board[2][2] =='O' or
       Board[0][2]==Board[1][1]==Board[2][0] =='O'
       ):
        return 2
    else:
        for i in Board:
            for j in i:
                if j in range(0,9):
                    return -1
        return 0
while True:
    option = input("Do you want to play With :\n1. Computer\n2. Friend\nEnter your choice :  ")
    if(option == '2'):
        plr1 = input("Enter the name of Player-1 : ")
        plr2 = input("Enter the name of Player-2 : ")
        break
    if(option == '1'):
        plr1 = input("Enter your name : ")
        plr2 = 'Computer'
        break
DisplayBoard()
while True:
    print(f"{plr1}'s Turn")
    Turn("X")
    DisplayBoard()
    if(CheckWin()==1):
        print(f'{plr1} Won')
        break
    elif(CheckWin()==0):
        print('Game Ended in Draw')
        break
    if(option == '2'):
        print(f"{plr2}'s Turn")
        Turn("O")
    if(option == '1'):
        print(f"{plr2}'s Turn")
        ComputerTurn()
    DisplayBoard()
    if(CheckWin()==2):
        print(f'{plr2} Won')
        break
    elif(CheckWin()==0):
        print('Game Ended in Draw')
        break

