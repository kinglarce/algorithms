# Top K Frequent Elements

#### Links:

Top K Frequent Elements -[ ](https://leetcode.com/problems/maximum-subarray/)[https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)

#### Problem:

Given an integer array `nums` and an integer `k`, return _the_ `k` _most frequent elements_. You may return the answer in **any order**.

**Example 1:**

```
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

#### Solutions

{% tabs %}
{% tab title="Hashmap w/ Heap - O(n log n)" %}
{% hint style="success" %}
Time: O(n log n), Space: O(1)
{% endhint %}

{% hint style="info" %}
**Hint:** This approach uses Max Heap, but for us to get the top K number, we need to get the frequency of the numbers, and after than, we will then use the heap. We will push each element/number to the heap and since `heappop` by default behaves like a Min Heap, then for each iteration, we pop out the smallest element and keep the bigger elements in the heap, and as a result, the heap will only contain the max element/numbers.
{% endhint %}

```python
import heapq

def top_k_frequent(nums: List[int], k: int) -> List[int]:
    frequency = {}
    heap = []
    for num in nums:
        frequency[num] = frequency.get(num, 0)
        frequency[num] += 1

    for key, val in frequency.items():
        heapq.heappush(heap, (val, key))
        
        if len(heap) > k :
            heapq.heappop(heap)
            
    return [heapq.heappop(heap)[1] for _ in range(k)]
```
{% endtab %}
{% endtabs %}
