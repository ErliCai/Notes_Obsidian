it can be surprisingly difficult—and sometimes even impossible—to determine the type of an expression. Under the new standard, we can let the compiler figure out the type for us by using the `auto` type specifier.

`auto` tells the compiler to deduce the type from the initializer. By implication, a variable that uses `auto` as its type specifier must have an initializer

The type that the compiler infers for `auto` is not always exactly the same as the initializer’s type.  Instead, the compiler adjusts the type to conform to normal initialization rules.

1. when we use a reference as an initializer, the initializer is the corresponding object. The compiler uses that object’s type for `auto`’s type deduction:
   ```
   int i = 0, &r = i;  
   auto a = r;  // a is an int (r is an alias for i, which has type int)
   ```
2.  `auto` ordinarily ignores top-level
   ```
   const int ci = i, &cr = ci;  
    auto b = ci;  // b is an int (top-level const in ci is dropped)  
    auto c = cr;  // c is an int (cr is an alias for ci whose const is top-level)  
    auto d = &i;  // d is an int*(& of an int object is int*)  
    auto e = &ci; // e is const int*(& of a const object is low-level const)
```

If we want the deduced type to have a top-level `const`, we must say so explicitly:
```
const auto f = ci; // deduced type of ci is int; f has type const int
```

