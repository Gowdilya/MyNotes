---
Link: https://leetcode.com/discuss/general-discussion/460599/blind-75-leetcode-questions
---
#  [1. Two Sum](https://leetcode.com/problems/two-sum/)

#Complement

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

**Input:** nums = [2,7,11,15], target = 9
**Output:** [0,1]
**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

**Example 2:**

**Input:** nums = [3,2,4], target = 6
**Output:** [1,2]

**Example 3:**

**Input:** nums = [3,3], target = 6
**Output:** [0,1]



> [!NOTE] Complement
> The key idea is to find the complement of the current number (i.e., the difference between the target sum and the current number) and check if that complement exists in the hash map. If it does, we have found a pair of indices whose corresponding numbers add up to the target sum.

This algorithm has a time complexity of O(n) since it only requires a single pass through the array, and the hash map allows constant-time lookups.


[[02_Two Sum - Class Based Solution_py]]
[[02_TwoSum_ts]]
[[02_TwoSum_cs]]

---
#   [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

#GreedyAlgorithm 
You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.

**Example 1:**

**Input:** prices = [7,1,5,3,6,4]
**Output:** 5
**Explanation:** Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

**Example 2:**

**Input:** prices = [7,6,4,3,1]
**Output:** 0
**Explanation:** In this case, no transactions are done and the max profit = 0.

**Constraints:**

- `1 <= prices.length <= 105`
- `0 <= prices[i] <= 104`


> [!NOTE] Greedy Algorithim
> Yes, the algorithm described is a greedy algorithm. Greedy algorithms make locally optimal choices at each step with the hope of finding a global optimum. In the context of this stock trading problem, the algorithm makes a greedy choice by updating the `min_price` to be the minimum encountered so far, and it calculates the potential profit for each day based on this minimum price.

The key insight here is that to maximize the profit, it's optimal to buy the stock at the lowest possible price. By updating the `min_price` at each step, the algorithm makes a locally optimal choice, and by calculating the potential profit, it also keeps track of the globally optimal choice for selling the stock to maximize profit.

While the algorithm is greedy in its approach, it is important to note that not all greedy algorithms are applicable to every problem. In this case, the specific structure of the problem allows for a greedy strategy to find the optimal solution efficiently.

---

[[🧑🏾‍💻 Software Development/LeetCode/_ts/03_BestTimeToBuySellStock_ts]]
[[🧑🏾‍💻 Software Development/LeetCode/c_Sharp/03_BestTimeToBuySellStock_ts|03_BestTimeToBuySellStock_ts]]
# [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

**Input:** nums = [1,2,3,1]
**Output:** true


**Example 2:**

**Input:** nums = [1,2,3,4]
**Output:** false

**Example 3:**

**Input:** nums = [1,1,1,3,3,4,3,2,4,2]
**Output:** true

**Constraints:**

- `1 <= nums.length <= 105`
- `-109 <= nums[i] <= 109`****
---
[[04_ContainsDuplicate_ts]]