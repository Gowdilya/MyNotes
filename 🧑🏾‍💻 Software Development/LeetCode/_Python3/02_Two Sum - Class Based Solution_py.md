Given List of numbers and a target return index of 2 numbers that add up to the target

```python
from typing import List

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # Create a dictionary to store the complement of each number and its index
        num_dict = {}
        
        for i, num in enumerate(nums):
            complement = target - num
            
            # Check if the complement is in the dictionary
            if complement in num_dict:
                # Return the indices of the two numbers that add up to the target
                return [num_dict[complement], i]
            
            # If not found, add the current number and its index to the dictionary
            num_dict[num] = i
        
        # If no solution is found
        return None

# Example usage:
solution = Solution()
nums = [7, 11, 15, 2]
target = 9
result = solution.twoSum(nums, target)
print(result);
```

