# Baba Is CPU
This is going to be an unusual blogpost for me.  
Recently I got back into the game [Baba Is You](https://en.wikipedia.org/wiki/Baba_Is_You). If you don't know the game - I *highly* recommend it.  
In this blogpost, I am going to show to Turing-completeness of the game.

## What is Baba Is You?
Baba Is You is a [Sokoban](https://en.wikipedia.org/wiki/Sokoban)-style puzzle game. It features 2 dimentional levels, in each of them you can manipulate various objects to eventually reach a goal.  
Unlike Sokoban, however, the rules that make up the game are also blocks that could be manipulated.

### Rules
The rules of the game come in a complex format, which I will not be methodically analyzing here. Here is a hand-wavy description though:
- Basic rules look like `OBJECT IS ADJECTIVE`, like `WALL IS STOP` (which makes walls non-pushable) or `BOX IS PUSH` (which makes box pushable).
- There is also `BABA IS YOU` which controls the character, but won't be super-relevant for this blogpost.
- You can also use `OBJECT IS OBJECT`, which is used quite a lot during the game. For example, `FLAG IS KEY` turns all flag objects into keys.
- There are conditional rules, like `BUG ON TREE IS FLAG` (turns the bug into a flag if placed on a tree) or `BUG FACING KEY IS WALL` (when the bug's orientation directly looks at at key, it turns into a wall).

The game highly abuses those mechanics - for example, breaking a `WALL IS STOP` to move through walls or turning `WALL IS YOU` to move *as the wall*.
