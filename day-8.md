Problem: [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/description/)

Input: List[int] (List of integers)

Output: int (length of longest consecutive sequence)

Algorithm:

- create a set of nums
- initialize a variable to count the longest sequence
- loop through nums and check each loop if the current num minus 1 is not in the set
- if its not, then set the current length to 0
- then, while the current num plus the current length is in the set, add 1 to the current length
- after, compare the current length to the overall longest sequence and set the bigger one to the overall longest sequence
- return the longest overall sequence
  Solution:

```py
def longestConsecutive(self, nums: List[int]) -> int:
        num_set = set(nums)
        longest = 0
        for n in nums:
            if n - 1 not in num_set:
                length = 0
                while n + length in num_set:
                    length += 1
                longest = max(length, longest)
        return longest
```
