---
title: Leetcode study day 1
categories:
- Leetcode
feature_image: "https://picsum.photos/2560/600?image=872"
---

Today, I have studied [a leetcode problem](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

I found this solution was really helpful:

```python
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        i = 0
        while i < len(nums)-1:
            if nums[i] == nums[i+1]:
                del nums[i]
            else:
                i += 1
        return len(nums)
```

- in-place deletion method `del`
- loop end condition: when i >= len(nums)-1
    - [0, 1, 2, 3, 4]
    - The maximum index can only be less than len(nums)-1 (5 nums -> index 0 ~ 4 etc.)