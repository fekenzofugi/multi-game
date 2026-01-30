# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
My first idea was using the two loops, but this solution results in a $O(n^2) time complexity. Therefore, the other idea was using a hash table to map each value into an array index. If the difference of the current number in the loop and the target is within the hash table, returns the difference index and the current index, otherwise, add the current value to the hash table.

# Approach
<!-- Describe your approach to solving the problem. -->
Loop through the array, if the difference between the target and current number is within the hash table, return the index of the difference of the hash table and the current index. Else, add the current number and index key-value pair and continue the loop.

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
**for i in nums**: $O(n)$
**hash table search**: $O(1)$
**hash table insert**: $O(1)$

Total time complexity = $O(n)$

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
**hash table**: $O(n)$

# Code
```python3 []
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hash_map = {}
        for i, num in enumerate(nums):
            if target-num in hash_map:
                return [hash_map[target-num], i]
            hash_map[num] = i
```