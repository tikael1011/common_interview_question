Rotate Matrix

clockwise, counter-clockwise, 180 degree, transpose...

The following solution is O(n^2) rc and O(1) space. (And I believe is the best we can do)

Rotate by +90:

Transpose
Reverse each row
Rotate by -90:

Method 1 :

Transpose
Reverse each column
Method 2 :

Reverse each row
Transpose
Rotate by +180:

Method 1: Rotate by +90 twice

Method 2: Reverse each row and then reverse each column (Transpose)

Rotate by -180:

Method 1: Rotate by -90 twice

Method 2: Reverse each column and then reverse each row

Method 3: Rotate by +180 as they are same

```Python
rotated = zip(*original[::-1]) #clockwise 90
```
```Python
rotated_ccw = zip(*original)[::-1] #counterclockswise 90
```
Personally I do not like to two nest for loop and we have other solution, so why bother?
