# sudoku-solver
A Rust sudoku server for me to practice concepts on.

My goal is to write a package which I can then try out in various
situations (web server, WASM, making a Ruby Gem, Rust embedded). Maybe
I'll port the same design over to other languages to get some
comparisons.

This will be a solver for 9x9 standard sudoku puzzles. It will be
backtracking - for each empty square it will try each of the 9
possibilities - if none work then it knows the previous state is wrong
and to continue the enumeration from the previous square.

Backtracking will allow me to create an Iterator for solutions. I think
I will be able to make it double ended by counting down from 9 instead
of up from 1 (I expect this to be the case but I haven't properly
checked yet). An iterator will allow me to categorize a puzzle as:
* unsolvable
* uniquely solvable
* multiple solutions

My one nod towards optimisation will be to pick the order of the squares
tactically. Instead of starting in the top left corner and working
round, it will create a plan based on prioritising squares which are in
the most complete row/column/region.
