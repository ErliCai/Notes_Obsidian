A `type alias` is a name that is a synonym for another type. Type aliases let us simplify complicated type definitions, making those types easier to use. Type aliases also let us emphasize the purpose for which a type is used.

Traditionally, we use a typedef:

```
typedef double wages;   // wages is a synonym for double  
typedef wages base, *p; // base is a synonym for double, p for double*
```

The new standard introduced a second way to define a type alias, via an `alias declaration`:

```
using SI = Sales_item;  // SI is a synonym for Sales_item
```

### Pointers, `const`, and Type Aliases

The base type in these declarations is `const pstring`. As usual, a `const` that appears in the base type modifies the given type.

```
typedef char *pstring;  
const pstring cstr = 0; // cstr is a constant pointer to char  
const char *cstr = 0; // wrong interpretation of const pstring cstr
const pstring *ps;      // ps is a pointer to a constant pointer to char
```