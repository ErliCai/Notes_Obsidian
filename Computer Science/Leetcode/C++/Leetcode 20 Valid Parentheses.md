
```
class Solution {
public:
    bool isValid(string s) {
        vector<char> vec;
        map<char, char> m{
            {'(',')'}, {'[',']'}, {'{','}'}
        };
        
        for (char c: s){
            if (m.count(c) != 0){
                vec.push_back(c);
            }
            else{
                if (vec.size() == 0){
                    return false;
                }
                char c2 = vec.back();
                if (m.count(c2) == 0 ||c != m[c2]){
                    return false;
                }
                
                vec.pop_back();
            }
        }
        
        return vec.size() == 0;
    }
};
```