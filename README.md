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

## [Largest subarray with 0 sum](https://practice.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)
> Submission code: [Check here](https://practice.geeksforgeeks.org/problems/largest-subarray-with-0-sum/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)

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
	
## [Count Number of Pairs With Absolute Difference K](https://leetcode.com/problems/count-number-of-pairs-with-absolute-difference-k/description/)
> Submission code: [Check here](https://leetcode.com/problems/count-number-of-pairs-with-absolute-difference-k/submissions/927177323/)

##### Concept

```
let a is an element of given array.
we have to find another element that is k less than a or k greater than a in the given array.

```

##### Algorithm

```
1. Create a hashmap occurence.
2. Iterate over array check for each element if 'element + k' or 'element - k' or both exists in the map,
3. If it doesn't exist, insert the element in the hashmap with its frequency. eg: occurence[nums[i]]++
4. If it exists, increment the count of pair by the frequency of the element.
```

<details><summary>Code</summary>

<p>

	
```C++
class Solution {
public:
    int countKDifference(vector<int>& nums, int k) {
        unordered_map<int,int> occurence;
        int count = 0;
        for(int i=0; i<nums.size(); i++) {
            int pair1 = nums[i]-k;
            int pair2 = nums[i] + k;
            count+=occurence[pair1];
            count+=occurence[pair2];
            occurence[nums[i]]++; 
        }
        return count;
    }
};
	
```
</p>
</details>
	

## [Subarrays with sum K](https://practice.geeksforgeeks.org/problems/subarrays-with-sum-k/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)
> Submission code: [Check here](https://practice.geeksforgeeks.org/problems/subarrays-with-sum-k/1?utm_source=gfg&utm_medium=article&utm_campaign=bottom_sticky_on_article)

##### Concept

```
range =                        l           r
let array arr =  [a1, a2, a3, a4, a5, a6, a7, a8, a9 ]
index =            0   1   2   3   4   5   6   7   8
let 's' be the prefix sum till r.
let 'k' be the prefix sum of subarray from (l to r)
then prefix sum from range ( 0 to 'l-1') will be sum-k;

so at each index, we will have total sum till that index 's',
then we just need to check if there is a prefix which is having sum = 's-k' is present.
if it's present then remaining part till the current index will have sum 'k'.
```

##### Algorithm

```
1. Create a hashmap 'prefixOccurrences' of type <int, int> to store the occurrence of prefixSum and its count.
2. Create a variable 'sum' to keep track of prefix sum.
3. Create a variable 'count' to count the number of subarrays.
4. Loop through the given array and update the prefix sum.
5. Increment the count by number of occurrence of 'sum -k' from the prefixSumOccurrences.
6. Insert the prefix sum and it's current count in the prefixSumOccurrences -> prefixSumOccurences[sum]++;

```

<details><summary>Code</summary>

<p>

	
```C++
class Solution{
    public:
    int findSubArraySum(int Arr[], int N, int k)
    {
        unordered_map<int,int> prefixSumOccurences;
        int sum = 0;
        int count=0;
        for(int i=0; i<N; i++) {
            sum += Arr[i];
            if(sum==k) count++;
            count+=prefixSumOccurences[sum-k];
            prefixSumOccurences[sum]++;
            
        }
        return count;
    }
};
	
```
</p>
</details>
	

## [Longest Consecutive Sequence](https://leetcode.com/problems/longest-palindrome-by-concatenating-two-letter-words/)
> Submission code: [Check here](https://leetcode.com/problems/longest-consecutive-sequence/submissions/928263138/)

##### Concept

```
There is two types of strings.
(i) s[0] == s[1]
(ii) s[0] != s[1]

if we have type(i) string something like -> ["lc" , "cl", "cl" ],
our palindrome will be ("lc cl").
It means if we have reverse of the string present in the array then 
the count of length of palindrome will be min(occurrence["lc"], occurrence["cl"])*2.

if we have type(ii) string something like -> ["gg","gg","gg","gg","gg","ll","ll","ll"]
our palindrome will be ("gg gg ll gg ll gg gg") or ("ll gg gg ll gg gg ll")
It means that 2 different strings of type(ii) occurr in odd number of times, 
then we can use only one string(all 5 "gg" or all 3 "ll") for odd times.
other strings can be used for even times only(4 times "gg" or 2 times "ll")

```

##### Algorithm

```
1. Create a hashmap and store the occurrences of each string present in the array.
2. Create variable to store length of palindrome.
3. Create a count variable,
4. Create a variable flag to check if we have used type(ii) string odd number of times.
5. Iterate over the given array of strings.
	6. if the word is type(i). if it is, create a variable and store the reverse of word in it.
		7. Check in the hashmap if the reverse is present. if it is, find the count = min(occurrence[word], occurrence[reverse])
		8. Update the lenghth.
		9. erase the word and its reverse from the map so that it can not be counted twice.
	9.else if the word is type(ii),
		10. find its occurrence(means count) from hashmap.
		11. if count is even, increment the length by (count*2)
		12. If count is odd, 
			13. If flag is false, increment length by (count*2), set flag to true.
			14. If flag is true, increment length by [(count-1)*2]
		15. Erase the word from hashmap

```

<details><summary>Code</summary>

<p>

	
```C++

int longestPalindrome(vector<string>& words) {
        int len = 0;
        int count = 0;
        bool flag = 0;
        // store all the strings with their number of occurences
        unordered_map<string,int> mp;
        for(int i = 0;i<words.size();i++)
        {
            mp[words[i]]++;
        }
        // now check cases
        for(int i = 0;i<words.size();i++)
        {
            // if s[0] != s[1]
            if(words[i][0] != words[i][1])
            {
              string s = "";
              // store the reverse
              s += words[i][1];
              s += words[i][0];
              // if we find the reverse in the map
              // we take the minimum count
              // we do len = count*4 because each string has 2 characters
              if(mp.find(s) != mp.end())
              {
                count = min(mp[words[i]],mp[s]);
                len += count*4;
              }
              // erase the words which are already counted including the reverse one
              mp.erase(words[i]);
              mp.erase(s);
            }
            // if s[0] == s[1]
            else if(words[i][0] == words[i][1])
            {
                // get number of occurence of such string
                count = mp[words[i]];
                // if that string occur even number of times
                if(mp[words[i]]%2==0)
                {
                    // if its even
                    len += count*2;
                }
                else{
                    // if its odd
                    // flag = 0 means its the first string that occurs odd number of times
                    // if its the first one then we can use all its occurences for our result
                    if(flag==0)
                    {
                      // means its the first string which is equal but odd occurence
                      len += count*2;
                      // make sure to turn the flag=1 because we already have one string with odd number of occurences in our output now
                      flag = 1;
                    }
                    else{
                        // if flag = 1 already then we need to count -1 from the all occurence of that string
                        len += (count-1)*2;
                    }
                }
                // erase that word from the map
                mp.erase(words[i]);
            }
        }
        // return the output length
        return len;
    }
	
```
</p>
</details>
	



