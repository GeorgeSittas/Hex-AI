# Hex
Goal for this project is to make the board game [Hex](https://en.wikipedia.org/wiki/Hex_(board_game)) and a
competitive [rational agent](https://en.wikipedia.org/wiki/Rational_agent) that can play it, using C.<br/>
The game window looks like this:

![](https://i.imgur.com/ybZ5tGg.png)

### Usage
The following command line options are available during the compilation phase:

- \-n \<size\> : Sets the grid size to 4 ≤ \<size\> ≤ 26 (default grid size: 11)

- \-d \<difficulty\> : Sets the game difficulty to 1 ≤ \<difficulty\> ≤ N², where N is the grid size
(default difficulty: 1)

- \-b : Sets the user's colour to black, so he makes the second move

- \-s : Activates the [swap rule](https://www.hexwiki.net/index.php/Swap_rule)

#### Starting the game
##### 1) with default parameters
```
cd src
make play
```
##### 2) with user-specified parameters
```
cd src
make
./hex <parameter_list> (eg ./hex -n 5 -d 3 -b)
```

#### File cleanup
```
cd src
make clean
```

### How to play
In each round, the user is prompted to enter a directive. The following directives are available during gameplay:

- ##### newgame [white|black [swapoff|swapon [\<size\>]]]

  Starts a new game, possibly with new settings, given in the order that is shown
  (eg. "newgame white swapon"). If no parameters are given the game settings
  are reset to the default (initial) settings (this directive is always available).

- ##### play \<move\>

  The user makes a move, eg. "play A4" (this directive is available only during the user's turn).

- ##### cont

  The agent (computer) makes a move (this directive is available only during the agent's turn).

- ##### undo

  Unplays the user's last move. If the agent (computer) played last, that move is also unplayed,
  thus rewinding the game for 2 rounds (this directive is available only if the user has made at
  least one move).

- ##### suggest

  The agent (computer) suggests a move to the user (this directive is available only during the user's turn).

- ##### level \<difficulty\>

  If the \<difficulty\> parameter is given, the difficulty of the game is updated correspondingly. Otherwise,
  the current game difficulty is displayed. Note that the game difficulty cannot exceed N², where N is the grid
  size (this directive is always available).

- ##### swap

  The swap ruled is applied (this directive is available only during the second turn, if it's the user's turn to
  make a move and the rule is active).

- ##### save \<statefile\>

  Saves the current game state in the file \<statefile\> (this directive is always available).

- ##### load \<statefile\>

  Loads the game state contained in \<statefile\> (this directive is always available).

- ##### showstate

  Prints the current game state (this directive is always available).

- ##### quit

  Terminates the program (this directive is always available).

## Authors
- George Sittas
- [John Zervakis](https://github.com/johnzerv)
