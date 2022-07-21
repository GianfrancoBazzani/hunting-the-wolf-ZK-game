# hunting-the-wolf-ZK-game
ZK game designed for ZKU cohort 4 week 3 assignment

## Game start
* The game starts with the generation of a matrix n*m.
* The matrix is filled with i numbers of sheep, every sheep has a assigned number.
* The wolf has to choose a sheep to kill it and steal its skin. The sheep number has to be hashed with a salt in order to commit the decision of the wolf. H(Sheep#,WolfSalt), this hash has to be public.

## Rounds
* In every round the wolf has to select a ship to kill.(The wolf has to compute the wollfKillSheep)
* Then this sheep appear dead(wollfKillSheep output).
* now it is time for the shepherd to make deductions, he can shoot a sheep to see if it is the wolf, if it is not the sheep dies.(The wolf has to compute shepherdKillSheep).
* Finaly the sheep are mixed randomly and a new round can start again.

## Final
* The game is over hen the shepherd kills the wolf, the score consists in the # of sheep that left alive.
* The game can be repeated switching the roles in order to compare the scores and obtain a winner.

ZK is used to allow the game computation mantaining hiden the wolf hidden inside a sheep skin. To avoid brute force attack against the wolf hidden identity we use a salted hash commitment.

## Circuits
we use 2 circuits, since every round is done in 2 steps
* wollfKillSheep: checks if the sheep is dead, checks if the identity of the wolf is correct with the public hash,  checks if the sheep to kill is in the range of the wolf, outputs the #of the killed sheep.
* shepherdKillSheep: checks if the sheep is dead, checks if the sheep is the wolf, outputs the # of the killed sheep.

## Example play with 3X3 matrix

|0|0|0|
|-|-|-|
|0|0|0|
|-|-|-|
|0|0|0|

