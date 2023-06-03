The type `void*` is a special pointer type that can hold the address of any object

```
double obj = 3.14, *pd = &obj;  
// ok: void* can hold the address value of any data pointer type  
void *pv = &obj;  // obj can be an object of any type  
pv = pd;          // pv can hold a pointer to any type
```

There are only a limited number of things we can do with a `void*` pointer: 
- We can compare it to another pointer, 
- we can pass it to or return it from a function, 
- and we can assign it to another `void*` pointer. 

We cannot use a `void*` to operate on the object it addresses—we don’t know that object’s type

