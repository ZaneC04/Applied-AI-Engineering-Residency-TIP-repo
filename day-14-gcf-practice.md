Problems: [Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/description/), [Maximum Number of Vowels in a Substring of Given Length](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/description/), [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/description/)

Inputs:
Running Sum: List[int] (list of integers)
Maximum Number of Vowels: str, int (string of lowercase english letters, length of substrings)
Subarray Sum: List[int], int (list of integers, integer that a subarray's sum should equal to)

Outputs:
Running Sum: List[int] (running sum of input array that adds all previous nums to current num)
Maximum Number of Vowels: int (maximum number of vowels in any substring with length of k)
Subarray Sum: int (total number of subarrays that equal to k)

Algorithms:

- RUNNING SUM:
  create a results list and add the first num of the nums list
  loop through the nums list
  append the sum of the current num in nums list plus the last sum added to the results list
  after the loop, return the nums list

- MAXIMUM NUMBER OF VOWELS:
  create a set of vowels for checking later
  initialize a count for count of vowels in the current window/substring, starting at 0
  loop through the first substring of length k and increment count if there is a vowel at the current character
  set the max count of vowels to the current count
  loop through the entire string starting from the end of the first substring
  if the last character in the leaving character of the substring is a vowel, decrement the count as it is not in the current substring
  if the incoming character in the substring is a vowel, add it to the count as it is included
  if the current count is more than the max count, set the max count to the current count
  if the count is equal to k, then return the count as all letters in the substring are vowels
  after the loop, return the max count

- SUBARRAY SUM:
  create a dictionary with a default value of an integer for each key
  set the 0 key with a value of 1
  set the current sum and the result int to a value of 1
  loop through the nums list
  add the current num to the current sum
  add the value of the current sum minus k in the dictionary to the result
  increment the current sum's value in the dictionary by 1
  after the loop, return the result

Psuedocode:
FUNCTION runningSum(nums)
CREATE res AS [nums[0]]
FOR i FROM 1 TO LENGTH OF nums - 1:
APPEND nums[i] + res[i - 1] TO res
END FOR
RETURN res
END FUNCTION

FUNCTION maxVowels(s, k)
CREATE vowels AS set of "aeiou"
SET count TO 0

    FOR i FROM 0 TO k - 1:
        IF s[i] IN vowels:
            INCREMENT count
        END IF
    END FOR

    SET max_count TO count

    FOR i FROM k TO LENGTH OF s - 1:
        IF s[i - k] IN vowels:
            DECREMENT count
        END IF
        IF s[i] IN vowels:
            INCREMENT count
        END IF

        IF count GREATER THAN max_count:
            SET max_count TO count
        END IF

        IF count EQUALS k:
            RETURN count
        END IF
    END FOR

    RETURN max_count

END FUNCTION

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

Solutions:

```py
def runningSum(self, nums: List[int]) -> List[int]:
        res = [nums[0]]
        for i in range(1, len(nums)):
                res.append(nums[i] + res[i-1])
        return res

def maxVowels(self, s: str, k: int) -> int:
        vowels = set('aeiou')
        count = 0
        for i in range(k):
            if s[i] in vowels:
                count += 1

        max_count = count

        for i in range(k, len(s)):
            if s[i - k] in vowels:
                count -= 1
            if s[i] in vowels:
                count += 1

            if count > max_count:
                max_count = count

            if count == k:
                return count

        return max_count

def subarraySum(self, nums: List[int], k: int) -> int:
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
