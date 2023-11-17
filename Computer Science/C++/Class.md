

### Introduction

Class defines a type along with a collection of operations that are related to that type

To use a class, we need not care about how it is implemented. Instead, what we need to know is what operations objects of that type can perform.

```
struct Sales_data {  
    std::string bookNo;  
    unsigned units_sold = 0;  
    double revenue = 0.0;  
};
```

The close curly that ends the class body must be followed by a semicolon. The semicolon is needed because we can define variables after the class body:

```
struct Sales_data { /* ... */ } accum, trans, *salesptr;
```

The class body defines the `members` of the class

#### why we need defining our own data types

By defining types that mirror concepts in problems we want to solve, we can make our program easier to write, debug and modify

#### fundamental ideas 

- **data abstraction**
    separation of interface and implementation
- **encapsulation**
    enforces separation and hide implementation

A class that uses data abstraction and encapsulation define a `abstract data type`

programmer don't need to know how the type works, instead can think abstractly about what the type does.
### Data member

bookNo, units_sold, revenue are data member of Sales_data

Under the new standard, we can supply an `in-class initializer` for a data member. When we create objects, the in-class initializers will be used to initialize the data members. Members without an initializer are default initialized

### Defining a class

When we define a class outside of a function, there may be only one definition of that class in any given source file. In addition, if we use a class in several different files, the class’ definition must be the same in each file.

In order to ensure that the class definition is the same in each file, classes are usually defined in [[Header File]]. Typically, classes are stored in headers whose name derives from the name of the class

