### Vector

A `vector` is a collection of objects, all of which have the same type. Every object in the collection has an associated index, which gives access to that object. A `vector` is often referred to as a `container` because it “contains” other objects.

A `vector` is a `class template`. C++ has both class and function templates.

`Templates` are not themselves functions or classes. Instead, they can be thought of as instructions to the compiler for generating classes or functions. The process that the compiler uses to create classes or functions from templates is called `instantiation`

When we use a template, we specify what kind of class or function we want the compiler to instantiate.

For a class template, we specify which class to instantiate by supplying additional information, the nature of which depends on the template. How we specify the information is always the same: We supply it inside a pair of angle brackets following the template’s name.

In the case of `vector`, the additional information we supply is the type of the objects the `vector` will hold:

```
vector<int> ivec;             // ivec holds objects of type int  
vector<Sales_item> Sales_vec; // holds Sales_items  
vector<vector<string>> file;  // vector whose elements are vectors
```

We can define `vector`s to hold objects of most any type. Because references are not objects, we cannot have a `vector` of references

###  Initialization

![[vector_initialization.png]]

##### List Initializer or Element Count?

- On one hand, if we use braces and there is no way to use the initializers to list initialize the object,
- On the other hand,  When we use curly braces, `{...}`, we’re saying that, if possible, we want to _list initialize_ the object. Only if it is not possible to list initialize the object will the other ways to initialize the object be considered.

```
vector<string> v5{"hi"}; // list initialization: v5 has one element  
vector<string> v6("hi"); // error: can't construct a vector from a string literal  
vector<string> v7{10};       // v7 has ten default-initialized elements  
vector<string> v8{10, "hi"}; // v8 has ten elements with value "hi"
```

### Vector Operations

![[Vector Operations.png]]

#### adding element to vector

Directly initializing the elements of a `vector` is feasible only if we have a small number of known initial values, if we want to make a copy of another `vector`, or if we want to initialize all the elements to the same value.

As one example, if we need a `vector` with values from 0 to 9, we can easily use list initialization. What if we wanted elements from 0 to 99 or 0 to 999? List initialization would be too unwieldy. In such cases, it is better to create an empty `vector` and use a `vector` member named `push_back` to add elements at run time.

```
vector<int> v2;        // empty vector  
for (int i = 0; i != 100; ++i)  
    v2.push_back(i);    // append sequential integers to v2
```

### grow efficiency

`vector grows with amortized runtime O(n)`

The standard requires that `vector` implementations can efficiently add elements at run time. Because `vector`s grow efficiently, it is often unnecessary—and can result in poorer performance—to define a `vector` of a specific size. The exception to this rule is if _all_ the elements actually need the same value. If differing element values are needed, it is usually more efficient to define an empty `vector` and add elements as the values we need become known at run time.

The fact that we can easily and efficiently add elements to a `vector` greatly simplifies many programming tasks. However, this simplicity imposes a new obligation on our programs: **We must ensure that any loops we write are correct even if the loop changes the size of the `vector`**.


#### other operations

To use `size_type`, we must name the type in which it is defined. A `vector` type _always_ includes its element type

```
vector<int>::size_type // ok  
vector::size_type      // error
```

We can compare two `vector`s only if we can compare the elements in those `vector`s. Some class types, such as `string`, define the meaning of the equality and relational operators. Others, such as our `Sales_item` class, do not.

**Caution: Subscript Only Elements that are Known to Exist!**

```
vector<int> ivec;      // empty vector  
cout << ivec[0];       // error: ivec has no elements!
```

Attempting to subscript elements that do not exist is, unfortunately, an extremely common and pernicious programming error. So-called **buffer overflow** errors are the result of subscripting elements that don’t exist. Such bugs are the most common cause of security problems in PC and other applications.


#### use array to initialize vector

we noted that we cannot initialize a built-in array from another array. Nor can we initialize an array from a `vector`. However, we can use an array to initialize a `vector`.

```
int int_arr[] = {0, 1, 2, 3, 4, 5};  
// ivec has six elements; each is a copy of the corresponding element in int_arr  
vector<int> ivec(begin(int_arr), end(int_arr));

// copies three elements: int_arr[1], int_arr[2], int_arr[3]  
vector<int> subVec(int_arr + 1, int_arr + 4);
```