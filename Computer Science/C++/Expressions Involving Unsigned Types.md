**signed values are automatically converted to unsigned**

if we use both `unsigned` and `int` values in an arithmetic expression, the `int` value ordinarily is converted to `unsigned`.

both expression converted to unsigned:
```
    int i1 = 10;
    int i2 = 42;
    unsigned u1 = 10;
    unsigned u2 = 42;

    std::cout << i1 - u2 << std::endl;
    std::cout << u1 - i2 << std::endl;

output:
4294967264
4294967264
```