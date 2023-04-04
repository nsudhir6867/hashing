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
	
## [Max distance between same elements](https://practice.geeksforgeeks.org/problems/max-distance-between-same-elements/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)
> Submission code: [Check here](https://practice.geeksforgeeks.org/problems/max-distance-between-same-elements/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)

##### Concept

```
The idea is to traverse the input array and store the index of the first occurrence in a hash map. 
For every other occurrence, find the difference between the index and the first index stored in the hash map.
If the difference is more than the result so far, then update the result.

```

##### Algorithm

```
1. Take a hashmap of type <int, int>
2. Take a variable maximum.
2. Traverse the array and try to find if same element is present in the hashmap or not.
3. if it's not present, insert (nums[i], i) into map and move forward.
4. if it's present, find the difference of indices of both occurence. if difference is greater than the maximum, update maximum.

```

<details><summary>Code</summary>

<p>

	
```C++
class Solution{
    public:
    // your task is to complete this function
    int maxDistance(int arr[], int n)
    {
        unordered_map<int,int> freq;
        int maxi = 0;
        for(int i=0; i<n; i++) {
            if(freq.find(arr[i]) != freq.end()) {
                int distance = i-freq[arr[i]];
                maxi = max(maxi, distance);
            }else freq[arr[i]] = i;
            
        }
        return maxi;
    }
};
	
```
</p>
</details>

## [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)
> Submission code: [Check here](https://leetcode.com/problems/first-unique-character-in-a-string/submissions/927026665/)

##### Concept

```
Storing frequency and then checking which has frequency as 1.

```

##### Algorithm

```
1. Take a hashmap of type <int, int>
2. store the frequency of each character of string.
2. Traverse each character of string and check which character has first occurence with frequency as 1.

```

<details><summary>Code</summary>

<p>

	
```C++
class Solution {
public:
    int firstUniqChar(string s) {
        int unique = -1;
        unordered_map<char, int> freq;
        for(int i=0; i<s.size(); i++) {
            freq[s[i]]++;
        }
        for(int i=0; i<s.size(); i++) {
            if(freq[s[i]]>1) {
                continue;
            }else {
                unique = i;
                return unique;
            }
        }
        return unique;
    }
};
	
```
</p>
</details>
	

	
