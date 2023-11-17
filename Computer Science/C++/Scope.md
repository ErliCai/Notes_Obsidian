
At any particular point in a program, each name that is in use refers to a specific entity—a variable, function, type, and so on. However, a given name can be reused to refer to different entities at different points in the program.

A scope is a part of the program in which a name has a particular meaning. Most scopes in C++ are delimited by curly braces.

The same name can refer to different entities in different scopes. Names are visible from the point where they are declared until the end of the scope in which the declaration appears.

### Global Scope

The name `main` is defined outside any curly braces. The name `main`—like most names defined outside a function—has global scope. Once declared, names at the global scope are accessible throughout the program

### Nested Scope

Scopes can contain other scopes. The contained (or nested) scope is referred to as an inner scope, the containing scope is the outer scope

Once a name has been declared in a scope, that name can be used by scopes nested inside that scope. Names declared in the outer scope can also be redefined in an inner scope: