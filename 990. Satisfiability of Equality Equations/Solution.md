
```python
class Solution:
    def equationsPossible(self, equations: List[str]) -> bool:

        ancient = [i for i in range(0,26)]
        for equation in equations:
            if equation[1] == '=':
                x = ord(equation[0]) - 97
                y = ord(equation[3]) - 97
                tempx = ancient[x]
                while ancient[tempx] != tempx:
                    tempx = ancient[tempx]
                tempy = ancient[y]
                while ancient[tempy] != tempy:
                    tempy = ancient[tempy]
                ancient[tempx] = ancient[tempy]


        def check(x,y):
            tempx = ancient[x]
            while ancient[tempx] != tempx:
                tempx = ancient[tempx]
            tempy = ancient[y]
            while ancient[tempy] != tempy:
                tempy = ancient[tempy]
            if tempx == tempy:
                return True
            return False

            
        for equation in equations:
            if equation[1] == '!':
                x = ord(equation[0]) - 97
                y = ord(equation[3]) - 97
                if check(x,y):
                    return False
        return True
```
