The preprocessor—which C++ inherits from C—is a program that runs before the compiler and changes the source text of our programs

### include

When the preprocessor sees a #include, it replaces the #include with the contents of the specified header.

### header guard

```
#ifndef SALES_DATA_H 
#define SALES_DATA_H

#include <string> 
struct Sales_data {
std::string bookNo; 
unsigned units_sold = 0; 
double revenue = 0.0;
};

#endif
```

Preprocessor variables, including names of header guards, must be unique throughout the program.

Typically we ensure uniqueness by basing the guard’s name on the name of a class in the header.