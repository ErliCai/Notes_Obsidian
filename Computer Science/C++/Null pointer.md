
different ways to define null pointers:

```
int *p1 = nullptr; // equivalent to int *p1 = 0;  
int *p2 = 0;       // directly initializes p2 from the literal constant 0  
// must #include cstdlib  
int *p3 = NULL;    // equivalent to int *p3 = 0;
```

It is illegal to assign an `int` variable to a pointer, even if the variable’s value happens to be `0`.

```
int zero = 0;  
pi = zero;        // error: cannot assign an int to a pointer
```