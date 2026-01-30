# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
When I saw the problem, my first idea was to check the if the element was already inserted in a new array. But this idea turned out to be not efficient. Then I went to study hash tables and learned about the `set` collection in Python. Which is a hash table where only the keys are stored, then there are no duplicates in the collection. Based on this idea, the idea was to create a set based on the elements of the input array and if the length of the `set` is different from the input array, the function should return `True` because it means that there are duplicate elements in the array, otherwise, if the length is the same for both collections, the function should return `False`, because there is no duplicates in the array.

# Approach
<!-- Describe your approach to solving the problem. -->
The approach was to use the `set` collection feature of storing only different values. Based on that create a set based on the input array, and compare its length. 

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
$O(n)$, insertion in hash-based data structures are contant time $O(1)$, based on that, for n numbers in the array, on average the time complexity should be $O(n)$.

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$O(n)$, it occupates in memory $O(n)$ because a hash-table have a known size array to store the values.


# Code
```python3 []
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(set(nums)) != len(nums)
```