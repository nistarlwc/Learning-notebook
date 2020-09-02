# 1. Two Sum

Given an array of integers, return indices of the two numbers such that they **add up to** a specific target.  
给定一个整数数组，返回两个数字的索引，使它们**相加到等于**特定目标。  
You may assume that each input would have **exactly** one solution, and you may not use the same element twice.  
你可以假设每个输入只有一个**准确的**解决方案，并且您不能两次使用相同的元素。  

>Example:  
>Given nums = [2, 7, 11, 15], target = 9,  
>Because nums[0] + nums[1] = 2 + 7 = 9,  
>return [0, 1].  

```python
# Brute Force    Runtime: 52 ms
class Solution:  
    def twoSum(self, nums: List[int], target: int) -> List[int]:  # 暴力搜索
        for i in range(len(nums) - 1):   
            for j in range(i+1, len(nums)):   # 避免不重复搜索
                if nums[i] + nums[j] == target:   
                    return [i, j] 
```
```python
# Two-pass Hash Table  Runtime: 40 ms
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash = {}  # python中dict就是hash的结构
        for i in range(len(nums)):  # 将所有的数据先写入dict词典
            hash[nums[i]] = i
        for i in range(len(nums)):
            if target - nums[i] in hash and i != hash[target - nums[i]]:  # 用in搜索dict速度更快
                    return [i, hash[target - nums[i]]]
```
```python
#  One-pass Hash Table   Runtime: 48 ms
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash = {}        
        for i in range(len(nums)): # 不用将所有的数据都写入dict词典
            if target - nums[i] in hash and i != hash[target - nums[i]]:
                return [hash[target - nums[i]], i]
            hash[nums[i]] = i
```