# hunting-the-wolf-ZK-game
ZK game designed for ZKU cohort 4 week 3 assignment

## Game start
* The game starts with the generation of a matrix n*m.
* The matrix is filled with i numbers of sheep, every sheep has a assigned number.
* The wolf has to choose a sheep to kill it and steal its skin. The sheep number has to be hashed with a salt in order to commit the decision of the wolf. H(Sheep#,WolfSalt), this hash has to be public.

## Rounds
* In every round the wolf has to select a ship to kill ony can kill that is in contact(distance = 1).(The wolf has to compute the wollfKillSheep)
* Then this sheep appear dead(wollfKillSheep output).
* now it is time for the shepherd to make deductions, he can shoot a sheep to see if it is the wolf, if it is not the sheep dies.(The wolf has to compute shepherdKillSheep).
* Finally the sheep are mixed randomly and a new round can start again.

## Final
* The game is over hen the shepherd kills the wolf, the score consists in the # of sheep that left alive.
* The game can be repeated switching the roles in order to compare the scores and obtain a winner.

ZK is used to allow the game computation maintaining hidden the wolf inside a sheep skin. To avoid brute force attack against the wolf hidden identity we use a salted hash commitment.

## Circuits
we use 2 circuits, since every round is done in 2 steps
* wollfKillSheep: checks if the sheep is dead, checks if the identity of the wolf is correct with the public hash,  checks if the sheep to kill is in the range of the wolf, outputs the #of the killed sheep.
* shepherdKillSheep: checks if the sheep is dead, checks if the sheep is the wolf, outputs the # of the killed sheep.

## Example play with 3X3 matrix
### Round1

Initial random ditribution of the sheep in the field
"secret info": the wolf is the shep #7
the wolf decides to kill the sheep #1
|2|4|3|
|-|-|-|
|5|1|7|
|8|9|6|

The shepherd decides not to gamble and not kill any sheep
|2|4|3|
|-|-|-|
|5|X|7|
|8|9|6|

### Round2
the sheep are mixed, corpses don't move
the wolf decides to kill the sheep #6
|4|7|2|
|-|-|-|
|3|X|X|
|5|8|9|

the shepherd is suspicious about (7,2,8,9)
the shepherd decides to kill sheep #2
he was wrong
|4|7|X|
|-|-|-|
|3|X|X|
|5|8|9|

### Round 3
the sheep are mixed, corpses don't move
the wolf only can kill the sheep #3
|4|9|X|
|-|-|-|
|8|X|X|
|5|X|7|
   
the shepherd is suspicious about (7,8)
the shepherd decides to kill sheep #7
he was right
|4|9|X|
|-|-|-|
|8|X|X|
|5|X|X|


The game ends with 3 sheep alive
