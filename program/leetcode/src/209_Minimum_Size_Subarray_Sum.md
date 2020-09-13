# 209. Minimum Size Subarray Sum 长度最小的子数组  
Medium

Given an array of n positive integers and a positive integer s, find the minimal length of a contiguous subarray of which the sum ≥ s. If there isn't one, return 0 instead.  
给定一个含有 n 个正整数的数组和一个正整数 s ，找出该数组中满足其和 ≥ s 的长度最小的 连续 子数组，并返回其长度。如果不存在符合条件的子数组，返回0。  

>Example:   
>Input: s = 7, nums = [2,3,1,2,4,3]  
>Output: 2  
>Explanation: the subarray [4,3] has the minimal length under the problem constraint.  

Follow up:  
If you have figured out the O(n) solution, try coding another solution of which the time complexity is O(n log n).   
如果你已经完成了 O(n) 时间复杂度的解法, 请尝试 O(n log n) 时间复杂度的解法。  

```python
class Solution:
    def minSubArrayLen(self, s: int, nums: List[int]) -> int:
        len_nums = len(nums)
        if len_nums==0:
            return 0
        i,j = 0,1
        sum = nums[i]
        result = len_nums+11
        while i<len_nums-1:
            if sum < s and j<len_nums:
                sum += nums[j]
                j += 1
            else:
                if sum>=s and j-i < result:
                    result = j-i
                sum -= nums[i]
                i+=1
            
        if result == len_nums+11:
            return 0 
        else:
            return result           
```
