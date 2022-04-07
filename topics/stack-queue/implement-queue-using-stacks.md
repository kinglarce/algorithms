# Implement Queue using Stacks

#### Links:

Implement Queue using Stacks - [https://leetcode.com/problems/implement-queue-using-stacks/](https://leetcode.com/problems/implement-queue-using-stacks/)

#### Problem:

Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (`push`, `peek`, `pop`, and `empty`).

Implement the `MyQueue` class:

* `void push(int x)` Pushes element x to the back of the queue.
* `int pop()` Removes the element from the front of the queue and returns it.
* `int peek()` Returns the element at the front of the queue.
* `boolean empty()` Returns `true` if the queue is empty, `false` otherwise.

**Notes:**

* You must use **only** standard operations of a stack, which means only `push to top`, `peek/pop from top`, `size`, and `is empty` operations are valid.
* Depending on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only a stack's standard operations.

**Example 1:**

```
Input
["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]
Output
[null, null, null, 1, 1, false]

Explanation
MyQueue myQueue = new MyQueue();
myQueue.push(1); // queue is: [1]
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
myQueue.peek(); // return 1
myQueue.pop(); // return 1, queue is [2]
myQueue.empty(); // return false
```

#### Solutions

{% tabs %}
{% tab title="Stack - O(n)" %}
{% hint style="success" %}
Time: \
Push - O(n), Pop - O(1), Peek - O(1)\
Space: O(n)
{% endhint %}

{% hint style="info" %}
**Hint:** Idea is the newest element must be pushed to the bottom of the stack. To do so we first transfer all`self.stack` elements to an auxiliary stack `stack2` and then the newly arrived element is pushed on top of `stack2` and all its elements are popped and pushed back to `self.stack`.\
e.g.

Pushing "3" element in the queue\
1\. self.stack = \[2, 1] , stack2 = \[] \
2\. self.stack = \[3] , stack2 = \[1, 2] - Move all elements to `stack2` and push new element to `self.stack`.\
3\. self.stack = \[3, 2, 1] , stack2 = \[] - Move all elements back from `stack2` to `self.stack`.
{% endhint %}

```python
class MyQueue:
    def __init__(self):
        self.stack = []

    def push(self, x: int) -> None:
        if self.empty():
            self.stack.append(x)
            return
        
        stack2 = [self.stack.pop() for _ in range(len(self.stack))]
        
        self.stack.append(x)
        for _ in range(len(stack2)):
            self.stack.append(stack2.pop())

    def pop(self) -> int:
        return self.stack.pop()

    def peek(self) -> int:
        num = self.stack.pop()
        self.stack.append(num)
        return num

    def empty(self) -> bool:
        return not self.stack
```
{% endtab %}
{% endtabs %}
