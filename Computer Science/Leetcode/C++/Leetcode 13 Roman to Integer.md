```
#include <string>
#include <map>

using namespace std;

class Solution {
public:
    int romanToInt(string s) {
        map<string, int> twoRomanToInt = {
            {"IV", 4}, {"IX", 9},
            {"XL", 40}, {"XC", 90},
            {"CD", 400}, {"CM", 900}
        };
        map<string, int> oneRomanToInt = {
            {"I", 1}, {"V", 5}, {"X", 10}, {"L", 50},
            {"C", 100}, {"D", 500}, {"M", 1000}
        };
        int ssize = s.size();
        
        int value = 0;
        
        int i = 0;
        while (i < s.size()){
            if (i == ssize-1){
                // if only one digit left
                string subs = s.substr(i, 1);
                value += oneRomanToInt[subs];
                i++;
            }
            else{
                // if two or more digit left
                
                string subs1 = s.substr(i, 1);
                string subs2 = s.substr(i, 2);
                
                if(twoRomanToInt.count(subs2) != 0){
                    // int represent by two roman
                    value += twoRomanToInt[subs2];
                    i+=2;
                } else if(oneRomanToInt.count(subs1) != 0){
                    // int represent by one roman 
                    value += oneRomanToInt[subs1];
                    i++; 
                }
            }
        }
        
        return value;
    }
};
```


```
#include <string>
#include <map>

using namespace std;

class Solution {
public:
    int romanToInt(string s) {
        map<char, int> charToInt = {
            {'I', 1}, {'V', 5}, {'X', 10}, {'L', 50},
            {'C', 100}, {'D', 500}, {'M', 1000}
        };
        int val = 0;
        
        for (int i=0; i<s.size()-1; i++){
            if (charToInt[s[i]] < charToInt[s[i+1]]){
                val -= charToInt[s[i]];
            }
            else{
                val += charToInt[s[i]];
            }
        }
        val += charToInt[s[s.size() - 1]];
        
        return val;
    }
};
```