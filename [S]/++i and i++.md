//This Question is for C++

One maybe told that ++i is a fit faster, or at least not slower than i++, why? and does this apply to other language?

It does __NOT__ apply to other language

In C++, ++i just does its job and out, while i++ will create a variable to perform the increment.

Unless you need the value 'i', there is no reason to use i++ over ++i.
