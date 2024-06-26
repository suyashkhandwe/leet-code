# Problem 122. Best Time to Buy and Sell Stock II

> [!NOTE]
> [122. Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/?envType=study-plan-v2&envId=top-interview-150)

You are given an integer array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day.

Find and return the `maximum profit` you can achieve.

### Examples

#### Example 1:

> **Input**: `prices = [7,1,5,3,6,4]`<br/>
> **Output**: `7`<br/>
> **Explanation**:
> - Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
> - Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
> - Total profit is 4 + 3 = 7.

#### Example 2:

> **Input**: `prices = [1,2,3,4,5]`<br/>
> **Output**: 4<br/>
> **Explanation**: 
> - Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
> - Total profit is 4.

#### Example 3:

> **Input**: `prices = [7,6,4,3,1]`
> **Output**: 0
> **Explanation**: There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of 0.

#### Constraints:

- `1 <= prices.length <= 3 * 104`
- `0 <= prices[i] <= 104`

## Solutions

### Solution 1

```java
public int maxProfit(int[] prices) {
    int maxProfit = 0;
    int buyPrice = prices[0];
    for (int i = 1; i < prices.length; i++) {
        if (prices[i] > buyPrice) {
            maxProfit += prices[i] - buyPrice;
        }
        buyPrice = prices[i];
    }
    return maxProfit;
}
```

#### Complexities

- `Time Complexity`: O(n) 
    - iterate through the prices array once for `n` prices.

- `Space Complexity`: O(1)buy price.
    - using a constant amount of extra space regardless of the size of the input array

> [!TIP]
> The above code uses the greedy algorithm - buy ion a dip, sell on the first spike and the nbuy immidiately for the next spike.