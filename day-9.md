Problem: [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/description/)

Input: List[int] (list of integers), int (int that subarrays should equal to)

Output: int (amount of subarrays whose sum equals k)

Algorithm:

- initalize a hash map with the default value as an int, to avoid keyErrors
- initalize the first index with 1, handling if the first index is equal to k
- initalize the current sum and result as zero
- loop through the list
- add the current num to the current sum
- add the value of current sum minus k from the hash map to the result, which will default to zero if it doesn't exist
- increment the value of the current sum in the hashmap by 1
- after the loop, return the result

Solution:

```py
def subarraySum(self, nums: List[int], k: int) -> int:
    from collections import defaultdict
    count = defaultdict(int)
    count[0] = 1
    curr_sum = 0
    res = 0
    for num in nums:
        curr_sum += num
        res += count[curr_sum - k]
        count[curr_sum] += 1
    return res
```
