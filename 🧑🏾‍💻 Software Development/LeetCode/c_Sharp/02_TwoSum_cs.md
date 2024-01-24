
```c#

```namespace Algo;

public class Solution{
    public int[] TwoSum(int[] nums, int target){
         // Create a dictionary to store the complement of each number and its index
        Dictionary<int, int> numDict = new Dictionary<int, int>();
        for (int i = 0; i <nums.Length; i ++){
            int complement = target - nums[i];
            if(numDict.ContainsKey(complement)){{
                return new int[] {numDict[complement], i};
            }}
            numDict[nums[i]] = i;
        }
        return null;
    }
}