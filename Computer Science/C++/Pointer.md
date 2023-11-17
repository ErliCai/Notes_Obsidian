A pointer is a compound type that “points to” another type

![[Pointer v.s. Reference]]

A pointer holds the address of another object. We get the address of an object by usin the address-of operator (the & operator)

```
int ival = 42;  
int *p = &ival; // p holds the address of ival; p is a pointer to ival
```

With two exceptions ([[Const#Pointer and Const|Pointer to const]]), the types of the pointer and the object to which it points must match.

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

![[Null pointer]]

NULL is the [[Preprocessor Variable]]

###  Initialize all Pointers

![[Uninitialized pointers#^cc42e1]]

If possible, define a pointer only after the object to which it should point has been defined. If there is no object to bind to a pointer, then initialize the pointer to `nullptr` or zero.

### Compare Pointers

Two pointers are equal if they hold the same address and unequal otherwise. 

Two pointers hold the same address (i.e., are equal) if 
- they are both null, 
- if they address the same object,
- or if they are both pointers one past the same object

`Note that it is possible for a pointer to an object and a pointer one past the end of a different object to hold the same address. Such pointers will compare equal.`

![[Void Pointer]]

### Common Pitfall with pointer declaration

```
int* p;  // legal but might be misleading
int* p1, p2; // p1 is a pointer to int; p2 is an int
```

### Pointer of Pointer

In general, there are no limits to how many type modifiers can be applied to a declarator.

As one example, consider a pointer. A pointer is an object in memory, so like any object it has an address. Therefore, we can store the address of a pointer in another pointer.

```
int ival = 1024;  
int *pi = &ival;    // pi points to an int  
int **ppi = &pi;    // ppi points to a pointer to an int
```

![[Pointer with Reference]]


