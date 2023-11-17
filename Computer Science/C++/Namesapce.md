
example: std::cout

### using Declarations

Referring to library names with this notation can be cumbersome

A using declaration lets us use a name from a namespace without qualifying the name with a namespace_name:: prefix. 

A using declaration has the form:
```
using namespace::name;
using std::cin;
using namespace std;
```

- **A Separate using Declaration Is Required for Each Name**
- **Headers Should Not Include using Declarations** : contents of a header are copied into the including program’s text. If a header has a using declaration, then every program that includes that header gets that same using declaration.

