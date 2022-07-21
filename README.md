# hunting-the-wolf-ZK-game
ZK game designed for ZKU cohort 4 week 3 assignment

## Game start
* The game starts with the generation of a matrix n*m.
* The matrix is filled with i numbers of sheeps, every sheep has a assigned number.
* The wolf has to choose a sheep to kill it and steal its skin. the sheep number has to be hashed with a salt in order to commit the decision of the wolf. H(Sheep#,WolfSalt), this hash has to be public.

## Rounds
* In every round the wolf has to select a ship to kill.(The wolf has to compute the wollfKillSheep)
* Then this sheep apears dead(wollfKillSheep output).
* now it is time for the shepherd to make deductions, he can shoot a sheep to see if it is the wolf, if it is not the sheep dies.(The wolf has to compute shepherdKillSheep).

## Final
* The game is over hen the shepherd kills the wolf, the score consist in the # of sheps that left alive.
* The game can be repeated switching the roles in order to compare the scores and obtain a winner.



ZK is used to allow the game computation mantaining the hiden wollf in secret
