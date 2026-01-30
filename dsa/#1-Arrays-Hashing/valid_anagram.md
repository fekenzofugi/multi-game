# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My idea was to use some kind of hash table to count down the number of keys and the amount of appearences for each `s` and `t` input strings. Then with the hash-table of both strings, compare them, if they are different it's not a anagram and vice-versa.

# Approach
<!-- Describe your approach to solving the problem. -->
To get the number of keys I used the `set` collection which is a hash table that stores only the keys. Them I used `dict.fromkeys(set, value)` function to assign each key of the set to the number of appearences, in this case is 1. With the dict initialized, loop through each string and get the number of appearences for each. Finally, compare both dictionaries. 

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
n = len(s) = len(t)
**set(s)**: $O(1)$ n times -> $O(n)$ 
**set(t)**: $O(1)$ n times -> $O(n)$ 
**fromkeys() method**: $O(n)$, it loops through the length of a set and assign its value in a dict.
**loop s**: $O(1)$ * n -> $O(n)$ 
**loop t**: $O(1)$ * n -> $O(n)$ 
**dict comparison**: 

Total Time Complexity = $O(n) + O(n) + O(n) + O(n) + O(n) + O(n) = O(n)$

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
**Dictionary Size**: $O(n)$

# Code
```python3 []
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        s_d = dict.fromkeys(set(s), 1)
        t_d = dict.fromkeys(set(t), 1)
        for i in range(len(s)):
            s_d[s[i]] += 1
            t_d[t[i]] += 1
        return s_d == t_d
```