A reference is not an object. Hence, we may not have a pointer to a reference. However, because a pointer is an object, we can define a reference to a pointer:

```
int i = 42;  
int *p;        // p is a pointer to int  
int *&r = p;   // r is a reference to the pointer p  
r = &i; //  r refers to a pointer; assigning &i to r makes p point to i  
*r = 0; //  dereferencing r yields i, the object to which p points; changes i to 0
```

The easiest way to understand the type of `r` is to read the definition right to left.

The symbol closest to the name of the variable (in this case the `&` in `&r`) is the one that has the most immediate effect on the variable’s type.
