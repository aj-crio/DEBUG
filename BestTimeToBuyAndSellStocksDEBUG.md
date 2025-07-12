
```cpp
int maxProfit(vector<int>& prices) {
    int profit = INT_MAX;  // ❌ Error 1: should start with 0
    int n = prices.size();
    for (int i = 0; i <= n; ++i) {  // ❌ Error 2: should be i < n
        if (prices[i] - prices[i - 1] < 0) {  // ❌ Error 3: wrong sign
            profit += prices[i] - prices[i - 1];
        }
    }
    return profit;
}
```

```java
    public static int maxProfit(List<Integer> prices) {
        int profit = Integer.MAX_VALUE;  // ❌ Error 1
        int n = prices.size();
        for (int i = 0; i <= n; i++) {  // ❌ Error 2
            if (prices.get(i) - prices.get(i - 1) < 0) {  // ❌ Error 3
                profit += prices.get(i) - prices.get(i - 1);
            }
        }
        return profit;
    }
```

``` js
function maxProfit(prices) {
    let profit = Number.MAX_SAFE_INTEGER;  // ❌ Error 1
    const n = prices.length;
    for (let i = 0; i <= n; i++) {  // ❌ Error 2
        if (prices[i] - prices[i - 1] < 0) {  // ❌ Error 3
            profit += prices[i] - prices[i - 1];
        }
    }
    return profit;
}
```

```python
def max_profit(prices):
    profit = float('inf')  # ❌ Error 1
    n = len(prices)
    for i in range(n + 1):  # ❌ Error 2
        if prices[i] - prices[i - 1] < 0:  # ❌ Error 3
            profit += prices[i] - prices[i - 1]
    return profit
```
