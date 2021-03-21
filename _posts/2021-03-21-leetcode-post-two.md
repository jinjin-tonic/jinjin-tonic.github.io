---
title: Leetcode study day 2
categories:
- Leetcode
feature_image: "https://picsum.photos/2560/600?image=872"
---

Problem: [Reverse integer](https://leetcode.com/problems/reverse-integer/)

My solution:

```python
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        if x < 0:
            sign = "-"
        else:
            sign = "+"
        x = [char for char in str(x) if char != "-" and char != "+"]
        x = int(sign + "".join(x[::-1]))
        
        if x < -2**31 or x > (2**31 - 1):
            return 0
        
        return x
```

A better solution:

```python
class Solution:
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        sign = [1,-1][x < 0]
        rst = sign * int(str(abs(x))[::-1])
        return rst if -(2**31)-1 < rst < 2**31 else 0

```
- `sign = [1,-1][x<0]`
    - [x<0] returns [True] if x <0 and [False] if x > 0.
    - if [True] then it's the same as [1] -> indexing
    - if [False] then it's the same as [0] -> indexing
- Therefore, sign [1,-1][x<0] will be [1] if x > 0, [-1] if x <0.
- Pretty impressive!

