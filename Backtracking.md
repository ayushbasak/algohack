# Backtracking
___

Each problem has three parameters:
1. Choice 
2. Constraint
3. Goal

choose -> explore -> unchoose

### N Queens
- in the helper function, 
	- check if goal state is reached __[row == n]__, add to result
	- if not, for all columms at that row:
		- add to choice, check if pattern is valid
			- if is valid, recurse to new row
			- else, remove choice

- in the validate function,
	- check if n<sup>th</sup> queen is valid

### Subsets
- include every subset created in result vector
- At one position in list iteration
	- take this element and recurse
	- remove this element and iterate

### Permutations
- for every position, check if element is already in temp list, ignore that element
- otherwise push it in temp list
- recurse to next position
- remove element from temp list
- when temp size == n, add to result vector