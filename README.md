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
Note: Always check if target-nums[i] exists in the map before inserting the it into the map, because if you check after inserting, 
you will find the same element for 6 in the map.
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
	
	
## [Cumulative Sum Query ](https://www.spoj.com/problems/CSUMQ/)
> Submission code: [Check here](https://www.spoj.com/status/CSUMQ,nsudhir/)

##### Concept

```

Input: arr[] = {10, 20, 10, 5, 15}
Output: prefixSum[] = {10, 30, 40, 45, 60}
Explanation: While traversing the array, update the element by adding it with its previous element.
prefixSum[i] = prefixSum[i-1] + arr[i],
prefixSum[0] = 10, 
prefixSum[1] = prefixSum[0] + arr[1] = 30, 
prefixSum[2] = prefixSum[1] + arr[2] = 40 and so on.
	
To get prefixSum in range from l to r, we can get prefixSum[r] and subtract prefixSum[l-1] from it.
prefixSum[l -> r] = prefixSum[r] - prefixSum[l-1],

```

##### Algorithm

```
1. find out prefixSum of given array.
2. find prefixSum[r] and prefixSum[l-1],
3. subtract prefixSum[l-1] from prefixSum[r].
```

<details><summary>Code</summary>

<p>

	
```C++
#include <bits/stdc++.h>
using namespace std;
int main() {
  int N; cin>>N;
  vector<int> nums(N);
  for(int i=0; i<N; i++) cin>>nums[i];
  int Q; cin>>Q;
  vector<int> prefixSum; // 2 1 4 6 3
  prefixSum.push_back(nums[0]);
  for(int i=1; i<N; i++) {
    prefixSum.push_back(prefixSum[i-1] + nums[i]);
  }
  while(Q--) {
    int i, j; cin>>i>>j;
    cout<< prefixSum[j] - prefixSum[i-1]<<endl;
  }
  return 0;
} 
	
```
</p>
</details>
	

	
