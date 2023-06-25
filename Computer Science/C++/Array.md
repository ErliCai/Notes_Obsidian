
#### vector v.s array

An array is a data structure that is similar to the library `vector` type but offers a **different trade-off** between performance and flexibility.

Unlike a `vector`, arrays have fixed size; we cannot add elements to an array. Because arrays have fixed size, they sometimes offer better run-time performance for specialized applications. However, that run-time advantage comes at the cost of lost flexibility.

`If you don’t know exactly how many elements you need, use a vector`.`

### Defining and Initializing

#### Defining array

Arrays are a `compound type `

An array declarator has the form `a[d]`, where `a` is the name being defined and `d` is the dimension of the array.

The number of elements in an array is part of the array’s type. As a result, **the dimension must be known at compile time**, which means that the dimension must be a `constant expression`

```
int arr[10];             // array of ten ints  
int *parr[sz];           // array of 42 pointers to int  
string bad[cnt];         // error: cnt is not a constant expression  
string strs[get_size()]; // ok if get_size is constexpr, error otherwise
```

As with `vector`, arrays hold objects. Thus, t**here are no arrays of references**.

`As with variables of built-in type, a default-initialized array of built-in type that is defined inside a function will have undefined values.`

#### Explicitly initialize

We can list initialize the elements in an array. When we do so, we can omit the dimension.

If we omit the dimension, the compiler infers it from the number of initializers. If we specify a dimension, the number of initializers must not exceed the specified size. If the dimension is greater than the number of initializers, the initializers are used for the first elements and any remaining elements are value initialized

```
const unsigned sz = 3;  
int ia1[sz] = {0,1,2};        // array of three ints with values 0, 1, 2
```


#### character arrays are special

Character arrays have an additional form of initialization: We can initialize such arrays from a string literal. When we use this form of initialization, it is important to remember that string literals end with a null character. That null character is copied into the array along with the characters in the literal:

```
char a1[] = {'C', '+', '+'};       // list initialization, no null  
char a2[] = {'C', '+', '+', '\0'}; // list initialization, explicit null  
char a3[] = "C++";                 // null terminator added automatically  
const char a4[6] = "Daniel";       // error: no space for the null!
```

#### no copy assignment

We cannot initialize an array as a copy of another array, nor is it legal to assign one array to another:

```
int a[] = {0, 1, 2}; // array of three ints  
int a2[] = a;        // error: cannot initialize one array with another  
a2 = a;              // error: cannot assign one array to another
```

#### Pointer of array

```
int *ptrs[10];            //  ptrs is an array of ten pointers to int  
int &refs[10] = /* ? */;  //  error: no arrays of references  
int (*Parray)[10] = &arr; //  Parray points to an array of ten ints  
int (&arrRef)[10] = arr;  //  arrRef refers to an array of ten ints
```

By default, type modifiers bind right to left. Reading the definition of `ptrs` from right to left is easy: We see that we’re defining an array of size 10, named `ptrs`, that holds pointers to `int`.

there are no limits on how many type modifiers can be used:
```
int *(&arry)[10] = ptrs; // arry is a reference to an array of ten pointers
```



### Accessing elements in array

When we use a variable to subscript an array, we normally should define that variable to have type `size_t` . `size_t` is a machine-specific unsigned type that is guaranteed to be large enough to hold the size of any object in memory. The `size_t` type is defined in the `cstddef` header, which is the C++ version of the `stddef.h` header from the C library.

As with `string` and `vector`, it is up to the programmer to ensure that the subscript value is in range—that is, that the index value is equal to or greater than zero and less than the size of the array.

The most common source of security problems are buffer overflow bugs. Such bugs occur when a program fails to check a subscript and mistakenly uses memory outside the range of an array or similar data structure. ^cf68aa


