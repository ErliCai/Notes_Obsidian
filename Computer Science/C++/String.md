A `string` is a variable-length sequence of characters

```
#include <string> 
using std::string;
```

### Initialization

![[String Intialization.png]]

![[Copy Initialization]]
### String operation

![[String Operation.png]]

### string::size_type

The size member returns the length of a string
```
s.size();
```
It might be logical to expect that size returns an int. nstead, size returns a **string::size_type** value.

The string class—and most other library types—defines several **companion types**. These companion types make it possible to use the library types in a machine- independent manner

Although we don’t know the precise type of string::size_type, we do know that it is an unsigned type big enough to hold the size of any string. (**Because size returns an unsigned type, it is essential to remember that expressions that mix signed and unsigned data can have surprising results, if n is an int that holds a negative value, then ``s.size() < n`` will almost surely evaluate as true.)**

To use the size_type defined by string, we use the scope operator to say that the name size_type is defined in the string class

```
string::size_type len = line.size();
auto len = line.size();
```


### Comparing String

- If two strings have different lengths and if every character in the shorter string is equal to the corresponding character of the longer string, then the shorter string is less than the longer one.
- If any characters at corresponding positions in the two strings differ, then the result of the string comparison is the result of comparing the first character at which the strings differ

### Adding literals and strings

When we mix strings and string or character literals, **at least one** operand to each + operator must be of string type:

```
string s4 = s1 + ", "; // ok: adding a string and a literal 
string s5 = "hello" + ", "; // error: no string operand
string s6 = s1 + ", " + "world"; // ok: each + has a string operand 
string s7 = "hello" + ", " + s2; // error: can't add string literals
```