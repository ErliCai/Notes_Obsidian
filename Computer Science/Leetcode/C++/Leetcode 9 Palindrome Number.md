First convert int to string,
then use built in function to reverse and string,
and finally compare with original string

```
class Solution {
public:
    bool isPalindrome(int x) {
        string s1 = to_string(x);
        reverse(s1.begin(), s1.end());
        
        string s2 = to_string(x);
        
        return s1 == s2;
    }
};
```

Calculate each digit and store in a vector;

```
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0){
            return false;
        }

        vector<int> v;
        while (x > 0){
            int residue = x%10;
            x = x/10;
            v.push_back(residue);
        }
        for (int i=0; i<v.size()/2; i++){
            cout << v[i] << endl;
            if (v[i] != v[v.size()-i-1]){
                return false;
            }
        }
        return true;
    }
};
```

build another number that has the reverse order
__Since the reversed int might be out of range, we use long to store the reversed int__

```
class Solution {
public:
    bool isPalindrome(int x) {
        long copy_x = x;
        long reversed_x = 0;
        while (x > 0){
            reversed_x *= 10;
            
            int residue = x % 10;
            x = x/10;
            
            reversed_x += residue;
        }
        
        return reversed_x == copy_x;
    }
};
```