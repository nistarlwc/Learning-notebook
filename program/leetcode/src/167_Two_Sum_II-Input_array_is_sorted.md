# 167. Two Sum II - Input array is sorted

Given an array of integers that is already **sorted in ascending order**, find two numbers such that they add up to a specific target number.  
给定已**按升序排序**的整数数组，找到两个数字，使它们相加到特定的目标数。  
The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.  
函数twoSum应返回两个数字的索引，以便它们加起来到目标，其中index1必须小于index2。  

Note:  
    Your returned answers (both index1 and index2) are not zero-based.  
    您返回的答案（index1和index2）不是从零开始的。  
    You may assume that each input would have exactly one solution and you may not use the same element twice.  
    您可以假设每个输入只有一个解决方案，并且您可能不会两次使用相同的元素。  


>Example:  
>Input: numbers = [2,7,11,15], target = 9  
>Output: [1,2]  
>Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.  

与 [“1. Two Sum ”](001. Two Sum.md) 算法无本质区别

单词：  
**sorted in ascending order**：按升序排序  
**sorted in descending order**：按降序排序

```python
# Runtime: 36 ms    Memory Usage: 13.5 MB
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        hash = {}        
        for i in range(len(numbers)):
            if target - numbers[i] in hash and i != hash[target - numbers[i]]:
                return [hash[target - numbers[i]]+1, i+1]
            hash[numbers[i]] = i
```