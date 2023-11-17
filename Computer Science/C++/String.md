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

#### getline

```
int main()  
{  
    string line;  
    // read input a line at a time until end-of-file  
    while (getline(cin, line))  
        cout << line << endl;  
    return 0;  
}
```

##### getline vs cin

The `string` input operator `<<` will regard all three kinds of whitespace characters as delimiter, so the string read from the operator will contain no whitespace characters.

The `getline` function will regard only the newline character as delimiter, so the string read from `getline` function will contain no newline character but may contain space or tab.

#### string::size_type

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


#### Comparing String

- If two strings have different lengths and if every character in the shorter string is equal to the corresponding character of the longer string, then the shorter string is less than the longer one.
- If any characters at corresponding positions in the two strings differ, then the result of the string comparison is the result of comparing the first character at which the strings differ

#### Adding literals and strings

When we mix strings and string or character literals, `at least one` operand to each + operator must be of string type:

```
string s4 = s1 + ", "; // ok: adding a string and a literal 
string s5 = "hello" + ", "; // error: no string operand
string s6 = s1 + ", " + "world"; // ok: each + has a string operand 
string s7 = "hello" + ", " + s2; // error: can't add string literals
```

`String literal are different from library String`

For historical reasons, and for compatibility with C, string literals are _not_ standard library `string`s. It is important to remember that these types differ when you use string literals and library `string`s.



### Dealing with the Characters in a `string`

#### cctype function
part of processing characters is knowing and/or changing the characteristics of a character. These functions are defined in the `cctype` header.

![[cctype.png]]

#### process every chars in a string

Use Range-Based `for`:

```
for (declaration : expression)  
    statement
```

``` 
string str("some string");  
// print the characters in str one character to a line  
for (auto c : str)      // for every char in str  
    cout << c << endl;  // print the current character followed by a newline
```

#### Processing some chars

use subscript or iterator

The subscript operator (the `[ ]` **operator** takes a `string::size_type`  value that denotes the position of the character we want to access. The operator returns a reference to the character at the given position.

Subscripts for `string`s start at zero; if `s` is a `string` with at least two characters, then `s[0]` is the first character, `s[1]` is the second, and the last character is in `s[s.size() - 1]`.

```
string s("some string");  
if (!s.empty())             // make sure there's a character in s[0]  
    s[0] = toupper(s[0]);   // assign a new value to the first character in s
```


#### Subscripts are unchecked

When we use a subscript, we must ensure that the subscript is in range. That is, the subscript must be `>= 0` and `<` the `size()` of the `string`. One way to simplify code that uses subscripts is _always_ to use a variable of type `string::size_type` as the subscript. Because that type is `unsigned`, we ensure that the subscript cannot be less than zero. When we use a `size_type` value as the subscript, we need to check only that our subscript is less than value returned by `size()`.