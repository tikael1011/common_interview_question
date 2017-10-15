This is about knowledge of string in Java and Python.
Things covered in UTF file will not appear again.

Will update often

Why string in java is immutable?
[Answer on stackoverflow](https://stackoverflow.com/questions/1552301/immutability-of-strings-in-java)

[Another one](https://dzone.com/articles/why-string-immutable-java)

[Similiar in Python](https://stackoverflow.com/questions/9097994/arent-python-strings-immutable)

look at the following code:

```java
String s1 = "hello";
String s2 = s1;
System.out.println(s2); //hello
System.out.println(s1==s2);//true
System.out.println(s1.equals(s2));//true
s1 = "HHHH";
System.out.println(s2); // hello
```

```java
String s1 = "Hello";
String s2 = s1;
char[] cc = s1.toCharArray();
cc[1] = 'H';
StringBuilder sb = new StringBuilder();
for(char c : cc) sb.append(c);
s1 = sb.toString();
System.out.println(s1); //HHllo
System.out.println(s2); //Hello
```

```java
String s1 = "Hello";
String s2 = s1;
s1.replace('o', 'a');
System.out.println(s1); //Hello
System.out.println(s2); //Hello
s1 = s1.replace('o', 'a');
System.out.println(s1); //Hella
System.out.println(s2); //Hello
```
