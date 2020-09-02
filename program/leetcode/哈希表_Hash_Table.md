# 哈希表

## 原理  
使用哈希表可以进行非常快速的查找操作，查找时间为常数，同时不需要元素排列有序；python的内建数据类型：字典，就是用哈希表实现的。  
python中的这些东西都是哈希原理：字典(dictionary)、集合(set)、计数器(counter)、默认字典Defaut dict)、有序字典(Order dict)。  

## leetcode题目：
### Easy   
[001. Two Sum](src/001_Two_Sum.md)    
哈希基础  

[167. Two Sum II - Input array is sorted](src/167_Two_Sum_II-Input_array_is_sorted.md)    
哈希基础，与 “1. Two Sum ” 算法无本质区别 

[136. Single Number](src/136_Single_Number.md)    
找出唯一一个出现单次的数字，方法很多。值得反复看


[202. Happy Number](src/202_Happy_Number.md)    
这道题定义了一种快乐数，就是说对于某一个正整数，如果对其各个位上的数字分别平方，然后再加起来得到一个新的数字，再进行同样的操作，如果最终结果变成了1，则说明是快乐数，如果一直循环但不是1的话，就不是快乐数。
