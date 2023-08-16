
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





### array and pointer

arrays have a special property—in most places when we use an array, the compiler automatically substitutes a pointer to the first element:
```
string nums[] = {"one", "two", "three"};  // array of strings  
string *p = &nums[0];   // p points to the first element in nums

string *p2 = nums;      // equivalent to p2 = &nums[0]
```

There are various implications of the fact that operations on arrays are often really operations on pointers. One such implication is that when we use an array as an initializer for a variable defined using `auto`,  the deduced type is a pointer, not an array:

```
int ia[] = {0,1,2,3,4,5,6,7,8,9}; // ia is an array of ten ints  
auto ia2(ia); // ia2 is an int* that points to the first element in ia  
ia2 = 42;     // error: ia2 is a pointer, and we can't assign an int to a pointer

auto ia2(&ia[0]);  // now it's clear that ia2 has type int*
```

this connversion does not happen when we use `decltype`

```
// ia3 is an array of ten ints  
decltype(ia) ia3 = {0,1,2,3,4,5,6,7,8,9};  
ia3 = p;    // error: can't assign an int* to an array  
ia3[4] = i; // ok: assigns the value of i to an element in ia3
```

#### Pointers Are Iterators

Pointers that address array elements can use all the iterator operations

We can take the address of the nonexistent element one past the last element of an array:
```
int *e = &arr[10]; // pointer just past the last element in arr
```

Although we can compute an off-the-end pointer, doing so is error-prone. To make it easier and safer to use pointers, the new library includes two functions, named `begin` and `end`:
```
int ia[] = {0,1,2,3,4,5,6,7,8,9}; // ia is an array of ten ints  
int *beg = begin(ia); // pointer to the first element in ia  
int *last = end(ia);  // pointer one past the last element in ia
```

```
int ia[] = {0,2,4,6,8}; // array with 5 elements of type int  
int last = *(ia + 4); // ok: initializes last to 8, the value of ia[4]

last = *ia + 4;  // ok: last = 4, equivalent to ia[0] + 4
```

We can use the subscript operator on any pointer, as long as that pointer points to an element (or one past the last element) in an array:

```
int *p = &ia[2];  // p points to the element indexed by 2  
int j = p[1];     // p[1] is equivalent to *(p + 1),  
                  // p[1] is the same element as ia[3]  
int k = p[-2];    // p[-2] is the same element as ia[0]
```



### C-Style Character Strings

Character string literals are an instance of a more general construct that C++ inherits from C: **C-style character strings**.

C-style strings are not a type. Instead, they are a convention for how to represent and use character strings. Strings that follow this convention are stored in character arrays and are **null terminated**.

#### C-Style Character String Functions

![[cStringFuncs.png]]

#### compare strings

Comparing two C-style strings is done quite differently from how we compare library `string`

```
const char ca1[] = "A string example";  
const char ca2[] = "A different string";  
if (ca1 < ca2)  // undefined: compares two unrelated addresses

if (strcmp(ca1, ca2) < 0) // same effect as string comparison s1 < s2
```

####  Caller Is Responsible for Size of a Destination String

The array we pass _must_ be large enough to hold the generated string

```
// disastrous if we miscalculated the size of largeStr  
strcpy(largeStr, ca1);     // copies ca1 into largeStr
```

#### Converting between string and char array

Generally, we can use a null-terminated character array anywhere that we can use a string literal:

• We can use a null-terminated character array to initialize or assign a `string`.

• We can use a null-terminated character array as one operand (but not both operands) to the `string` addition operator or as the right-hand operand in the `string` compound assignment (`+=`) operator.

```
string s("Hello World");  // s holds Hello World

char str = "Hello World";
string s(str);  //equivalent
```

The reverse functionality is not provided: There is no direct way to use a library `string` when a C-style string is required


```
char *str = s; // error: can't initialize a char* from a string  
const char *str = s.c_str(); // ok
```

The array returned by `c_str` is not guaranteed to be valid indefinitely. Any subsequent use of `s` that might change the value of `s` can invalidate this array.




### Multidimensional Arrays

**Strictly speaking, there are no multidimensional arrays in C++.** What are commonly referred to as multidimensional arrays are actually arrays of arrays. It can be helpful to keep this fact in mind when you use what appears to be a multidimensional array.

#### define

```
int ia[3][4]; // array of size 3; each element is an array of ints of size 4  
// array of size 10; each element is a 20-element array whose elements are arrays of 30 ints  
int arr[10][20][30] = {0}; // initialize all elements to 0
```

```
int ia[3][4] = {    // three elements; each element is an array of size 4  
    {0, 1, 2, 3},   // initializers for the row indexed by 0  
    {4, 5, 6, 7},   // initializers for the row indexed by 1  
    {8, 9, 10, 11}  // initializers for the row indexed by 2  
};

// equivalent initialization without the optional nested braces for each row  
int ia[3][4] = {0,1,2,3,4,5,6,7,8,9,10,11};

// explicitly initialize only element 0 in each row  
int ia[3][4] = {{ 0 }, { 4 }, { 8 }};

// explicitly initialize row 0; the remaining elements are value initialized  
int ix[3][4] = {0, 3, 6, 9};

```


#### Range for 

```
size_t cnt = 0;  
for (auto &row : ia)        // for every element in the outer array  
    for (auto &col : row) { // for every element in the inner array  
        col = cnt;          // give this element the next value  
        ++cnt;              // increment cnt  
    }
```

In the previous example, we used references as our loop control variables because we wanted to change the elements in the array.

```
// would not compile
for (auto row : ia)  
    for (auto col : row)
```

our program would not compile. As before, the first `for` iterates through `ia`, whose elements are arrays of size 4. Because `row` is not a reference, when the compiler initializes `row` it will convert each array element (like any other object of array type) to a pointer to that array’s first element. As a result, in this loop the type of `row` is `int*`. The inner `for` loop is illegal. Despite our intentions, that loop attempts to iterate over an `int*`.

**To use a multidimensional array in a range `for`, the loop control variable for all but the innermost array must be references.**

#### Type Aliases Simplify Pointers to Multidimensional Arrays

```
using int_array = int[4]; // new style type alias declaration; 
typedef int int_array[4]; // equivalent typedef declaration; 

// print the value of each element in ia, with each inner array on its own line  
for (int_array *p = ia; p != ia + 3; ++p) {  
    for (int *q = *p; q != *p + 4; ++q)  
         cout << *q << ' ';  
    cout << endl;  
}
```


