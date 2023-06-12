
Header files that we write usually have a suffix of `.h`, but some programmers use `.H`, `.hpp`, or `.hxx`. The standard library headers typically have no suffix at all. 

Compilers usually don’t care about the form of header file names, but IDEs sometimes do.  

Headers (usually) contain entities (such as class definitions and const and constexpr variables) that can be defined only once in any given file.

Because a header might be included more than once (directly and indirectly), we need to write our headers in a way that is safe even if the header is included multiple times.

The most common technique for making it safe to include a header multiple times relies on the [[Preprocessor]]

