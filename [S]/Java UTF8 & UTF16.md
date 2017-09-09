How do I come to this question?

Q: How does java String.lengh() work?
```bash
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
```bash
throws UnsupportedEncodingException
```
or surround with try-catch

http://docs.oracle.com/javase/tutorial/i18n/text/unicode.html
