Braced lists of initializers can now be used whenever we initialize an object and in some cases when we assign a new value to an object.

```
int units_sold = 0;
int units_sold = {0};
```

this form of initialization has one important property: The compiler will not let us list initialize variables of built-in type if the initializer might lead to the loss of information:

```
long double ld = 3.1415926536;  
int a{ld}, b = {ld}; // error: narrowing conversion required  
int c(ld), d = ld;   // ok: but value will be truncated
```

