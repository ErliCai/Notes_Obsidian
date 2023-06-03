A `constant expression` is an expression whose value cannot change and that can be evaluated at compile time. 

A literal is a constant expression. A `const` object that is initialized from a constant expression is also a constant expression.

In a large system, it can be difficult to determine (for certain) that an initializer is a constant expression. We might define a `const` variable with an initializer that we think is a constant expression. However, when we use that variable in a context that requires a constant expression we may discover that the initializer was not a constant expression.

Under the new standard, we can ask the compiler to verify that a variable is a constant expression by declaring the variable in a [[Constexpr]] declaration.