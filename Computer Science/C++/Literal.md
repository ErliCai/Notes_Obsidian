
A value, such as `42`, is known as a literal because its value self-evident.

### Interger Literal

- decimal:  20
- octal: 024
- hexidecimal: 0x14
- binary:  0b10100

Although integer literals may be stored in signed types, technically speaking, **the value of a decimal literal is never a negative number**. If we write what appears to be a negative decimal literal, for example, `-42`, the minus sign is _not_part of the literal. The minus sign is an operator that negates the value of its (literal) operand.


### Floating Literal

Floating-point literals include either a decimal point or an exponent specified using scientific notation

e.g: 3.14159    3.14159E0    0.    0e0    .001

### Character and Character String Literals

```
'a'  // character literal  
"Hello World!"  // string literal
```

The compiler appends a null character (’`\0`’) to every string literal.

For example, the literal `'A'` represents the single character `A`, whereas the string literal `"A"` represents an array of two characters, the letter `A` and the null character.

Two string literals that appear adjacent to one another and that are separated only by spaces, tabs, or newlines are concatenated into a single literal.

```
std::cout << "a really, really long string literal "  
             "that spans two lines" << std::endl;
```

### Escape Sequence

Some characters, such as backspace or control characters, have no visible image. Such characters are nonprintable. Other characters (single and double quotation marks, question mark, and backslash) have special meaning in the language. Our programs cannot use any of these characters directly. Instead, we use an escape sequence to represent such characters.

newline            `\n`     horizontal tab      `\t`     alert (bell)       `\a`  
vertical tab       `\v`     backspace          `\b`     double quote  `\"`  
backslash         `\\`     question mark     `\?`     single quote    `\'`  
carriage return   `\r`     formfeed            `\f`


We can also write a generalized escape sequence, which is `\x` followed by one or more hexadecimal digits or a `\` followed by one, two, or three octal digits. The value represents the numerical value of the character. Some examples (assuming the Latin-1 character set):

```
std::cout << "Hi \x4dO\115!\n";  // prints Hi MOM! followed by a newline  
std::cout << '\115' << '\n';     // prints M followed by a newline
```

#### Specifying the Type of a Literal

We can override the default type of an integer, floating- point, or character literal by supplying a suffix or prefix as listed below

![[literal_prefix_suffix.png]]

```
L'a'     // wide character literal, type is wchar_t  
u8"hi!"  // utf-8 string literal (utf-8 encodes a Unicode character in 8 bits)  
42ULL    // unsigned integer literal, type is unsigned long long  
1E-3F    // single-precision floating-point literal, type is float  
3.14159L // extended-precision floating-point literal, type is long double
```


### Boolean and Pointer Literals

The words `true` and `false` are literals of type `bool`:
```
bool test = false;
```

The word `nullptr` is a pointer literal.