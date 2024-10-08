# **121. Best Time to Buy and Sell Stock**
`Easy`
### Question : 
You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.
 

Example 1:<br>
Input: prices = [7,1,5,3,6,4]<br>
Output: 5<br>
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.<br>
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.<br>

Example 2:<br>
Input: prices = [7,6,4,3,1]<br>
Output: 0<br>
Explanation: In this case, no transactions are done and the max profit = 0.<br>

### Java Solution:
```java
class Solution {
    public int maxProfit(int[] prices) {
        int maxProfit = 0;
        int buyPrice = prices[0];
        int currProfit = 0;

        for(int i = 0; i<prices.length; i++){
            if(prices[i]<buyPrice){
                buyPrice = prices[i];
            }   
            currProfit = prices[i]-buyPrice;  
            if(currProfit > maxProfit){
                maxProfit = currProfit;
            }    
        }
        return maxProfit;
    }
}
```