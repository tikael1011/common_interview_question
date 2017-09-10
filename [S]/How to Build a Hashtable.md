No language specific.

The answer is definitely NOT Hashtable<> ht = new ...
IMHO, the answer should cover/follow some logic.

Why do we need a hashtable rather than other data strcuture?
O(1) lookup.

How do HT achieve this?
By use a (good) hash function, put every key into a certain memory address.

Anything else? What if collision?
If all the keys are known, we are able to bulid a prefect hash function, no collision at all. Otherwise, there is no guarantee that no collision would happen. Thare are two main methods, open addressing and separate chaining. (some details), better mention load factor, and open addressing is good for what kind of data?(small size, single element key) what about separate chaining?

update 9/8 : Maybe ask interviewer this question as well: We will **_NOT_** use double/float as key, will we?
