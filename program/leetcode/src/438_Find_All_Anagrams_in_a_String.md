# 438. Find All Anagrams in a String
Medium

Given a string s and a non-empty string p, find all the start indices of p's anagrams in s.  
Strings consists of lowercase English letters only and the length of both strings s and p will not be larger than 20,100.   
The order of output does not matter.  
给定一个字符串 s 和一个非空字符串 p，找到 s 中所有是 p 的字母异位词的子串，返回这些子串的起始索引。  
字符串只包含小写英文字母，并且字符串 s 和 p 的长度都不超过 20100。
不考虑答案输出的顺序。 

说明：
字母异位词指字母相同，但排列不同的字符串。

Example 1:  
>Input:  
>s: "cbaebabacd" p: "abc"  
>Output:  
>[0, 6]  

Explanation:  
The substring with start index = 0 is "cba", which is an anagram of "abc".  
The substring with start index = 6 is "bac", which is an anagram of "abc".  

Example 2:  
>Input:  
>s: "abab" p: "ab"  
>Output:  
>[0, 1, 2]  

Explanation:  
The substring with start index = 0 is "ab", which is an anagram of "ab".  
The substring with start index = 1 is "ba", which is an anagram of "ab".  
The substring with start index = 2 is "ab", which is an anagram of "ab".  


思路：设置长度为len(p)的滑动窗；由于没有字母顺序，将其变为数字列表问题

``` python
class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        result = []
        if len(s) < len(p):
            return result
        
        alphabet_p = [0 for _ in range(26)]
        alphabet = [0 for _ in range(26)]
        
        i = 0
        while i < len(p):
            flag = ord(s[i]) - ord("a")
            alphabet[flag] += 1
            flag = ord(p[i]) - ord("a")
            alphabet_p[flag] += 1
            i += 1
        if alphabet == alphabet_p:
            result.append(i-len(p))
    
        while i < len(s):
            flag = ord(s[i]) - ord("a")
            alphabet[flag] += 1
            flag = ord(s[i-len(p)]) - ord("a")
            alphabet[flag] -= 1
            i += 1
            if alphabet == alphabet_p:
                result.append(i-len(p))
            
        return result   
```