# Energy Games Experiment

## Technical Notes
-   Game boards HTML layout is generated from the HAML, Ruby equations are used to quickly set up figures on board. See .haml for the structure
-   Stylesheet is generated by the LESS preprocessor, please see .less files for the source code.
-   Bootstrap 3.2.0 is used here. Though there is no real need for it here, except for the grid and media queries it provides. Bootstrap selector naming conventions are used here.
-   jQuery and Bootstrap JavaScript is not required by this example and therefore not plugged.
-   Tested to work in current WebKit browsers, may fail in Internet Explorer. By the way, did you know Microsoft announced they are going to rename Internet Explorer because everybody hates it's early versions?

## Developers Guide
-   The same person can play figures of different color. Current Player figures are starting at A1 (on the bottom).
-   Board figures are descendants of the board squares, thus, current layout implementation makes movement transitions from one square to another hardly possible.

### Board layout
- Each game has a .game class.
- Game board design and corresponding figures design is set up by adding a class with  .chess, .checkers, .othello to the .game. You are encouraged to attach game logic to the corresponding class name either.

### Game Squares and Figures
Board’s squares coordinates are the same as on a chess board, through A1 to H8 (8 is a top row). The "sq_" prefix is used on squares, for example .sq_G4 for G4.
Game figures belong to either Player 1 or Player 2 and reside inside the corresponding .sq. Take a look at the pseudo-code jQuery selectors, explaining what is expected in the DOM:
-   $('.chess .sq_G6 > .ch-player1.ch-rook') — This is a Rook figure of the Player 1, residing on G6 square in Chess game.
-   $('.othello .sq_A1 > .ch-player2') — Player’s 2 figure occupying A1 square in Othello game.

### Activating a Game
To activate a game on a current player’s turn, add .active class to the .game and change the copy of .game-player. Please note that current player can play as Player 1 or Player 2.

### Game Score & Captured Pieces
The .game-score layout is determined by .game type. It is holding the .game-score-player1 and .game-score-player2 as well as more details: .captured-pieces and .player-score.

### Winning, Loosing, Whatever
After the game is won or lost (or draw, check, checkmate, etc), you should add a notification classes, which indicate the game outcome related to Player 1 and a text. Notification classes supported: success, failure, info.
NB: Please do not use text longer than 12 characters including spaces and punctuation.

## Suggestions to UI/UX Team
-   I would suggest adding more game controls i.e. Skip Turn, Show Threats, Show Hints etc.
-   Name of the person whose turn it is to play should be more subtle if it is not the Current Player.
-   Captured items colors should be related to the Current Player, Player 1 captures Player’s 2 Figures, thus colors should be inverted on wireframe.