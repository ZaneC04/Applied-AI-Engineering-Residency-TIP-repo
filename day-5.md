# Day 5

Problem: [Palindrome Number](https://leetcode.com/problems/palindrome-number/) and [3Sum](https://leetcode.com/problems/3sum/)

```js
function isPalindrome(x) {
  if (x < 0) return false;
  const str = x.toString();
  let left = 0;
  let right = str.length - 1;
  while (left < right) {
    if (str[left] !== str[right]) return false;
    left++;
    right--;
  }
  return true;
}

function threeSum(nums) {
  const result = [];
  nums.sort((a, b) => a - b);
  for (let i = 0; i < nums.length - 2; i++) {
    if (i > 0 && nums[i] === nums[i - 1]) continue;
    let left = i + 1;
    let right = nums.length - 1;
    while (left < right) {
      const sum = nums[i] + nums[left] + nums[right];
      if (sum === 0) {
        result.push([nums[i], nums[left], nums[right]]);
        while (left < right && nums[left] === nums[left + 1]) left++;
        while (left < right && nums[right] === nums[right - 1]) right--;
        left++;
        right--;
      } else if (sum < 0) {
        left++;
      } else {
        right--;
      }
    }
  }
  return result;
}
```

Input:
Palindrome Number: int (integer)
3Sum: List[int] (list of integers)

Output:
Palindrome Number: bool (true if palindrome, false if not)
3Sum: List[List[int]] (List of list of triplets that add up to similar with no duplicate integers)

Algorithm:
Palindrome Number:

- check if the integer is less than zero, if so return false
- turn the integer into a string
- set a left pointer starting at zero and a right pointer starting at the end of the string
- while the left pointer is less than the right, loop
- if the current left element is not equal to the current right element, return false
- after the check, increment left and decrement right
- after the loop, return true

3Sum:

- create a result list
- sort the nums list in ascending order
- create a loop starting at zero and ending at the length of the list minus two
- in the loop, check if the index is more than zero and the current num is equal to the previous num
- if so, skip this loop
- otherwise, set the left pointer to the current index plus one and the right to the last element in the list
- then while the left pointer is less than the right, loop
- set a sum variable to the current num, the left pointer num and the right pointer num added together
- if the sum makes 0, push the three nums into the result list in a list
- then while left is less than right and left is equal to the next num and right is equal to the last num, increment and decrement left and right respectively
- if this isnt true, icrement and decrement left and right
- if the sum is less than zero, increment left
- otherwise, decrement right
- return the result list after the most outer loop

- Python Solution:

```py
def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False
        string = str(x)
        left = 0
        right = len(string) - 1
        while left < right:
            if string[left] != string[right]:
                return False
            left += 1
            right -= 1
        return True

def threeSum(self, nums: list[int]) -> list[list[int]]:
        res = []
        nums.sort()
        for i in range(len(nums)-2):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            left = i + 1
            right = len(nums) - 1
            while left < right:
                summed = nums[i] + nums[left] + nums[right]
                if summed == 0:
                    res.append([nums[i], nums[left], nums[right]])
                    while left < right and nums[left] == nums[left+1]:
                        left += 1
                    while left < right and nums[left] == nums[left+1]:
                        right -= 1
                    left += 1
                    right -= 1
                elif summed < 0:
                    left += 1
                else:
                    right -= 1
        return res
```
