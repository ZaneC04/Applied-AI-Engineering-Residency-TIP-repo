Problem: [4Sum II](https://leetcode.com/problems/4sum-ii/description/)

Input: List[int] (4 lists of integers)

Output: int (amount of tuples where one number of each list equals to 0)

Psuedocode:
FUNCTION fourSumCount(nums1, nums2, nums3, nums4)
    CREATE hm AS {}
    SET res TO 0

    FOR EACH a IN nums1:
        FOR EACH b IN nums2:
            SET first_sum TO 0 - a - b
            IF first_sum NOT IN hm:
                SET hm[first_sum] TO 1
            ELSE
                INCREMENT hm[first_sum]
            END IF
        END FOR
    END FOR

    FOR EACH c IN nums3:
        FOR EACH d IN nums4:
            SET second_sum TO c + d
            IF second_sum IN hm:
                SET res TO res + hm[second_sum]
            END IF
        END FOR
    END FOR

    RETURN res
END FUNCTION

Algorithm:

- initialize a empty hash map and the result which starts at 0
- loop through the first nums list
- in that loop, loop through the second nums list and get the first sum of two needed nums through rearranging
  a + b + c + d == 0 to c + d == -(a - b)
- if this sum exists in the hash map, increment it
- otherwise initialize it in the hash map
- after these loops, loop through the third nums list and the fourth nums list nested
- in the fourth loop, get the second sum of the third and fourth lists
- add the amount of the times that sum (the sum's value in the hash map) has appeared to the result
- return the result
  Solution:

```py
def fourSumCount(self, nums1: List[int], nums2: List[int], nums3: List[int], nums4: List[int]) -> int:
        hm, res = {}, 0
        for a in nums1:
            for b in nums2:
                first_sum = 0 - a - b
                if first_sum not in hm:
                    hm[first_sum] = 1
                else:
                    hm[first_sum] += 1

        for c in nums3:
            for d in nums4:
                second_sum = c + d
                if second_sum in hm:
                    res += hm[second_sum]
        return res
```
