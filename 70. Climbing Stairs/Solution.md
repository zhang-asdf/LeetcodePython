
```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        f = [1 for i in range(0,n+1)]
        for i in range(2,n+1):
            f[i] = f[i-1] + f[i-2]

        return f[n]
```

```python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        x = 1
        y = 1
        for i in range(2,n+1):
            temp = x
            x = y
            y = temp + x
        return y
```
