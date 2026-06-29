Problem: [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/description/)

Input: List[int] (list of integers), int (int that subarrays should equal to)

Output: int (amount of subarrays whose sum equals k)

Psuedocode:
FUNCTION subarraySum(nums, k)
CREATE count AS {}
SET count[0] TO 1
SET curr_sum TO 0
SET res TO 0

    FOR EACH num IN nums:
        SET curr_sum TO curr_sum + num
        IF (curr_sum - k) NOT IN count:
            SET res TO res + 0
        ELSE
            SET res TO res + count[curr_sum - k]
        END IF
        IF curr_sum NOT IN count:
            SET count[curr_sum] TO 0
        END IF
        INCREMENT count[curr_sum]
    END FOR

    RETURN res

END FUNCTION

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
