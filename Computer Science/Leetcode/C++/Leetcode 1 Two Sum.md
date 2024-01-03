
Brute Force:
```
#include <vector>

using namespace std;

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        for (int i=0; i<nums.size(); i++){
            for (int j=i+1; j<nums.size(); j++){
                if (nums[i] + nums[j] == target){
                    return {i,j};
                }
            }
        }
    }
};
```

Hash Table:
```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int,int> m;
        for (int i=0; i<nums.size(); i++){
            if (m.count(target - nums[i]) > 0){
                return {i, m[target - nums[i]]};
            }
            else{
                m[nums[i]] = i;
            }
        }
        return {};
    }
};
```