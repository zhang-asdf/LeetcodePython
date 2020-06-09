
```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False
        s = str(x)
        if s == s[::-1]:
            return True
        return False
```
