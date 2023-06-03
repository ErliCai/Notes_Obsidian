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

### Data member

bookNo, units_sold, revenue are data member of Sales_data

Under the new standard, we can supply an `in-class initializer` for a data member. When we create objects, the in-class initializers will be used to initialize the data members. Members without an initializer are default initialized