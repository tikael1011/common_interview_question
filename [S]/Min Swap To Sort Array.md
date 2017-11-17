the question is from : [geekforge](http://www.geeksforgeeks.org/minimum-number-swaps-required-sort-array/)

the trick is 

**ans = Σ(cycle_size – 1)**

and the cycle_size means how many nodes are included in it. 

and how do we detect a cycle?
we need to use a hashmap to store original (value, index) pair, then sort the array to figure out what is the correct position. Now, go arr[i] -> k -> arr[k] -> l -> arr[l] ...whenever arr[l] == arr[i], we find a cycle, also, when we visit the arr, mark every visited element.

code is trivia.

note that it is provided that there is no duplicated element in the original input.
