
1: using while loop

```
int main(){
    int sum = 0, value = 0;

    // read until end-of-file, calculating a running total of all values read
    while (cin >> value)
        sum += value; // equivalent to sum = sum + value

    cout << "Sum is: " << sum << endl;
}
```

explanation: When we use an [[IOStream|istream]] as a condition, the effect is to test the state of the stream. If the stream is valid—that is, if the stream hasn’t encountered an error—then the test succeeds. An `istream` becomes invalid when we hit end-of-file or encounter an invalid input, such as reading a value that is not an integer. An `istream` that is in an invalid state will cause the condition to yield false.