
Although we can use subscripts to access the characters of a `string` or the elements in a `vector`, there is a more general mechanism—known as `iterators` —that we can use for the same purpose.

All of the library containers have iterators, but only a few of them support the subscript operator. Technically speaking, a `string` is not a container type, but `string` supports many of the container operations.

### Iterator operations

![[Iterator Operations.png]]

Unlike pointers, we do not use the address-of operator to obtain an iterator. Instead, types that have iterators have members that return iterators. In particular, these types have members named `begin` and `end`.

#### begin and end

If the object is `const`, then `begin` and `end` return a `const_iterator;` if the object is not `const`, they return `iterator`:

```
// b denotes the first element and e denotes one past the last element in v  
vector<int> v;  
const vector<int> cv;
auto b = v.begin(), e = v.end(); // b and e have the same type
auto it2 = cv.begin(); // it2 has type vector<int>::const_iterator
```

- The iterator returned by `end` is often referred to as the **off-the-end iterator**
- If the container is empty, the iterators returned by `begin` and `end`are equal—they are both off-the-end iterators.

#### moving iterator

**Because the iterator returned from `end` does not denote an element, it may not be incremented or dereferenced.**

#### Iterator Types

Just as we do not know the precise type of a `vector`’s or `string`’s `size_type`member, so too, we generally do not know—and do not need to know—the precise type of an iterator. Instead, as with `size_type`, the library types that have iterators define types named `iterator` and `const_iterator`that represent actual iterator types:

```
vector<int>::iterator it; // it can read and write vector<int> elements  
string::iterator it2;     // it2 can read and write characters in a string  
vector<int>::const_iterator it3; // it3 can read but not write elements
```

To let us ask specifically for the `const_iterator` type, the new standard introduced two new functions named `cbegin` and `cend`:

```
auto it3 = v.cbegin(); // it3 has type vector<int>::const_iterator
```

####  Combining Dereference and Member Access

Without parentheses, the dot operator would apply to `it`, not to the resulting object:

```
(*it).empty() // dereferences it and calls the member empty on the resulting object  
*it.empty()   // error: attempts to fetch the member named empty from it  
              //     but it is an iterator and has no member named empty
```

The arrow operator combines dereference and member access into a single operation. That is, `it->mem` is a synonym for `(* it).mem`.



### Iterator Arithmetic 

We can also subtract two iterators so long as they refer to elements in, or one off the end of, the same `vector` or `string`. The result is the distance between the iterators. By distance we mean the amount by which we’d have to change one iterator to get the other. The result type is a signed integral type named `difference_type` . Both `vector` and `string` define `difference_type`. This type is signed, because subtraction might have a negative result.