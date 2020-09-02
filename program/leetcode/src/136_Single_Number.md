# 136. Single Number

Given a non-empty array of integers, every element appears twice except for one. Find that single one.  
给定一个非空的整数数组，除了一个元素外每个元素都会出现两次。 找那个单一的元素。 

Note:
Your algorithm should have a linear runtime **complexity**. Could you **implement** it without using extra memory?  
您的算法应具有线性运行时**复杂性**。 你能不用额外的内存来**实现**吗？

>Example 1:  
> Input: [2,2,1]  
> Output: 1  

>Example 2:  
> Input: [4,1,2,1,2]  
> Output: 4  

```python
# Runtime: 1176 ms    Memory：14.9 MB
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        no_duplicate_list = []
        for i in nums:
            if i not in no_duplicate_list:
                no_duplicate_list.append(i)
            else:
                no_duplicate_list.remove(i)
        return no_duplicate_list.pop()
```

```python
# Runtime: 48 ms    Memory：15.2 MB
class Solution:  # 通过values搜索keys，但是values和keys都需要是唯一对应的
    def singleNumber(self, nums: List[int]) -> int:
        dict = {}
        for i in nums:
            if i not in dict:
                dict[i] = 1
            else:
                dict[i] += 1
        return list(dict.keys())[list(dict.values()).index(1)]  
```

```python
# Runtime: 44 ms    Memory：15.2 MB
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        hash_table = {}
        for i in nums:
            try:
                hash_table.pop(i)
            except:
                hash_table[i] = 1
        return hash_table.popitem()[0]  # 随机返回并删除字典中的一对键和值，由于最后只会有一对，相当于取值
```


下面是数学的方法，因为只有1个值是单数，可以通过set去除掉所有重复值。2∗(a+b+c)−(a+a+b+b+c)=c
```python
# Runtime: 36 ms    Memory：14.9 MB
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        return 2 * sum(set(nums)) - sum(nums)
```


下面是位操作的方法，a⊕b⊕a=(a⊕a)⊕b=0⊕b=b
```python
# Runtime: 36 ms    Memory：14.9 MB
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        a = 0
        for i in nums:
            a ^= i
        return a
```