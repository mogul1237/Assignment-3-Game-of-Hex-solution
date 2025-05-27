# Assignment-3-Game-of-Hex-solution

Download Here: [Assignment 3: Game of Hex solution](https://jarviscodinghub.com/assignment/assignment-3-game-of-hex-solution/)

For Custom/Original Work email jarviscodinghub@gmail.com/whatsapp +1(541)423-7793

In this assignment, you will write a program using arrays to play a game called Hex (六貫棋), which is
a two-player game played on an initially empty diamond game board, with a typical size 11×11. The
two players have some chess pieces in two different colors. They take turns placing their pieces on
empty cells of the board. The goal of the first player is to form a chain of his/her pieces connecting
the left and right border of the board, while the goal of the second player is to form a chain of
his/her pieces connecting the top and bottom border of the board. Each of the four corners belongs
to both of its adjacent borders. The player who first achieves his/her goal is the winner. This game
always has a winner; it never ends in a draw.
We shall call the first and second players ‘O’ and ‘X’ respectively. Figure 1 shows an example game
board. The character ‘.’ denotes an empty cell. The rows and columns are named in numbers (0–10)
and letters (A–K) respectively. Each cell has at most six neighbors. For example, cell F3 has neighbors
F2, G2, E3, G3, E4, and F4. (E2 and G4 are not neighbors of F3.)
A B C D E F G H I J K
0 O X . X . . . . . . .
1 . . . . . X . . . . .
2 X . O . . . . . O X .
3 . . . . . O . . . O X
4 . X . . . . . . . . .
5 O X X . O . . X . . O
6 O . . . . . . . . X O
7 . . . . . . . . . . .
8 . O . . . . . X . . X
9 . X . O . . . O . . .
10 O . X . . . . . . O .
Figure 1: An Example Game Board
Program Specification
Game Board
You can use a two-dimensional array of char to represent the game board.
const int N = 11;
……
char board[N][N];
The array elements board[0][0], board[0][10], board[10][0], and board[10][10] denote
four corner cells A0, K0, A10, and K10 respectively. Note that among the eight neighbors of an array
element (not on the borders), only six of them are true neighbors of the corresponding cell location.
For example, E2 (board[2][4]) and G4 (board[4][6]) are not neighbors of F3 (board[3][5]).

Game Flow
 Starting with an empty board, players O and X make moves alternately. Player O makes the first
move.
 In each move, you should prompt the player to enter two inputs denoting the cell location to be
placed. You can assume that the first input is always a character and the second input is always
an integer.
 A user input is invalid if: (a) it is not a proper cell location (i.e., rows 0–10 and columns A–K, big
letters only), or (b) the input location is already occupied.
 You should warn the player about invalid inputs and prompt the same player to enter again until
a valid input is entered.
 When a player has formed a winning chain of pieces (left-right for player O and top-bottom for
player X), you should print a winning message and the program should then terminate.
Hint for Checking Winning Chain
After a player has made a move, you have to check whether (s)he has made a winning chain of
pieces. To do so, you may need another two-dimensional array (of type bool) to store whether each
cell location is “reachable” from the input location. If there is a cell on one side of the board
reachable from the input location, and another cell on the opposite side also reachable from the
input location, then the player has formed a winning chain. Figure 2 illustrates the idea for player O.
After a player placed a piece on the board, the whole reachability array is false except the input
position, which is true. Then, you incrementally expand the reachability (set true) to the neighbors
of the input position, to the neighbors of the neighbors of the input position, to the neighbors of the
neighbors of the neighbors of the input position, and so on. A player has formed a winning chain if
you identify that the two corresponding borders are reached. Your challenge is to write code to
correctly compute the two-dimensional reachability array.
b b
o o
r O r
d O O d
e e
r r
Figure 2: A Winning Chain of Pieces for Player O
Other Notes
 You are not allowed to use global variables in your program. (That is, you cannot declare any
variables outside any functions). Nonetheless, const ones (e.g., N) does not count.
 Your program should be decomposed into at least four functions (including main()). At least
two functions should have array parameter(s).
Program Output
The following shows some sample output of the program. The bold blue text is user input and the
other text is the program output. You can try the provided sample program for other input. Your
program output should be exactly the same as the sample program (i.e., same text, same symbols,
same letter case, same number of spaces, etc.). Otherwise, it will be considered as wrong, even if
you have computed the correct result.
reachable reachable

A B C D E F G H I J K
0 . . . . . . . . . . .
1 . . . . . . . . . . .
2 . . . . . . . . . . .
3 . . . . . . . . . . .
4 . . . . . . . . . . .
5 . . . . . . . . . . .
6 . . . . . . . . . . .
7 . . . . . . . . . . .
8 . . . . . . . . . . .
9 . . . . . . . . . . .
10 . . . . . . . . . . .
Player O, make your move: A 0↵
A B C D E F G H I J K
0 O . . . . . . . . . .
1 . . . . . . . . . . .
2 . . . . . . . . . . .
3 . . . . . . . . . . .
4 . . . . . . . . . . .
5 . . . . . . . . . . .
6 . . . . . . . . . . .
7 . . . . . . . . . . .
8 . . . . . . . . . . .
9 . . . . . . . . . . .
10 . . . . . . . . . . .
Player X, make your move: B 11↵
Invalid move. Enter again!
Player X, make your move: M 4↵
Invalid move. Enter again!
Player X, make your move: A 0↵
Invalid move. Enter again!
Player X, make your move: b 9↵
Invalid move. Enter again!
Player X, make your move: B 9↵
A B C D E F G H I J K
0 O . . . . . . . . . .
1 . . . . . . . . . . .
2 . . . . . . . . . . .
3 . . . . . . . . . . .
4 . . . . . . . . . . .
5 . . . . . . . . . . .
6 . . . . . . . . . . .
7 . . . . . . . . . . .
8 . . . . . . . . . . .
9 . X . . . . . . . . .
10 . . . . . . . . . . .
.
. (Many moves skipped to save space. Full version available in Blackboard.)
.
A B C D E F G H I J K
0 O X O O X O O X . X X
1 O O X X O X O X X X O
2 X O X O X X O X X O X

3 O O O X O O O . O O O
4 X O O O . X X X O X X
5 X . X O O O O X . O X
6 O O X O O X O O . O O
7 . X . X X O O O X O X
8 X X X O X X X O X O O
9 X X X X X O O O X X X
10 O X X O X X O O X O O
Player X, make your move: I 0↵
A B C D E F G H I J K
0 O X O O X O O X X X X
1 O O X X O X O X X X O
2 X O X O X X O X X O X
3 O O O X O O O . O O O
4 X O O O . X X X O X X
5 X . X O O O O X . O X
6 O O X O O X O O . O O
7 . X . X X O O O X O X
8 X X X O X X X O X O O
9 X X X X X O O O X X X
10 O X X O X X O O X O O
Player O, make your move: I 5↵
A B C D E F G H I J K
0 O X O O X O O X X X X
1 O O X X O X O X X X O
2 X O X O X X O X X O X
3 O O O X O O O . O O O
4 X O O O . X X X O X X
5 X . X O O O O X O O X
6 O O X O O X O O . O O
7 . X . X X O O O X O X
8 X X X O X X X O X O O
9 X X X X X O O O X X X
10 O X X O X X O O X O O
Player O wins!
Submission and Marking
 Your program file name should be hex.cpp. Submit the file in Blackboard
(https://elearn.cuhk.edu.hk/).
 Insert your name, student ID, and e-mail address as comments at the beginning of your source
file.
 Besides the above information, your program should further include suitable comments as
documentation.
 You can submit your assignment multiple times. Only the latest submission counts.
 Your program should be free of compilation errors and warnings.
 Plagiarism is strictly monitored and heavily punished if proven. Lending your work to others is
subjected to the same penalty as the copier.
