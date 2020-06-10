
```python
class Solution:
    def isPalindrome(self, x: int) -> bool:

        # 如果数字小于0，直接返回False
        if x < 0:
            return False

        # 将数字转为字符串，判断字符串是否回文
        s = str(x)
        return s == s[::-1]
```

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:

        # 如果数字为0，返回True
        if x == 0:
            return True

        # 如果数字小于0，或最后一位为0，直接返回False
        if x < 0 or x % 10 == 0:
            return False

        # 利用reserve存储将x末尾数字反过来后的数字
        reverse = 0
        # 当x > reserve，即原本数字的左半部分大于右半部分时，继续循环
        while x > reverse:
            # 取x最后一位，加到reserve的最后一位上
            reverse = reverse * 10 + x % 10
            # 去掉x的最后一位
            x = x // 10
        return x == reverse or x == reverse // 10
```
