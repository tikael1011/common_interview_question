[Does Python optimize tail recursion?](https://stackoverflow.com/questions/13591970/does-python-optimize-tail-recursion)

[What is tail recursion?](https://stackoverflow.com/questions/33923/what-is-tail-recursion?rq=1)

[Guido's words 1](http://neopythonic.blogspot.com.au/2009/04/tail-recursion-elimination.html)

[Guido's words 2](http://neopythonic.blogspot.com.au/2009/04/final-words-on-tail-calls.html)


In traditional recursion, the typical model is that you perform your recursive calls first, and then you take the return value of the recursive call and calculate the result. In this manner, you don't get the result of your calculation until you have returned from every recursive call.

In tail recursion, you perform your calculations first, and then you execute the recursive call, passing the results of your current step to the next recursive step. This results in the last statement being in the form of "(return (recursive-function params))" 


Normal One
```Python
def recsum(x):
    if x == 1:
        return x
    else:
        return x + recsum(x - 1)
```

TR
```Python
def tailrecsum(x, running_total=0):
    if x == 0:
        return running_total
    else:
        return tailrecsum(x - 1, running_total + x)
```
