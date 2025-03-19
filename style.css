def evaluate(board):
    """Evaluates the Tic-Tac-Toe board for a winner."""
    # Check rows
    for row in board:
        if row[0] == row[1] == row[2] and row[0] != ' ':
            return 1 if row[0] == 'X' else -1

    # Check columns
    for col in range(3):
        if board[0][col] == board[1][col] == board[2][col] and board[0][col] != ' ':
            return 1 if board[0][col] == 'X' else -1

    # Check diagonals
    if board[0][0] == board[1][1] == board[2][2] and board[0][0] != ' ':
        return 1 if board[0][0] == 'X' else -1
    if board[0][2] == board[1][1] == board[2][0] and board[0][2] != ' ':
        return 1 if board[0][2] == 'X' else -1

    # Check for draw
    if all(' ' not in row for row in board):
        return 0  # Draw

    return None  # Game not over

def minimax(board, depth, is_maximizing):
    """Minimax algorithm for Tic-Tac-Toe."""
    result = evaluate(board)

    if result is not None:
        return result

    if is_maximizing:
        best_score = -float('inf')
        for i in range(3):
            for j in range(3):
                if board[i][j] == ' ':
                    board[i][j] = 'X'
                    score = minimax(board, depth + 1, False)
                    board[i][j] = ' '  # Undo the move
                    best_score = max(score, best_score)
        return best_score
    else:
        best_score = float('inf')
        for i in range(3):
            for j in range(3):
                if board[i][j] == ' ':
                    board[i][j] = 'O'
                    score = minimax(board, depth + 1, True)
                    board[i][j] = ' '  # Undo the move
                    best_score = min(score, best_score)
        return best_score

def find_best_move(board):
    """Finds the best move using the minimax algorithm."""
    best_move = None
    best_score = -float('inf')

    for i in range(3):
        for j in range(3):
            if board[i][j] == ' ':
                board[i][j] = 'X'
                score = minimax(board, 0, False) #Opponent's turn next.
                board[i][j] = ' '  # Undo the move

                if score > best_score:
                    best_score = score
                    best_move = (i, j)

    return best_move

def print_board(board):
    """Prints the Tic-Tac-Toe board."""
    for row in board:
        print(' | '.join(row))
        print('-' * 9)

def play_game():
    """Plays a game of Tic-Tac-Toe."""
    board = [[' ' for _ in range(3)] for _ in range(3)]
    player_turn = True  # True for X, False for O

    while True:
        print_board(board)
        result = evaluate(board)
        if result is not None:
            if result == 1:
                print("X wins!")
            elif result == -1:
                print("O wins!")
            else:
                print("It's a draw!")
            break

        if player_turn:
            while True:
                try:
                    row = int(input("Enter row (0, 1, 2): "))
                    col = int(input("Enter column (0, 1, 2): "))
                    if 0 <= row <= 2 and 0 <= col <= 2 and board[row][col] == ' ':
                        board[row][col] = 'X'
                        break
                    else:
                        print("Invalid move. Try again.")
                except ValueError:
                    print("Invalid input. Please enter numbers.")
        else:
            print("Computer's turn (O):")
            best_move = find_best_move(board)
            if best_move:
                row, col = best_move
                board[row][col] = 'O'

        player_turn = not player_turn

if __name__ == "__main__":
    play_game()
