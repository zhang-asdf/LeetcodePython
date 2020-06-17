
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

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def recoverFromPreorder(self, S: str) -> TreeNode:

        n = len(S)
        i = 0
        cur_depth = 0
        stack = []
        while i < n:
            val_s = ''
            depth = 0
            while S[i] == '-':
                depth = depth + 1
                i = i + 1
            while i < n and S[i].isdigit():
                val_s = val_s + S[i]
                i = i + 1
            val = int(val_s)

            node = TreeNode(val)
            if depth > cur_depth:
                stack[-1].left = node
                cur_depth = cur_depth + 1
            else:
                if stack:
                    stack = stack[:depth]
                    stack[-1].right = node
                    cur_depth = depth
            stack.append(node)
        return stack[0]
```
