Part of the compiler’s job is to look for errors in the program text.

A compiler cannot detect whether a program does what its author intends, but it can detect errors in the _form_ of the program.

- [[Syntax error]]
- [[Type Error]]
- [[Declaration errors]]

#### compile with g++ (GNU compiler
)

```
g++ hello_world.cpp -o hello_world   

echo $?    // to obtain status
```

