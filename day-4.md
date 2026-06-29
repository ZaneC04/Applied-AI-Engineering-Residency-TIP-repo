# Day 4

Problem: [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/description/) and [Group Anagrams](https://leetcode.com/problems/group-anagrams/)

```js
function containsDuplicate(nums) {
  const seen = new Set();
  for (let i = 0; i < nums.length; i++) {
    if (seen.has(nums[i])) {
      return true;
    }
    seen.add(nums[i]);
  }
  return false;
}

function groupAnagrams(strs) {
  const map = {};
  for (let i = 0; i < strs.length; i++) {
    const key = strs[i].split("").sort().join("");
    if (map[key] === undefined) {
      map[key] = [];
    }
    map[key].push(strs[i]);
  }
  return Object.values(map);
}
```

Input:
Contains Duplicate: List[int] (list of all integers)
Group Anagrams: List[str] (list of all strings)

Output:
Contains Duplicate: bool (true if a integer appears twice in list, false otherwise)
Group Anagrams: List[List[str]] (matrix, each list in each element is a list of anagrams)

Psuedocode:

FUNCTION containsDuplicate(nums)
CREATE seen AS set
FOR EACH num IN nums:
IF num IN seen:
RETURN TRUE
END IF
ADD num TO seen
END FOR
RETURN FALSE
END FUNCTION

FUNCTION groupAnagrams(strs)
CREATE dictionary AS {}
FOR EACH string IN strs:
SET key TO sorted letters of string joined together
IF key NOT IN dictionary:
SET dictionary[key] TO []
END IF
APPEND string TO dictionary[key]
END FOR
RETURN list of values in dictionary
END FUNCTION

Algorithm:
Contains Duplicate:

- create empty set
- loop through the nums list
- if the current num is in the set, return true
- otherwise, add the num to the set
- after the loop, return false

Group Anagrams:

- create empty dictionary
- loop through strs list
- for each string in strs, sort all the letters in the string and save that new string to be our key later
- if the new key does not exist in the dictionary, initialize it in the dictionary with the value of an empty list
- otherwise, add the current string into the current key's list value
- after the loop, return all the lists from the dictionary in a list
- Python Solution:

```py
def containsDuplicate(self, nums: List[int]) -> bool:
        seen = set()
        for num in nums:
            if num in seen:
                return True
            seen.add(num)
        return False

def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        dictionary = {}
        for string in strs:
            key = ''.join(sorted(list(string)))
            if key not in dictionary:
                dictionary[key] = []
            dictionary[key].append(string)
        return list(dictionary.values())
```
