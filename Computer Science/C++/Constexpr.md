Variables declared as `constexpr` are implicitly `const` and must be initialized by constant expressions:

```
constexpr int mf = 20;        // 20 is a constant expression  
constexpr int limit = mf + 1; // mf + 1 is a constant expression  
constexpr int sz = size();    // ok only if size is a constexpr function
```

### Literal type
Because a constant expression is one that can be evaluated at compile time, there are limits on the types that we can use in a `constexpr` declaration. The types we can use in a `constexpr` are known as “literal types” because they are simple enough to have literal values.

arithmetic, reference, and pointer types are literal types

Although we can define both pointers and reference as `constexpr`s, the objects we use to initialize them are strictly limited. 

We can initialize a `constexpr` pointer from the `nullptr` literal or the literal (i.e., constant expression) `0`. We can also point to (or bind to) an object that remains at a fixed address.

variables defined inside a function ordinarily are not stored at a fixed address. Hence, we cannot use a `constexpr`pointer to point to such variables.

### Pointers and `constexpr`

It is important to understand that when we define a pointer in a `constexpr` declaration, the `constexpr` specifier applies to the pointer, not the type to which the pointer points:

```
const int *p = nullptr;     // p is a pointer to a const int  
constexpr int *q = nullptr; // q is a const pointer to int
constexpr const int *p = &i; // p is a constant pointer to the const int i
```

