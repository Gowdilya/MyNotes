---
tags:
  - GreedyAlgorithm
  - DSA
  - Array
---
# Slow Solution

```ts
function maxProfit(prices:number[]): number {
    var boughtPrice: number;
    var soldPrice: number;
    var maxProfit:number = 0;
    for (let i = 0;  i < prices.length; i ++){
        boughtPrice = prices[i];
        for (let j = i + 1;  j < prices.length; j ++){
            soldPrice = prices[j];
            let Profit = soldPrice - boughtPrice;
            if(Profit > maxProfit){
                maxProfit = Profit;
            }
        }
    }
    return maxProfit;
}
```

# Optimal Solution using Greedy Algorithm:

```ts
function maxProfit(prices:number[]): number {
    if (prices.length === 0){
        return 0;
    }
    var maxProfit:number = 0;
    var minPrice: number = prices[0];

    for (let i = 1; i < prices.length; i ++){
        // update min price if Current is lower
        minPrice = Math.min(minPrice, prices[i]);

        maxProfit = Math.max(maxProfit, prices[i] - minPrice)
    }
    return maxProfit;
}

var prices = [7,1,5,3,6,4];
console.log(maxProfit(prices));```


The technique used in this solution is often referred to as "greedy algorithm." The basic idea is to make the locally optimal choice at each step with the hope of finding a global optimum.

In this specific problem:

1. **Initialization:** Initialize `minPrice` with the first element of the array and `maxProfit` with zero.
    
2. **Iteration:** Traverse through the array, and at each step:
    
    - Update `minPrice` to be the minimum of the current `minPrice` and the current price.
    - Update `maxProfit` to be the maximum of the current `maxProfit` and the difference between the current price and `minPrice`.

By doing this, you are effectively keeping track of the lowest buying price encountered so far and calculating the potential profit if you sell at the current price. The goal is to maximize the profit by finding the best time to buy and sell the stock.

This greedy approach works well for this problem because you only need to make one transaction (buy once, sell once), and the goal is to find the maximum profit from that single transaction.