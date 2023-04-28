A pointer is a compound type that “points to” another type

![[Pointer v.s. Reference]]

A pointer holds the address of another object. We get the address of an object by usin the address-of operator (the & operator)

```
int ival = 42;  
int *p = &ival; // p holds the address of ival; p is a pointer to ival
```

With two exceptions, the types of the pointer and the object to which it points must match.

### Pointer value

The value (i.e., the address) stored in a pointer can be in one of four states:

**1.** It can point to an object.

**2.** It can point to the location just immediately past the end of an object.

**3.** It can be a null pointer, indicating that it is not bound to any object.

**4.** It can be invalid; values other than the preceding three are invalid.

##### Using a Pointer to Access an Object

When a pointer points to an object, we can use the dereference operator (the * operator) to access that object

```
int ival = 42;  
int *p = &ival; // p holds the address of ival; p is a pointer to ival  
cout << *p;     // * yields the object to which p points; prints 42
*p = 0;     // * yields the object; we assign a new value to ival through p  
cout << *p; // prints 0
```

We may dereference only a valid pointer that points to an object.

