Sometimes we want to define a variable whose value we know cannot be changed

We can make a variable unchangeable by defining the variable’s type as `const`

Because we can’t change the value of a `const` object after we create it, it must be **initialized**

```
const int bufSize = 512;    // input buffer size
bufSize = 512; // error: attempt to write to const object
const int k;               // error: k is uninitialized const
```



### By Default, `const` Objects Are Local to a File

When a `const` object is initialized from a compile-time constant, such as in our definition of `bufSize`, the compiler will usually replace uses of the variable with its corresponding value during compilation

To substitute the value for the variable, the compiler has to see the variable’s initializer. When we split a program into multiple files, every file that uses the `const` must have access to its initializer. In order to see the initializer, the variable must be defined in every file that wants to use the variable’s value

To share a `const` object among multiple files, you must define the variable as `extern`.

```
// file_1.cc defines and initializes a const that is accessible to other files  
extern const int bufSize = fcn();  
// file_1.h  
extern const int bufSize; // same bufSize as defined in file_1.cc
```

### Reference to const

Unlike an ordinary reference, a reference to `const` cannot be used to change the object to which the reference is bound:

```
const int ci = 1024;  
const int &r1 = ci;   // ok: both reference and underlying object are const  
r1 = 42;              // error: r1 is a reference to const  
int &r2 = ci;         // error: non const reference to a const object
```

###  Initialization of References to `const`

we can initialize a reference to `const` from any expression that can be converted to the type of the reference.

```
int i = 42;  
const int &r1 = i;      // we can bind a const int& to a plain int object  
const int &r2 = 42;     // ok: r2 is a reference to const  
const int &r3 = r1 * 2; // ok: r3 is a reference to const  
int &r4 = r1 * 2;        // error: r4 is a plain, non const reference
```

### Pointer and Const
 Like a reference to `const`, a pointer to `const` may not be used to change the object to which the pointer points. We may store the address of a `const` object only in a pointer to `const`:
 
```
const double pi = 3.14;   // pi is const; its value may not be changed  
double *ptr = &pi;        // error: ptr is a plain pointer  
const double *cptr = &pi; // ok: cptr may point to a double that is const  
*cptr = 42;               // error: cannot assign to *cptr
```

we can use a pointer to `const` to point to a non`const` object:
```
double dval = 3.14;       // dval is a double; its value can be changed  
const double *cptr = &dval;             // ok: but can't change dval through cptr
```

### Const Pointer

Like any other `const` object, a `const`**pointer** must be initialized

We indicate that the pointer is `const` by putting the `const` after the `*`:
```
int errNumb = 0;  
int *const curErr = &errNumb;  // curErr will always point to errNumb
const double pi = 3.14159;  
const double *const pip = &pi; // pip is a const pointer to a const object
```

The fact that a pointer is itself `const` says nothing about whether we can use the pointer to change the underlying object.

### Top-level const

We use the term top-level `const` to indicate that the pointer itself is a `const`. When a pointer can point to a `const` object, we refer to that `const` as a low-level `const`

top-level `const` indicates that an object itself is `const`. Top-level `const` can appear in any object type

Low-level `const` appears in the base type of compound types such as pointers or references.

The distinction between top-level and low-level matters when we copy an object. 
- When we copy an object, top-level `const`s are ignored. Copying an object doesn’t change the copied object. As a result, it is immaterial whether the object copied from or copied into is `const`.
- On the other hand, low-level `const` is never ignored. When we copy an object, both objects must have the same low-level `const` qualification or there must be a conversion between the types of the two objects. In general, we can convert a non`const` to `const` but not the other way round