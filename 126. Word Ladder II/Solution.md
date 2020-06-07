
```python
def findLadders(self, beginWord: str, endWord: str, wordList: List[str]) -> List[List[str]]:

    wordList = wordList + [beginWord]
    n = len(wordList)
    m = len(beginWord)
    wordSet = set(wordList)
    succ = {}
    steps = {}

    for word in wordList:
        succ[word] = []
        steps[word] = 0
        for j in range(0,m):
            for k in range(0,26):
                newword = word[:j]+chr(k+97)+word[j+1:]
                if newword != word and newword in wordSet:
                    succ[word].append(newword)

    queue = [beginWord]
    visited = set([beginWord])
    while queue:
        curr_word = queue.pop(0)
        for next_word in succ[curr_word]:
            if not next_word in visited:
                queue.append(next_word)
                steps[next_word] = steps[curr_word] + 1
                visited.add(next_word)
        if endWord in visited:
            break

    max_steps = max(list(steps.values()))

    def dfs(curr_word,depth):
        if depth > max_steps:
            return []
        if curr_word == endWord:
            return [[curr_word]]
        path = []
        for next_word in succ[curr_word]:
            if steps[next_word] == depth + 1:
                temppaths = dfs(next_word,depth + 1)
                for temppath in temppaths:
                    path.append([curr_word] + temppath)
        return path

    return dfs(beginWord,0)
```
