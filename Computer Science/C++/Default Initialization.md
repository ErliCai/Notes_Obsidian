When we define a variable without an initializer, the variable is default initialized

Variables defined outside any function body are initialized to zero

With one exception, variables of built-in type defined inside a function are uninitialized. The value of an uninitialized variable of built-in type is undefined. It is an error to copy or otherwise try to access the value of a variable whose value is undefined.

Each class controls how we initialize objects of that class type. In particular, it is up to the class whether we can define objects of that type without an initializer. If we can, the class determines what value the resulting object will have.