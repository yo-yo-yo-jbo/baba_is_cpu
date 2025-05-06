# Baba Is CPU
This is going to be an unusual blogpost for me.  
Recently I got back into the game [Baba Is You](https://en.wikipedia.org/wiki/Baba_Is_You). If you don't know the game - I *highly* recommend it.  
In this blogpost, I am going to show to one might use the game mechanics to build a CPU.

## What is Baba Is You?
Baba Is You is a [Sokoban](https://en.wikipedia.org/wiki/Sokoban)-style puzzle game. It features 2 dimentional levels, in each of them you can manipulate various objects to eventually reach a goal.  
Unlike Sokoban, however, the rules that make up the game are also blocks that could be manipulated.

### Rules
The rules of the game come in a complex format, which I will not be methodically analyzing here. Here is a hand-wavy description though:
- Basic rules look like `OBJECT IS ADJECTIVE`, like `WALL IS STOP` (which makes walls non-pushable) or `BOX IS PUSH` (which makes box pushable).
- There is also `BABA IS YOU` which controls the character, but won't be super-relevant for this blogpost.
- You can also use `OBJECT IS OBJECT`, which is used quite a lot during the game. For example, `FLAG IS KEY` turns all flag objects into keys.
- There are conditional rules, like `BUG ON TREE IS FLAG` (turns the bug into a flag if placed on a tree) or `BUG FACING KEY IS WALL` (when the bug's orientation directly looks at at key, it turns into a wall).
- There are `AND` and `NOT` clauses. For example, `NOT BUG IS YOU` means you control every type of object in the game except bugs, and `BUG IS NOT YOU` would prevent you from creating `BUG IS YOU`.
- There are certain verbs that affect what the object does. For example, `KEY IS MOVE` makes keys move (according to their orientation).

The game highly abuses those mechanics - for example, breaking a `WALL IS STOP` to move through walls or turning `WALL IS YOU` to move *as the wall*.  
As the game progresses, things become more "meta", but I do not want to spoil anything and it's not super relevant for this blogpost anyway.

### Level editor
I have used a [free level editor](https://hempuli.itch.io/baba-is-you-level-editor-beta) to play around with this experiment.  
Sadly, levels have a size limit of 33x8, but it's good enough for the purpose of building the basic building-blocks of a CPU.

## Designing a CPU
What do we need to "create" a CPU in software? Apparently not much! We only need the following receipe:
- A way to represent bits (`0` and `1`).
- A way to transmit bits (in `wires`). Note this includes splitting a wire into two, just like in electric circuits.
- [Functionally complete](https://en.wikipedia.org/wiki/Functional_completeness) gates. For the same of simplicity - being able to implement a [NAND gate](https://en.wikipedia.org/wiki/NAND_gate).

Everything else (ALU, registers, control units) could be implemented using those. I think that's pretty amazing!  
In fact, I highly recommend the course [From NAND to Tetris](https://www.nand2tetris.org) that shows exactly how to get to a full CPU from those 3 concepts.
