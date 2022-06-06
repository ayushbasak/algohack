# Linked Lists
___

### Intersection of two linked lists
a1 -> a2 -> ... ak -> c1 -> c2 -> ... cl
b1 -> b2 -> ... bn -> c1 -> c2 -> ... cl

intersection at c1

- iterate both head forward
- when one reaches _nullptr_, point to head of another list
- total length travelled by first node = k + l  + n
- total length travelled by second node = n + l + k
- in case of no intersection, both heads travel a + b length and b + a length respectively