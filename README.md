# Alpha-Beta-Adversarial-Search-with-Minimax-Pruning-for-Othello
## Othello Game:

![f362f3ba001858b28d8ad6a800728b8b_t](https://raw.githubusercontent.com/peyman-paknezhad/Alpha-Beta-Adversarial-Search-with-Minimax-Pruning-for-Othello/main/pic/othello.jpeg)

Othello, also known as Reversi, is a popular two-player board game played on an 8x8 grid. The game is played with discs, typically black on one side and white on the other. The objective of the game is to have the majority of your colored discs on the board at the end of the game. The game starts with four discs placed in a specific pattern in the center of the board. Players take turns placing their discs on empty squares, with the goal of flipping their opponent's discs to their own color by surrounding them in a straight line horizontally, vertically, or diagonally. A player must make a move if they have a valid move available, and if they cannot make a move, they pass their turn. The game ends when neither player can make a move, and the player with the most discs of their color on the board wins.

## Minimax Algorithm:
The minimax algorithm is a decision-making algorithm used in game theory and artificial intelligence to determine the optimal move for a player in a game. It is commonly used in games with a finite number of possible moves, such as Othello. The algorithm considers all possible moves that can be made by both players and evaluates the outcome of each move by assuming both players play optimally. The goal is to maximize the player's score while minimizing the opponent's score.

##The minimax algorithm works recursively, exploring the game tree by simulating all possible moves and their outcomes. Each node in the game tree represents a game state, and the algorithm assigns a value to each node based on the evaluation of that game state. The algorithm alternates between maximizing and minimizing the value at each level of the tree.

## Alpha-Beta Pruning:

![alpha beta](https://github.com/peyman-paknezhad/Alpha-Beta-Adversarial-Search-with-Minimax-Pruning-for-Othello/assets/102018763/ba4519a6-1247-487f-b32f-df3117d5beaf)

Alpha-beta pruning is an optimization technique used in conjunction with the minimax algorithm to reduce the number of nodes that need to be evaluated. It eliminates branches in the game tree that are guaranteed to be worse than previously evaluated branches, thereby reducing the search space and improving the algorithm's efficiency.

During the minimax search, the algorithm maintains two values: alpha and beta. The alpha value represents the best maximum score that the maximizing player has found so far, while the beta value represents the best minimum score that the minimizing player has found so far. As the search progresses, if the algorithm finds a move that leads to a lower score than the current alpha value (for the maximizing player) or a higher score than the current beta value (for the minimizing player), it can prune the remaining branches of that node because the opponent would not choose that path.

Alpha-beta pruning allows for significant reductions in the number of nodes that need to be evaluated, making the minimax algorithm more efficient and practical for games with large search spaces like Othello.

## implement
To implement adversarial search in this game, the beta-alpha with minimax limited-depth pruning technique has been used. This is because the number of possible game states in the game is approximately 3 to the power of 64, and implementing it without limitations and optimizations would be problematic. The branching factor of this game is around 10, and considering that we have a similar method to DFS search, even with optimization using alpha-beta pruning, the number of possible states starting from the white move, b(3m/4), would still be significant. To address this issue, we will use an evaluation function.

### evaluation function
The features used in the evaluation function include the total number of black pieces, the number of legal moves, the number of pieces in the last row and column, and the number of pieces in the corner of the board. Each feature has a coefficient based on its importance. The pieces in the corner have the highest weight, which is 10. These pieces do not change throughout the game and also restrict the opponent's moves, giving us the ability to change more of the opponent's pieces. The number of available moves has a weight of 1. The more possible moves there are, the better move we can select and influence the opponent's subsequent moves. The number of pieces in the last row and column is important because they are constrained from one side and have a lower probability of changing their color. These pieces have a weight of 0.1. The final factor is the total number of pieces. Although this factor is considered less significant towards the end of the game, during the game, it is highly variable, and a single move can have a significant impact on it. It has the minimum weight of 0.01.
