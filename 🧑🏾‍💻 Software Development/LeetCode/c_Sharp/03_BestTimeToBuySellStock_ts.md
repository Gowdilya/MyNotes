
```c#
namespace Algo;
public class Solution{
  public int BuySellStock_Greedy(int[] prices){
         // If there are no prices
         if(prices.Length == 0){
            return 0;
         }

         int MaxProfit = 0;
         int minPrice = prices[0];
        for (int i = 0; i <prices.Length; i ++){
            minPrice = Math.Min(minPrice, prices[i]);
            MaxProfit = Math.Max(MaxProfit, prices[i]);
        }
        return MaxProfit;
    }
}
    
    ```