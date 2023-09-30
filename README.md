# Tic-tac-toe-Game

Welcome to the Tic-Tac-Toe Game repository! This is a fun and interactive Python-based implementation of the classic Tic-Tac-Toe game.
This game is a two-player game, here I have coded for one person can play with a computer. 


import random
rows=['']*10
computer,human='x','o'

def display_board(row):
    
    print(f'  {row[0]}  |  {row[1]}  |  {row[2]}  ')
    print(f'  -------------')
    print(f'  {row[3]}  |  {row[4]}  |  {row[5]}  ')
    print(f'  -------------')
    print(f'  {row[6]}  |  {row[7]}  |  {row[8]}  ')

def check_wins():
    if rows[0]==rows[1]==rows[2] and rows[0]!='':
        return True
    elif rows[3]==rows[4]==rows[5] and rows[3]!='':
        return True
    elif rows[6]==rows[7]==rows[8] and rows[6]!='':
        return True
    elif rows[0]==rows[3]==rows[6] and rows[0]!='':
        return True
    elif rows[1]==rows[4]==rows[7] and rows[1]!='':
        return True
    elif rows[2]==rows[5]==rows[8] and rows[2]!='':
        return True
    elif rows[2]==rows[4]==rows[6] and rows[2]!='':
        return True
    elif rows[0]==rows[4]==rows[8] and rows[0]!='':
        return True
    else:
        return False

def is_available(pos):
    return True if rows[pos]=='' else False
        
def check_draw():
    if rows.count('')<1:
        return True
    else:
        return False


def insert(letter,pos):
    if is_available(pos):
        rows[pos]=letter
        print('\n'*100)
        display_board(rows)
        if check_wins():
            if letter=='x':
                print('computer wins')
                exit()
            else:
                print('human wins')
                exit()
        elif check_draw():
            print('game draw')
            exit()
    else:
        if letter=='o':
            pos=int(input('not free , choose another position'))
        else:
            pos=random.randint(1,9)
        check_draw()
        insert(letter,pos)

def computer_move(letter):
    pos=random.randint(1,9)
    insert(letter,pos)

def human_move(letter):
    pos=int(input('enter the position to insert:  '))
    insert(letter,pos)
    
        #Main loop

while not check_wins():
    display_board(rows)
    computer_move(computer)
    human_move(human)


