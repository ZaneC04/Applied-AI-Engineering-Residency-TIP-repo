Problem: [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/description/)

Input: List[int] (List of integers)

Output: List[int] (list of integers, each one is product of all integers in input minus the current integer)

Psuedocode:
FUNCTION productExceptSelf(nums)
    CREATE answer AS []
    SET left TO 1
    SET right TO 1

    FOR i FROM 0 TO LENGTH OF nums - 1:
        APPEND left TO answer
        SET left TO left * nums[i]
    END FOR

    FOR i FROM LENGTH OF nums - 1 TO 0:
        SET answer[i] TO right * answer[i]
        SET right TO right * nums[i]
    END FOR

    RETURN answer
END FUNCTION

Algorithm:
- create answer list
- declare starting value for left and right products (1)
- loop through the nums list
- for each num, push it into the answer list then multiply the left product by the current num
- loop backwards through list
- make the current index in answer be the right product multiplied by itself
- multiply right product by current number in nums
- return the answer list

Solution:
```py
def productExceptSelf(self, nums: List[int]) -> List[int]:
        answer = [] # answer list
        left = 1 # starting multiplication value
        right = 1 # starting multiplication value
        for i in range(len(nums)): # loop thru list starting at index 0
            answer.append(left) # add the current left product (multiplication)
            left *= nums[i] # multiple left product by current num
        for i in range(len(nums) - 1, -1, -1): # loop backwards through nums
            answer[i] = right * answer[i] # make current index in answer the curr answer times the right
            right *= nums[i] # multiple right product by current num
        return answer
```
