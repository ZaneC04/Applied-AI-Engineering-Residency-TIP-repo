Problem: [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/description/)

Input: str, int

Output: int (length of longest string that can be made with repeating characters after turning k amount of characters to a different character)

Algorithm:

- create a frequency counter
- initialize a result and pointer both starting at 0
- loop through the string
- increment the current character in the frequency counter
- get the most common character from all the values in the counter
- get the current length by substracting the current index from the first pointer (i) and adding 1
- if the current length minus the max frequency is more than k, decrement the current character and add to i pointer
- after that check, set the result to the max of the current result versus the current length
- after the loop, return the result

Psuedocode:
FUNCTION characterReplacement(s, k)
CREATE freq AS {}
SET res TO 0
SET i TO 0
FOR j FROM 0 TO LENGTH OF s - 1:
IF s[j] NOT IN freq:
SET freq[s[j]] TO 0
END IF
INCREMENT freq[s[j]]
SET max_freq TO max value in freq
SET curr_len TO j - i + 1
IF curr_len - max_freq GREATER THAN k:
DECREMENT freq[s[i]]
INCREMENT i
END IF
SET res TO max(res, j - i + 1)
END FOR
RETURN res
END FUNCTION

Solution:

```py
def characterReplacement(self, s: str, k: int) -> int:
        freq = defaultdict(int)
        res = 0
        i = 0
        for j in range(len(s)):
            freq[s[j]] += 1
            max_freq = max(freq.values())
            curr_len = j - i + 1
            if curr_len - max_freq > k:
                freq[s[i]] -= 1
                i += 1
            res = max(res, j - i + 1)
        return res
```
