similar to [LC525](https://leetcode.com/problems/contiguous-array/description/)

Given an array with **At Most** _k_ distinct integer, you may assume they are [0,k-1],  find the maximum length of a contiguous subarray with equal number of distinct integers.

one may start with " **Exactly** _k_ distinct integer " , obviously _k-1_ nested loop could work, but can we do better?

example: 
input: [0,1,2,1] , k = 3
output: 3

input: [0,1,2,3,0,1] k = 5
output: 4 