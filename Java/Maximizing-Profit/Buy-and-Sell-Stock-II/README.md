## Best Time to Buy and Sell Stock II

__Code__: Green

Say you have an array prices for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

```{JAVA}
public int maxProfit(int[] prices) {
```

__Example 1__:

```
Input: [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
             Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
```

__Example 2__:

```
Input: [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
             Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
             engaging multiple transactions at the same time. You must sell before buying again.
```

__Example 3__:

```
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

### Approach: Peak Valley

```PeakValley.java```

__Algorithm__:

Say the given array is: ```[7, 1, 5, 3, 6, 4]```. If we plot the numbers of the given array on a graph, we get:

![Alt text](images/122_maxprofit_1.PNG?raw=true "Maximum Profit")

If we analyze the graph, we notice that the points of interest are the consecutive valleys and peaks.

Mathematically speaking: __TotalProfit__ = ∑<sub>i</sub>(height(peak<sub>i</sub>) − height(valley<sub>i</sub>)) 

The key point is we need to consider every peak immediately following a valley to maximize the profit. In case we skip one of the peaks (trying to obtain more profit), we will end up losing the profit over one of the transactions leading to an overall lesser profit.

For example, in the above case, if we skip peak<sub>i</sub> and valley<sub>j</sub> trying to obtain more profit by considering points with more difference in heights, the net profit obtained will always be lesser than the one obtained by including them, since C will always be lesser than A+B.

#### Complexity Analysis

___Time complexity___: O(n). Single pass.

___Space complexity___: O(1). Constant space required. 

### Approach: Brute Force

```BruteForce.java```

In this case, we simply calculate the profit corresponding to all the possible sets of transactions and find out the maximum profit out of them.

#### Complexity Analysis

___Time complexity___ : O(n<sup>n</sup>). Recursive function is called n<sup>n</sup> times.

___Space complexity___ : O(n). Depth of recursion is n. 


### Approach: Simple One Pass

__Algorithm__:

This solution follows the logic used in Peak Valley solution itself, but with only a slight variation. In this case, instead of looking for every peak following a valley, we can simply go on crawling over the slope and keep on adding the profit obtained from every consecutive transaction. In the end, we will be using the peaks and valleys effectively, but we need not track the costs corresponding to the peaks and valleys along with the maximum profit, but we can directly keep on adding the difference between the consecutive numbers of the array if the second number is larger than the first one, and at the total sum we obtain will be the maximum profit. This approach will simplify the solution. This can be made clearer by taking this example:

```[1, 7, 2, 3, 6, 7, 6, 7]```

The graph corresponding to this array is:

![Alt text](images/122_maxprofit_2.PNG?raw=true "Maximum Profit")

From the above graph, we can observe that the sum A+B+C is equal to the difference D corresponding to the difference between the heights of the consecutive peak and valley.

#### Complexity Analysis

___Time complexity___ : O(n). Single pass.

___Space complexity___ : O(1). Constant space needed.


