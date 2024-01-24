
```ts
function twoSum(nums: number[], target: number): number[] | null {
    // Create a Map to store the complement of each number and its index
    const numMap = new Map<number, number>();

    for (let i = 0; i < nums.length; i++) {
      const complement = target - nums[i];

      // Check if the complement is in the Map
      if (numMap.has(complement)) {
        // Return the indices of the two numbers that add up to the target
        return [numMap.get(complement)!, i];
      }

      // If not found, add the current number and its index to the Map
      numMap.set(nums[i], i);
    }

    // If no solution is found
    return null;
  }

// Example usage:
const nums = [2, 7, 11, 15];
const target = 9;

const result = twoSum(nums, target);

if (result !== null) {
  console.log(`The indices of the two numbers that add up to ${target} are: [${result[0]}, ${result[1]}]`);
} else {
  console.log("No solution found.");
}```