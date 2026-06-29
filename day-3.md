# Day 3

Problem: [Reverse String](https://leetcode.com/problems/reverse-string/description/) and [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

```js
function reverseString(s) {
  let left = 0;
  let right = s.length - 1;
  while (left < right) {
    let temp = s[left];
    s[left] = s[right];
    s[right] = temp;
    left++;
    right--;
  }
  return s;
}

function lengthOfLongestSubstring(s) {
  let seen = {};
  let left = 0;
  let maxLength = 0;
  for (let right = 0; right < s.length; right++) {
    if (seen[s[right]] !== undefined && seen[s[right]] >= left) {
      left = seen[s[right]] + 1;
    }
    seen[s[right]] = right;
    maxLength = Math.max(maxLength, right - left + 1);
  }
  return maxLength;
}
```

Input:
Reverse String: List[str] (list of letters, all strings)
Longest Substring Without Repeating Characters: str (str of letters)

Output:
Reverse String: List[str] (same list as input but reverse, ['c', 'a', 't'] becomes ['t', 'a', 'c'])
Longest Substring Without Repeating Characters: int (length of longest substring without repeating characters)

Psuedocode:

FUNCTION reverseString(s)
    SET i TO 0
    SET j TO LENGTH OF s - 1
    WHILE i LESS THAN j:
        SWAP s[i] AND s[j]
        INCREMENT i
        DECREMENT j
    END WHILE
    RETURN s
END FUNCTION

FUNCTION lengthOfLongestSubstring(s)
    CREATE seen AS {}
    SET left TO 0
    SET max_length TO 0

    FOR right FROM 0 TO LENGTH OF s - 1:
        IF s[right] IN seen AND seen[s[right]] GREATER THAN OR EQUAL TO left:
            SET left TO seen[s[right]] + 1
        END IF
        SET seen[s[right]] TO right
        SET max_length TO max(max_length, right - left + 1)
    END FOR

    RETURN max_length
END FUNCTION

Algorithm:
Reverse String:

- set variable for front and back of list that start at 0 and the end of the list respectively
- loop until the front reaches the current back of list
- for each loop, reverse the front letter and back letter of the list
- increment front to next letter and decrement back to next letter
- after the loop, return the reversed string

Longest Substring Without Repeating Characters:

- create a dictionary for characters and their last index found
- set variables for the left of the list and the max substring length, both starting at 0
- loop through the list
- check if the current letter has been seen before (exists in the dictionary) and its last index found is less than or equal to the current index,
- if it has been found, change the left variable to the last index the letter was found + 1 (meaning the substring can only be past that letter if it has appeared before now)
- after the check, set the current letter last index found (value in dictionary) to the current index
- compare the max length to the current index minus the left (the current window of substring) plus 1
- set max length to the larger value
- return max length after the loop
  Python Solution:

```py
def reverseString(self, s: List[str]) -> None:
        i = 0
        j = len(s) - 1
        while i < j:
            s[i], s[j] = s[j], s[i]
            i += 1
            j -= 1
        return s

def lengthOfLongestSubstring(self, s: str) -> int:
        seen = {}
        left = 0
        max_length = 0
        for right in range(0, len(s)):
            if s[right] in seen and seen[s[right]] >= left:
                left = seen[s[right]] + 1
            seen[s[right]] = right
            max_length = max(max_length, right - left + 1)
        return max_length
```
