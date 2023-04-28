A reference defines an alternative name for an object
A reference type “refers to” another type

We define a reference type by writing a declarator of the form `&d`, where `d` is the name being declared:

```
int ival = 1024;  
int &refVal = ival;  // refVal refers to (is another name for) ival  
int &refVal2;        // error: a reference must be initialized
```

Ordinarily, when we initialize a variable, the value of the initializer is copied into the object we are creating. When we define a reference, instead of copying the initializer’s value, we bind the reference to its initializer.

### Reference must be Initialized

Once initialized, a reference remains bound to its initial object. There is no way to rebind a reference to refer to a different object. Because there is no way to rebind a reference, references _must_ be initialized.

### A Reference Is an Alias

A reference is not an object. Instead, a reference is _just another name for an already existing object_. After a reference has been defined, _all_ operations on that reference are actually operations on the object to which the reference is bound:

```
refVal = 2;      // assigns 2 to the object to which refVal refers, i.e., to ival  
int ii = refVal; // same as ii = ival
```

### Reference Definition

- Each identifier that is a reference must be preceded by the `&` symbol
- type of a reference and the object to which the reference refers must match exactly (with two exception)
- a reference may be bound only to an object, not to a literal or to the result of a more general expression

Examples:
```
int i = 1024, i2 = 2048;  // i and i2 are both ints  
int &r = i, r2 = i2;      // r is a reference bound to i; r2 is an int  
int i3 = 1024, &ri = i3;  // i3 is an int; ri is a reference bound to i3  
int &r3 = i3, &r4 = i2;   // both r3 and r4 are references
int &refVal4 = 10;   // error: initializer must be an object
itn &refVal6 = i + 3; // error: cannot bind to an expression
double dval = 3.14;  
int &refVal5 = dval; // error: initializer must be an int object
```

