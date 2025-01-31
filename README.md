# TicTaeToe
# Function to print the Tic-Tac-Toe board
def print_board(board):
    for i in range(3):
        print(' | '.join(board[i]))
        if i < 2:
            print('-' * 5)
def check_win(board, player):
    for i in range(3):
        if all([spot == player for spot in board[i]]):  # Check row
            return True
        if all([board[j][i] == player for j in range(3)]):  # Check column
            return True
    if all([board[i][i] == player for i in range(3)]):  # Check diagonal \
        return True
    if all([board[i][2-i] == player for i in range(3)]):  # Check diagonal /
        return True
    return False
def board_full(board):
    return all([spot != ' ' for row in board for spot in row])
def tic_tac_toe():
    board = [[' ' for _ in range(3)] for _ in range(3)]  # Create an empty board
    current_player = 'X'  # X starts first

    while True:
        print_board(board)
        print(f"Player {current_player}'s turn:")
        row = int(input("Enter row (0, 1, 2): "))
        col = int(input("Enter column (0, 1, 2): "))
        if board[row][col] != ' ':
            print("This spot is already taken, try again!")
            continue
        board[row][col] = current_player
        if check_win(board, current_player):
            print_board(board)
            print(f"Player {current_player} wins!")
            break
        if board_full(board):
            print_board(board)
            print("It's a draw!")
            break
        current_player = 'O' if current_player == 'X' else 'X'

# Start the game
tic_tac_toe()
