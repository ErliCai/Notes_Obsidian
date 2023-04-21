There are several character types, most of which exist to support internationalization.

A `char` is guaranteed to be big enough to hold numeric values corresponding to the characters in the machine’s basic character set. That is, a `char` is the same size as a single machine byte.

The `wchar_t` type is guaranteed to be large enough to hold any character in the machine’s largest extended character set.

The types `char16_t` and `char32_t` are intended for Unicode characters.