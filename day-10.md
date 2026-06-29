Problem: [Contiguous Array](https://leetcode.com/problems/contiguous-array/description/)

Input: List[int] (list of int that are either 1 or 0)

Output: int (maximum length of a contiguous subarray with an equal number of 0 and 1s)

Psuedocode:
FUNCTION findMaxLength(nums)
SET count TO 0
SET res TO 0
CREATE prefix_sums AS {}
SET prefix_sums[0] TO 0

    FOR i FROM 1 TO LENGTH OF nums:
        SET n TO nums[i - 1]
        IF n EQUALS 0:
            DECREMENT count
        ELSE
            INCREMENT count
        END IF

        IF count IN prefix_sums:
            SET res TO max(res, i - prefix_sums[count])
        ELSE
            SET prefix_sums[count] TO i
        END IF
    END FOR

    RETURN res

END FUNCTION

Algorithm:

- Initialize a count and max length of subarray variables, starting at 0
- initialize a dictionary with an integer as a startig value to avoid keyErrors
- initalize 0 in the dictionary with a value of 0
- loop through the nums list
- if the current num is 0, decrement the count, otherwise increment the count
- if the current count is in the dictionary, get the max between the current max length and the value of count in the dictionary
- otherwise, initialize the count in the dictionary with the current index as the value
- after the loop, return the max length

Solution:

```py
def findMaxLength(self, nums: List[int]) -> int:
        count = 0
        res = 0
        prefix_sums = defaultdict(int)
        prefix_sums[0] = 0
        for i, n in enumerate(nums, 1):
            if n == 0:
                count -= 1
            else:
                count += 1

            if count in prefix_sums:
                res = max(res, i - prefix_sums[count])
            else:
                prefix_sums[count] = i

        return res
```
