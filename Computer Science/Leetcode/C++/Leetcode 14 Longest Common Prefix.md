
```
#include <string>
#include <vector>
#include <iostream>
#include <algorithm>

using namespace std;

class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        char c;
        string rst = "";
        
        string min_str = *min_element(strs.begin(), strs.end());
        int min_length = min_str.size();
        // string min_str = *min_element(strs.begin(), strs.end(), 
        //     [](string &s1, string &s2){return s1 < s2;});    
        
        int longestCommonPrefixLenght = 0;
        for (int i=0; i<min_length; i++){
            bool same = true;
            c = strs[0][i];
            for (string s: strs){
                if (s[i] != c){
                    same = false;
                }
            }
            if (!same){
                break;
            }
            longestCommonPrefixLenght++;
        }
        
        return min_str.substr(0, longestCommonPrefixLenght);
    }
};

```

```
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        string prefix = strs[0];
        
        for (string s: strs){
            while (prefix.size() > 0){
                if (s.find(prefix) == 0){
                    break;
                }
                else{
                    prefix = prefix.substr(0, prefix.size() - 1);
                }
            }
        }
        
        return prefix;
    }
};
```