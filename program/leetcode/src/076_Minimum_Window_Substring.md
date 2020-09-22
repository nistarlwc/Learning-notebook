76. Minimum Window Substring 最小覆盖子串  
Hard

Given a string S and a string T, find the minimum window in S which will contain all the characters in T in complexity O(n).  
给你一个字符串 S、一个字符串 T 。请你设计一种算法，可以在 O(n) 的时间复杂度内，从字符串 S 里面找出：包含 T 所有字符的最小子串。  

Example:
>Input: S = "ADOBECODEBANC", T = "ABC"
>Output: "BANC"

Note:
    If there is no such window in S that covers all characters in T, return the empty string "".  
    如果 S 中不存这样的子串，则返回空字符串 ""  
    If there is such window, you are guaranteed that there will always be only one unique minimum window in S.  
    如果 S 中存在这样的子串，我们保证它是唯一的答案。  

### 解题思路  
滑动窗口是双指针的高级技巧，首先得定义两个指针，left和right，在窗口[left, right]中寻找符合题意的解，如何寻找这样的解即滑动窗口的核心思想。就题解题：  
1、首先定义两个字典window和need，need记录T，window记录窗口中的字符出现次数  
2、首先让右指针不断向右走，直至窗口中包含了T中所有元素  
3、再不断缩短窗口，即让左指针也向右走，每走一步更新一下最新结果，直至走到窗口中不包含T中所有元素  
4、重复2、3步骤直至右指针走到最右  
上面的大致思路就是先找到一个符合包含T中所有元素的解（右指针右移），再去优化（左指针左移）这个解直至最优（最小子串）。滑动窗口的思想是比较好理解的，关键是实现起来需要注意一些细节和小技巧。  

``` python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        dict_window = {}
        dict_t = {}
        for str_t in t:
            dict_t[str_t] = dict_t.get(str_t, 0) + 1
        print("dict_t: ", dict_t)
        
        left = 0
        right = 0
        minlen = float('inf') # 定义一个最大值
        match = 0
        print("minlen: ", minlen)
        while right < len(s):
            c1 = s[right]
            if c1 in dict_t:		
                dict_window[c1] = dict_window.get(c1, 0) + 1     # 将匹配的字符加入windows
                if dict_window[c1] == dict_t[c1]:
                    match += 1              # c1出现次数符合要求，匹配计数+1
            right += 1                  	# 右指针右移
            
            while match == len(dict_t):   # window中字符串符合要求
                if right - left < minlen:		# 更新最小子串结果
                    start = left
                    minlen = right - left
                c2 = s[left]
                if c2 in dict_t:
                    if dict_window[c2] == dict_t[c2]:
                        match -= 1
                    dict_window[c2] -= 1			# 这里是个小技巧
                left += 1					# 左指针左移
                
        return '' if minlen == float('inf') else s[start:minlen+start]
            
```
