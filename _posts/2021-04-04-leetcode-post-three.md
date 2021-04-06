## Leetcode post three

### Problem
- [Roman to Integer](https://leetcode.com/problems/roman-to-integer/)

### My solution
```python
class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        
        # If large -> small; simple addition
        # If small -> large; small one is subtracted from the larger one
        
        symbol2val = {"I":1, "V":5, "X":10, "L":50, "C":100, "D":500, "M":1000}
        
        curr_char = s[0]
        output = 0
        for char in s[1:]:
            if symbol2val[curr_char] >= symbol2val[char]:
                output += symbol2val[curr_char]
            
            else:
                output -= symbol2val[curr_char]
            
            curr_char = char
        
        output += symbol2val[curr_char]
        
        return output
```

### Sample solution

```python
class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        mapping = {'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000}
        
        res = mapping[s[0]]
        for i in range(1, len(s)):
            res += mapping[s[i]]
            if mapping[s[i - 1]] < mapping[s[i]]:
                res -= 2 * mapping[s[i - 1]]
        
        return res
```

### Thoughts
- Didn't really need to store the output and the current character
- Only need to take care of the case where current character < next character
