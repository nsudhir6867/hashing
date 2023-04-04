## [Two Sum](https://leetcode.com/problems/two-sum/description/)
> Submission code: [Check here](https://leetcode.com/problems/two-sum/submissions/926969861/)

##### Concept

```

let given array nums = [3, 4, 10, 6, 2, 8] and target = 12;
find a and b such that a + b = 12,
if we know one element a = 10;
then 10 + b = 12;
or b = 2,
so if we can find another element b that is 2 in the array then we can say there exists a pair.

```

##### Algorithm

```
1. Take a map of type <int, int>
2. Traverse the array and try to find if element 'target - nums[i]' is present in the map.
3. if it's not present, insert (nums[i], i) into map and move forward.
4. if it's present, push the index of both element into an array and return it.
```

<details><summary>Code</summary>

<p>

	
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> solution;
        unordered_map<int, int> idxMap;
        for(int i=0; i<nums.size(); i++)
        {
            int req = target - nums[i];
            if(idxMap.find(req) != idxMap.end()) {
                solution.push_back(i);
                solution.push_back(idxMap[req]);
                return solution;
            }
            idxMap[nums[i]] = i;
        }
        return {-1,-1};
    }
};
	
```
</p>
</details>
	
