How do I come to this question?

[reading1](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/)

[reading2](http://www.unicode.org/notes/tn23/)

Q: How does java String.lengh() work?
```Java
    final String string = "Hello World";

    // Check length
    System.out.println(string.length()); // prints "11"

    // Check encoded sizes
    final byte[] utf8Bytes = string.getBytes("UTF-8");
    System.out.println(utf8Bytes.length); // prints "11"

    final byte[] utf16BEBytes= string.getBytes("UTF-16BE");
    System.out.println(utf16BEBytes.length); // prints "22"

    final byte[] utf16Bytes= string.getBytes("UTF-16");
    System.out.println(utf16Bytes.length); // prints "24". the diff is BOM : byte order mark

    final byte[] utf32Bytes = string.getBytes("UTF-32");
    System.out.println(utf32Bytes.length); // prints "44"

    final byte[] isoBytes = string.getBytes("ISO-8859-1");
    System.out.println(isoBytes.length); // prints "11"

    final byte[] winBytes = string.getBytes("CP1252");
    System.out.println(winBytes.length); // prints "11"
```

in java do not forget
```Java
throws UnsupportedEncodingException
```
or surround with try-catch

http://docs.oracle.com/javase/tutorial/i18n/text/unicode.html

[Top answer from stackoverflow](https://stackoverflow.com/questions/4655250/difference-between-utf-8-and-utf-16)

Both UTF-8 and UTF-16 are variable length encodings. However, in UTF-8 a character may occupy a minimum of 8 bits, while in UTF-16 character length starts with 16 bits.

Main UTF-8 pros:
Basic ASCII characters like digits, Latin characters with no accents, etc. occupy one byte which is identical to US-ASCII representation. This way all US-ASCII strings become valid UTF-8, which provides decent backwards compatibility in many cases.
No null bytes, which allows to use null-terminated strings, this introduces a great deal of backwards compatibility too.
UTF-8 is independent of byte order, so you don't have to worry about Big Endian / Little Endian issue.

Main UTF-8 cons:
Many common characters have different length, which slows indexing by codepoint and calculating a codepoint count terribly.
Even though byte order doesn't matter, sometimes UTF-8 still has BOM (byte order mark) which serves to notify that the text is encoded in UTF-8, and also breaks compatibility with ASCII software even if the text only contains ASCII characters. Microsoft software (like Notepad) especially likes to add BOM to UTF-8.

Main UTF-16 pros:
BMP (basic multilingual plane) characters, including Latin, Cyrillic, most Chinese (the PRC made support for some codepoints outside BMP mandatory), most Japanese can be represented with 2 bytes. This speeds up indexing and calculating codepoint count in case the text does not contain supplementary characters.
Even if the text has supplementary characters, they are still represented by pairs of 16-bit values, which means that the total length is still divisible by two and allows to use 16-bit char as the primitive component of the string.

Main UTF-16 cons:
Lots of null bytes in US-ASCII strings, which means no null-terminated strings and a lot of wasted memory.
Using it as a fixed-length encoding “mostly works” in many common scenarios (especially in US / EU / countries with Cyrillic alphabets / Israel / Arab countries / Iran and many others), often leading to broken support where it doesn't. This means the programmers have to be aware of surrogate pairs and handle them properly in cases where it matters!
It's variable length, so counting or indexing codepoints is costly, though less than UTF-8.

In general, UTF-16 is usually better for in-memory representation because BE/LE is irrelevant there (just use native order) and indexing is faster (just don't forget to handle surrogate pairs properly). UTF-8, on the other hand, is extremely good for text files and network protocols because there is no BE/LE issue and null-termination often comes in handy, as well as ASCII-compatibility.
