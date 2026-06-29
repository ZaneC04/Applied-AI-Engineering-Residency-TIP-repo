Problem: [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)

Input: s: str, t: str (2 strings of different lengths)

Output: str (minimum window substring of s that includes every character in t with duplicates included)

Algorithm:

- with an edge case, check if s and t are empty or the length of s is more than t
- if so, return an empty string
- create a counter dictionary for all the characters in t
- set a variable for the amount of characters in t, which will be from the amount of keys in the t counter
- initialize an empty counter for s
- initialize a match variable to 0 and answer to an empty string
- initalize two pointers, starting at 0 and -1 respectively
- while the left pointer starting at 0 is less than the length of s, loop
- if the match variable is less than the amount of characters then check if j is equal to the length of s minus 1 (the last character)
- if so, return the answer
- then increment the right pointer and the j-th character in s in the s counter
- then if the t counter has a value of more than 0 for the j-th character in the s counter AND the s count value is the same as the t count value, increment the match variable
- if the match is higher than the amount of characters, decrement the i-th character in the s count
- then check if the t count for the i-th character is more than zero AND the s count of the i-th character is equal to the t count of the i-th character minus 1
- if so, decrement the match variable
- after that check, increment i
- after the check of match and characters, check if match is equal to characters
- then check is the answer is empty, if so have the answer be the s string starting at i and ending at j plus 1
- otherwise check if j minus i plus 1 is less than the length of answer
- if so, do the same logic for if the answer is empty
- after the loop, return the answer

Psuedocode:
FUNCTION minWindow(s, t)
    IF s IS empty OR t IS empty OR LENGTH OF s LESS THAN LENGTH OF t:
        RETURN ""
    END IF

    CREATE t_count AS counter of characters in t
    SET chars TO LENGTH OF keys in t_count

    CREATE s_count AS {}
    SET match TO 0
    SET answer TO ""

    SET i TO 0
    SET j TO -1

    WHILE i LESS THAN LENGTH OF s:
        IF match LESS THAN chars:
            IF j EQUALS LENGTH OF s - 1:
                RETURN answer
            END IF

            INCREMENT j
            INCREMENT s_count[s[j]]
            IF t_count[s[j]] GREATER THAN 0 AND s_count[s[j]] EQUALS t_count[s[j]]:
                INCREMENT match
            END IF
        ELSE
            DECREMENT s_count[s[i]]
            IF t_count[s[i]] GREATER THAN 0 AND s_count[s[i]] EQUALS t_count[s[i]] - 1:
                DECREMENT match
            END IF
            INCREMENT i
        END IF

        IF match EQUALS chars:
            IF answer IS empty:
                SET answer TO substring of s FROM i TO j
            ELSE IF (j - i + 1) LESS THAN LENGTH OF answer:
                SET answer TO substring of s FROM i TO j
            END IF
        END IF
    END WHILE

    RETURN answer
END FUNCTION

Solution:

```py
def minWindow(self, s: str, t: str) -> str:
        if not s or not t or len(s) < len(t):
            return ''

        t_count = Counter(t)
        chars = len(t_count.keys())

        s_count = Counter()
        match = 0

        answer = ''

        i = 0
        j = -1

        while i < len(s):

            if match < chars:
                if j == len(s) - 1:
                    return answer

                j += 1
                s_count[s[j]] += 1
                if t_count[s[j]] > 0 and s_count[s[j]] == t_count[s[j]]:
                    match += 1

            else:
                s_count[s[i]] -= 1
                if t_count[s[i]] > 0 and s_count[s[i]] == t_count[s[i]] - 1:
                    match -= 1
                i += 1

            if match == chars:
                if not answer:
                    answer = s[i:j+1]
                elif (j - i + 1) < len(answer):
                    answer = s[i:j+1]

        return answer
```
