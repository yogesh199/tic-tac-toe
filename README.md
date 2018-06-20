# tic-tac-toe
def player1or2():
    player = int(input('Select player 1 or 2: player: '))
    if player ==1:
        player1 = input('Select o or x: ')
        if player1 == 'o':
            player2 = 'x'
            print('player1 == o , player2 ==x')
            return ('o','x')
        else:
            player2 = 'o'
            print('player1 == x , player2 == o')
            return ('x','o')
    else:
        player ==2
        player2 = input('select o or x: ')
        if player2 =='o':
            player1 = 'x'
            print('player1 == x , player2 ==o')
            return ('x','o')
        else:
            player1 ='o'
            print('player1 == o , player2 == x')
            return ('o','x')
            
        
        
def preparingboard(board):
    print(board[7]+ '|'+board[8]+'|'+board[9])
    print('---')
    print(board[4]+ '|'+board[5]+'|'+board[6])
    print('---')
    print(board[1]+ '|'+board[2]+'|'+board[3])

    
    
def selectingwinner(board,mark):
    
    return ((board[1]==board[2]==board[3]==mark) or
    (board[4]==board[5]==board[6]==mark) or
    (board[7]==board[8]==board[9]==mark) or
    (board[1]==board[4]==board[7]==mark) or
    (board[2]==board[5]==board[8]==mark) or
    (board[3]==board[6]==board[9]==mark) or
    (board[1]==board[5]==board[9]==mark) or
    (board[3]==board[5]==board[7]==mark))
    
    #board prepared
    #teal selected
    #winning methon selected

    
    
def placemarker(board, mark, position):
    board[position] = mark        
            
    
            
def reply():
    return input("Play again? Enter Yes or No").lower().startswitch('y')

def spacecheck(board,position):
    return board[position] == ' '

def fullboardcheck(board):
    for i in range(1,10):
        if spacecheck(board,i):
            return False
    return True


import random 
def starter():
    
    if random.randint(0, 1) == 0:
        return 'player2'
    else:
        return 'player1'

    
turn = starter()
print(turn)


# game starts



while True:
    board = [' ']*10
    markx,marky = player1or2()
    
     
    turn = starter()
    print(turn + ' will go first')
    playgame = input('ready to play? y or n? ')
    
    if playgame.lower()[0] == 'y':
        gameon = True
    else:
        gameon = False
        
        
        
    while gameon:
        if turn == 'player1':
            preparingboard(board)
            position = int(input('player1 turn enter position: '))
            placemarker(board,markx,position)
            if selectingwinner(board,markx):
                preparingboard(board)
                print('player1 won the game')
                gameon = False
            else:
                if fullboardcheck(board):
                    preparingboard(board)
                    print('tie game')
                    gameon = False
                else:
                    turn = 'player2'
                
                
                
        elif turn == 'player2':
            preparingboard(board)
            position = int(input('player2 turn enter position: '))
            placemarker(board,marky,position)
            if selectingwinner(board,marky):
                preparingboard(board)
                print('player2 won the game')
                gameon = False
            else:
                if fullboardcheck(board):
                    preparingboard(board)
                    print('tie game')
                    gameon = False
                else:
                    turn = 'player1'                
                
                
if not reply():
    break

