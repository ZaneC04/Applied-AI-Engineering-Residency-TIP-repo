# Day 1

Problem: FizzBuzz

leetcode link: https://leetcode.com/problems/fizz-buzz/

Psuedocode:

FUNCTION fizzBuzz(n)
    CREATE result AS []
    FOR num FROM 1 TO n:
        IF num MOD 15 EQUALS 0:
            APPEND "FizzBuzz" TO result
        ELSE IF num MOD 3 EQUALS 0:
            APPEND "Fizz" TO result
        ELSE IF num MOD 5 EQUALS 0:
            APPEND "Buzz" TO result
        ELSE
            APPEND num converted to string TO result
        END IF
    END FOR
    RETURN result
END FUNCTION

```js
function fizzBuzz(n) {
  const result = [];
  for (let i = 1; i <= n; i++) {
    if (i % 15 === 0) {
      result.push("FizzBuzz");
    } else if (i % 3 === 0) {
      result.push("Fizz");
    } else if (i % 5 === 0) {
      result.push("Buzz");
    } else {
      result.push(String(i));
    }
  }
  return result;
}
```

Input:
n = int

Output:
List[str] (List of strings of "FizzBuzz", "Fizz", "Buzz" or integer as a string)

Algorithm:

- Create result list
- Loop from 1 to including n
- If the current num is divisible by 15, add 'FizzBuzz' to the result list
- If the current num is divisible by 3, add 'Fizz' to the result list
- If the current num is divisible by 5, add 'Buzz' to the result list
- if none of these are true, add the integer version of the number to the list
- return the list of strings
  Python Solution:

```py
def fizzBuzz(self, n: int) -> List[str]:
  result = []
  for num in range(1, n+1):
    if num % 15 == 0:
      result.append('FizzBuzz')
    elif num % 3 == 0:
      result.append('Fizz')
    elif num % 5 == 0:
      result.append('Buzz')
    else:
      result.append(str(num))
  return result
```
