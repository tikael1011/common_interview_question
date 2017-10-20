The question is , given a stream of inputs, consists two arrays, one is called op, which contains either push or pop, add a number and remove a number respectively, while the other is arr, which contains integers[1]. The output is array of product of max and min number (you have/in the stack/from the stream...) Assume pop operation is always valid.

eg: 
op = ['push','push','pop','push']
arr = [1,2,2,5]
ans = [1*1, 1*2, 1*1, 1*5]

op = ['push','push','push','pop']
arr = [1,2,3,1]
ans = [1*1, 1*2, 1*3, 2*3]

[1] to make things easy,range is [1,2^16), but this can be expaned to [INT_MIN,INT_MAX] (for java, not python though)

Q: how to deal with duplicates from push, does pop() remove the current instance or all the instances has the same value
A: You may assume pop the current value only. but you can put another solution for remove all instances seperately.

One idea is maintain two heap, one is min and the other is max. Every time push, add element to both heap, and remove respectively. But there is one problem, if there is duplicate in the input stream, remove will remove all of them. Maybe maintain an extra hashmap to store weather or not dup? 
