
```python
class Solution:
    def translateNum(self, num: int) -> int:

        def feasible(s):
            num = int(s)
            if 10 <= num <= 25:
                return True 
            return False 

        s = str(num)
        n = len(s)
        f = [0 for i in range(0,n+1)]
        f[0] = 1
        for i in range(1,n+1):
            f[i] = f[i-1]
            if i >= 2 and feasible(s[i-2] + s[i-1]):
                f[i] = f[i] + f[i-2]
        return f[n]
```
