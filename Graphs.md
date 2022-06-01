# Graphs
___

### Topological Sorting
- create a rank / degrees array
- assign 0 rank to elements in rank array 
- stack of 0 rank elements
- while there are elements in 0 rank array,
	- add node to result vector, remove from 0 rank array
	- for children in node, decrement rank, if their rank is 0 append to 0 rank array 


