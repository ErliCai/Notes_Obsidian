When we initialize a variable using =, we are asking the compiler to **copy initialize** the object by copying the initializer on the right-hand side into the object being created

Otherwise, when we omit the =, we use **direct initialization**.

```
string s5 = "hiya"; // copy initialization  
string s6("hiya"); // direct initialization
string s7(10, 'c'); // direct initialization;
string s8 = string(10, 'c'); // copy initialization;
```

