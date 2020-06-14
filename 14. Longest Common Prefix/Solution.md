
```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        
        if not strs:
            return ""

        strs.sort()
        res = ""
        for i,j in zip(strs[0],strs[-1]):
            if i==j:
                res = res + i
            else:
                return res

        return res
```

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:

        if not strs:
            return ""

        n = len(strs)
        res = ""
        for pre in zip(*strs):
            for i in range(1,n):
                if pre[i] != pre[i-1]:
                    return res
            res = res + pre[0]
        
        return res
```
