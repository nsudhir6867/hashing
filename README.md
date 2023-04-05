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
	
## [Find Common Characters](https://leetcode.com/problems/find-common-characters/)
> Submission code: [Check here](https://leetcode.com/problems/find-common-characters/submissions/927047923/)

##### Concept

```
we can take a hashmap of type <char, int> and set the freq of each alphabet to max value of constraint. 
after that we will loop through each character of each word and set the freq to minimum occurrence for each word.
then we will loop throught the hashmap till the freq is zero and push the character into the solution array.

```

##### Algorithm

```
1. Create a hashmap alphaFreq<char, int> and set freq of each letter of alphabet to the maximum value of int or constraint.
2. Loop through each character of each word. create a hashmap freq and store the freq of each character of each word and the set the alphaFreq to the minimum freq of each character of each word.
3. Loop through the alphaFreq and push the character in the solution array until freq becomes 0.

```

<details><summary>Code</summary>

<p>

	
```C++
class Solution {
public:
    vector<string> commonChars(vector<string>& words) {
        unordered_map<char, int> alphaFreq;
        vector<string> solution;
        for(char i='a'; i<='z'; i++) {
            alphaFreq[i] = 1000;
        }
        for(auto w: words) {
            unordered_map<char, int> freq;
            for(auto ch: w) {
                freq[ch]++;
            }
            for(char c='a'; c<='z'; c++) {
                alphaFreq[c] = min(freq[c], alphaFreq[c]);
            }
        }
        for(auto alpha: alphaFreq) {
            while(alpha.second > 0) {
                string a = string(1, alpha.first);
                solution.push_back(a);
                alpha.second--;
            }
        }
        return solution;
    }
};
	
```
</p>
</details>
	

## [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)
> Submission code: [Check here](https://leetcode.com/problems/longest-consecutive-sequence/submissions/928263138/)

##### Concept

```
we can check loop over the array and check if any number that is one less than the current number exists in the array,
if it doesn't exist then we can start counting the sequence from that number.

```

##### Algorithm

```
1. Take two hashmap present and checked of type <int, bool>
2. Iterate over the given array and insert the element and true in present hashmap.
3. Iterate over the given array and check if a number that 1 less than the current number doesn't exist in present 
hashmap and current number is not in the checked hashmap.
4. If it doesn't exist in present hashmap and checked hashmap, then we know that it can be start point of any subsequence.
5. Now we will check if the sequence is present by incrementing the start point, we will also set the checked hashmap to true to for that number.
6. Once the sequence is over, we will check if it's length is maximum or not.
7. We will update the maximum_sequence length.
```

<details><summary>Code</summary>

<p>

	
```C++
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        int longest_chain_conseq;
        unordered_map<int,bool> present;
        unordered_map<int, bool> checked;
        for(auto n: nums) {
            present[n] = true;
        }
        for(int i=0; i<nums.size(); i++) {
            if(!checked[nums[i]] && !present[nums[i]-1]) {
                int current_chain = 0;
                int start = nums[i];
                while(present[start]) {
                    current_chain++;
                    checked[start] = true;
                    start++;
                }
                longest_chain_conseq = max(longest_chain_conseq, current_chain);
            }
        }
        return longest_chain_conseq;
    }
};
	
```
</p>
</details>

## [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)
> Submission code: [Check here](https://leetcode.com/problems/longest-consecutive-sequence/submissions/928263138/)

##### Concept

```

We will use concept of prefix sum
p(r) = sum from 0 to r
p(l-1) = sum from 0 to l-1
p(r) = p(l-1) + Sum(l,r)
if S(l,r) = 0 according to question means p(r) = p(l-1)
we maintain a unordered_map<int,int> to store <prefixSum, first_occurence_index>
we maintain a sum variable = 0, longest_length = 0
we store whole prefix sum in an variable sum = 0 one by one
we store all prefix_sum and first_occ_index in our map.
when we get a prefix_sum we check in map if its not present we store it in the map
if its present, we do that index i - map[that_prefix_sum] i.e map[4] give us first_occ_index for that sum and then we update the longest_length

```

##### Algorithm

```
1. Create an hashmap named firstOccurrence,
2. Create variable sum and maxi to store sum and largest subarray.
3. Iterate over the array and add the element to sum, 
if sum becomes zero, update maxi with i+1, else check if sum is present in the firstOccurence,
4. If it's present, find the length of of the subarray that is difference between the first occurence and current occurence,
and update the maxi if the subarray length is maximum.
5. If element is not present, then insert it in the firstOccurence.
```

<details><summary>Code</summary>

<p>

	
```C++
class Solution{
    public:
    int maxLen(vector<int>&A, int n)
    {   
        // Your code here
        
        unordered_map<int, int> firstOccurence;
        int sum=0;
        int maxi = 0;
        for(int i=0; i<A.size(); i++) {
            sum+= A[i];
            if(sum == 0) maxi = i+1;
            else {
                if(firstOccurence.find(sum) != firstOccurence.end()) {
                    int len = i-firstOccurence[sum];
                    maxi = max(maxi, len);
                }else firstOccurence[sum] = i;
            }
            
        }
        return maxi;
        
        
        
    }
};

	
```
</p>
</details>
	


