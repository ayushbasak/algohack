# Graphs
___

### Topological Sorting
- create a rank / degrees array
- assign 0 rank to elements in rank array 
- stack of 0 rank elements
- while there are elements in 0 rank array,
	- add node to result vector, remove from 0 rank array
	- for children in node, decrement rank, if their rank is 0 append to 0 rank array 

### Clone Graph
- Use BFS [reference](https://www.youtube.com/watch?v=vma9tCQUXk8)
- Search All elements in Graph
- From the start node, add it to the Queue, create a copy, map its copy to a hashtable
- until the queue is empty:
	- get the front element of queue, for all adjacent nodes of current node, 
	- if adjacent node is not in hashtable, create a clone of the adjacent node, map it in the hashtable, create a link of hashmap[current_node]->hashmap[adjacent_node]
	- Add adjacent node to queue

- Time Complexity O(|V| + |E|)
- Space Complexity O(|V| + |E|)
