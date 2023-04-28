A declaration makes a name known to the program. A file that wants to use a name defined elsewhere includes a declaration for that name

A declaration is a base type followed by a list of declarators. see also [[Compound Type]]

To obtain a declaration that is not also a definition, we add the `extern` keyword and may not provide an explicit initializer:

```
extern int i;   // declares but does not define i  
int j;          // declares and defines j
```

Any declaration that includes an explicit initializer is a definition. We can provide an initializer on a variable defined as `extern`, but doing so overrides the `extern`. An `extern` that has an initializer is a definition: ^initializeExtern1

```
extern double pi = 3.1416; // definition
```

^initializeExtern2

It is an error to provide an initializer on an `extern` inside a function.

[[Declaration v.s Definition]]
[[Declaration errors]]