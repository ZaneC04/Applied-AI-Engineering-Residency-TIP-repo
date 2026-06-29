Problem: [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/description/)

Input: List[int] (List of integers)

Output: List[int] (List of k most frequent integers)

Psuedocode:

FUNCTION topKFrequent(nums, k)
    CREATE counter AS counter of nums

    IF LENGTH OF keys in counter EQUALS 1:
        RETURN list of keys in counter
    END IF

    SET counter TO counter sorted BY value, descending
    CREATE keys AS list of keys in counter
    RETURN keys FROM 0 TO k
END FUNCTION

Algorithm:

- Create a counter dictionary for each num in nums list
- if there is only one key in the counter dictionary, return that number in a list (only number in list)
- otherwise, create a dictionary of ordered keys from most common to least
- create a list of said dictionary with only the keys
- return the list starting from zero and ending at the k index so the list only includes k amount of elements

Solution:

```py
def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        from collections import Counter
        import operator
        counter = dict(Counter(nums))
        if len(counter.keys()) == 1:
            return list(counter.keys())
        counter = dict(sorted(counter.items(), key=operator.itemgetter(1), reverse=True))
        keys = list(counter.keys())
        return keys[0:k]
```
