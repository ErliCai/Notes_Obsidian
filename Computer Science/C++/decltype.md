we want to define a variable with a type that the compiler deduces from an expression but do not want to use that expression to initialize the variable. For such cases, the new standard introduced a second type specifier, `decltype`, which returns the type of its operand

```
decltype(f()) sum = x; // sum has whatever type f returns
```

The way `decltype` handles top-level `const` and references differs subtly from the way `auto` does. When the expression to which we apply `decltype` is a variable, `decltype` returns the type of that variable, including top-level `const`and references:
```
const int ci = 0, &cj = ci;  
decltype(ci) x = 0; // x has type const int  
decltype(cj) y = x; // y has type const int& and is bound to x  
decltype(cj) z;     // error: z is a reference and must be initialized
```

Generally speaking, `decltype` returns a reference type for expressions that yield objects that can stand on the left-hand side of the assignment:
```
// decltype of an expression can be a reference type  
int i = 42, *p = &i, &r = i;  
decltype(r + 0) b;  // ok: addition yields an int; b is an (uninitialized) int  
decltype(*p) c;     // error: c is int& and must be initialized
```
[Here `r` is a reference, so `decltype(r)` is a reference type. If we want the type to which `r` refers, we can use `r` in an expression, such as `r + 0`, which is an expression that yields a value that has a nonreference type.]:

[On the other hand, the dereference operator is an example of an expression for which `decltype` returns a reference. As we’ve seen, when we dereference a pointer, we get the object to which the pointer points. Moreover, we can assign to that object. Thus, the type deduced by `decltype(*p)` is `int&`, not plain `int`.]:#

deduction done by `decltype` _depends on the form of its given expression_. What can be confusing is that enclosing the name of a variable in parentheses affects the type returned by `decltype`

```
// decltype of a parenthesized variable is always a reference  
decltype((i)) d;    // error: d is int& and must be initialized  
decltype(i) e;      // ok: e is an (uninitialized) int
```


