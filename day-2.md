# Day 2

Problem: [TwoSum](https://leetcode.com/problems/two-sum/description/) and [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

Psuedocode:

FUNCTION twoSum(nums, target)
FOR i FROM 0 TO LENGTH OF nums - 1:
FOR j FROM i + 1 TO LENGTH OF nums - 1:
IF nums[i] + nums[j] EQUALS target:
RETURN [i, j]
END IF
END FOR
END FOR
RETURN []
END FUNCTION

FUNCTION maxProfit(prices)
SET min_price TO INFINITY
SET max_profit TO 0

    FOR EACH price IN prices:
        IF price LESS THAN min_price:
            SET min_price TO price
        ELSE IF (price - min_price) GREATER THAN max_profit:
            SET max_profit TO price - min_price
        END IF
    END FOR

    RETURN max_profit

END FUNCTION

```js
function twoSum(nums, target) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }
}

function maxProfit(prices) {
  let minPrice = Infinity;
  let maxProfit = 0;
  for (let i = 0; i < prices.length; i++) {
    if (prices[i] < minPrice) {
      minPrice = prices[i];
    } else if (prices[i] - minPrice > maxProfit) {
      maxProfit = prices[i] - minPrice;
    }
  }
  return maxProfit;
}
```

Input:
TwoSum: nums = List[int], target = int
Best Time to Buy and Sell Stock: prices = List[int]

Output:
TwoSum: List[int] (Two indexes of nums that equal target)
Best Time to Buy and Sell Stock: int (max profit)
Algorithm:
Two Sum:

- Loop through the nums list
- For each loop, loop again through nums starting from the next index (If index is 1, start on index 2, etc.)
- Check if the first loop number and nested loop number sum up to the target number
- If they do, return a list with their two indexes
- If no two numbers are found, at the end of the outer loop, return an empty list.

Best Time to Buy and Sell Stock:

- create minimum price and max profit variables starting at infinity and zero respectively
- Loop through prices list
- if the current price in the loop is less than the current minimum price, update minimum price to the current price
- if not, check if the current price minus the minimum price is less than the current maximum price and update the maximum price if so
- After the loop, return the current maximum profit

  Python Solution:

```py
def twoSum(self, nums: List[int], target: int) -> List[int]:
    for i  in range(0, len(nums)):
        for j in range(i+1, len(nums)):
            if nums[i] + nums[j] == target:
                return [i, j]
    return []

def maxProfit(self, prices: List[int]) -> int:
        min_price = inf
        max_profit = 0
        for i, price in enumerate(prices):
            if prices[i] < min_price:
                min_price = prices[i]
            elif prices[i] - min_price > max_profit:
                max_profit = prices[i] - min_price
        return max_profit
```
