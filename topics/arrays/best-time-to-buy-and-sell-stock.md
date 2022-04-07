# Best Time to Buy and Sell Stock

#### Links:

Best Time to Buy and Sell Stock - [https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

#### Problem:

You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.

**Example 1:**

```
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
```

```
(prices)
        8|
        7|   *             (sell) - Best time to sell for 5 profile of 6-1
        6|                   * 
        5|           * 
        4|                       *
        3|               *
        2|
        1|       *(buy)
        0|_____________________________________
         0   1   2   3   4   5   6     (days)
```

#### Solutions

{% tabs %}
{% tab title="Two Pointer - O(n)/O(n^2)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** Use `left` and `right` point where `left` is your base and you have a runner `right` variable that check each price to the base value, getting its difference and recording the max profit.
{% endhint %}

```python
def buy_and_sell_stock(prices):
    max_profit = 0 
    left = 0
    right = left + 1
    while right < len(prices):
        if prices[left] < prices[right]:
            diff_value = prices[right] - prices[left]
            max_profit = max(diff_value, max_profit)
        else: 
            left = right
        right += 1
    return max_profit
```
{% endtab %}

{% tab title="One Pass - O(n)" %}
{% hint style="success" %}
Time: O(n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** We record the min price and max price respectively the check if the current day price minus min price is greater than the current max profile, then we replace the current max profile.
{% endhint %}

```python
def buy_and_sell_stock(prices):
    min_price = float('inf')
    max_profit = 0
    for i in range(len(prices)):
        if prices[i] < min_price:
            min_price = prices[i]
        elif prices[i] - min_price > max_profit:
            max_profit = prices[i] - min_price
        
    return max_profit 
```
{% endtab %}
{% endtabs %}
