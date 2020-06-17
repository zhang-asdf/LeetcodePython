
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def recoverFromPreorder(self, S: str) -> TreeNode:

        def dfs(val, depth):
            
            node = TreeNode(val.pop(0))
            depth.pop(0)
            i = 1
            n = len(depth)
            while i < n and depth[i] > depth[0]:
                i = i + 1

            if n >= 1:
                node.left = dfs(val[0:i], depth[0:i])
            if i < n:
                node.right = dfs(val[i:],depth[i:])
            return node

        k = 0
        val_s = ''
        val = []
        depth = []

        for i in S:
            if i == '-':
                if k == 0:
                    val.append(int(val_s))
                k = k + 1
                val_s = ''
            else:
                if val_s == '':
                    depth.append(k)
                val_s = val_s + i
                k = 0
        val.append(int(val_s))

        return dfs(val, depth)
             

```
