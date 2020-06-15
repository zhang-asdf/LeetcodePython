
```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        # 如果字符串为空集，则直接返回""
        if not strs:
            return ""

        # 对字符串进行排序，只比较第一个和最后一个即可
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
        # 如果字符串为空集，则直接返回""
        if not strs:
            return ""

        n = len(strs)
        res = ""
        # 获取所有字符串的前缀，并用pre记录
        for pre in zip(*strs):
            # 若pre中的字符全部相等，那么这个前缀是公共前缀
            for i in range(1,n):
                if pre[i] != pre[i-1]:
                    return res
            res = res + pre[0]

        return res
```
