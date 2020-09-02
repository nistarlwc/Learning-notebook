# 202. [Happy Number](https://leetcode.com/problems/happy-number/)

hash搜索法：无限循环只到出现于之前相同的值

```python
# Runtime: 32 ms    Memory Usage: 13.3 MB
class Solution:
    def isHappy(self, n: int) -> bool:
        num_dict = {} 
        flag = False
        while True: 
            num_dict[n] = True 
            sum = 0 
            while(n>=1): 
                sum += (n%10)**2
                n = int( n/10 ) 
            if sum == 1: 
                flag =  True 
                break
            elif sum in num_dict: 
                break
            else: 
                n = sum
        return flag
```