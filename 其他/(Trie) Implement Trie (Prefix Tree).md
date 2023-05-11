(Trie) Implement Trie (Prefix Tree)
===

Problem: https://leetcode.com/problems/implement-trie-prefix-tree/description/

---

1. (我寫的慢慢的)
```python
class Trie:

    def __init__(self):
        self.trie = []    

    def insert(self, word: str) -> None:
        self.trie.append(word)

    def search(self, word: str) -> bool:
        if word in self.trie:
            return True
        else:
            return False

    def startsWith(self, prefix: str) -> bool:
        for i in self.trie:
            if re.match(r'{}'.format(prefix), i):
                return True
        return False


# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix)
```

2.
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.isend = False # 看是不是字的最後

class Trie:
    def __init__(self):
        self.trie = TrieNode()

    def insert(self, word: str) -> None:
        cur = self.trie # 目前的位置
        for i in word:
            if i not in cur.children:
                cur.children[i] = TrieNode()
            cur = cur.children[i] # 移動到下一個
        cur.isend = True # 當 insert 的字結束了，標記為"結束"

    def search(self, word: str) -> bool:
        cur = self.trie
        for i in word:
            if i not in cur.children:
                return False
            cur = cur.children[i]
        return cur.isend

    def startsWith(self, prefix: str) -> bool:
        cur = self.trie
        for i in prefix:
            if i not in cur.children:
                return False
            cur = cur.children[i]
        return True
```

3.
```python
class Trie:
    def __init__(self):
        self.memo = {}

    def insert(self, word: str) -> None:
        current_memo = self.memo
        for char in word:
            if char not in current_memo:
                current_memo[char] = {}

            current_memo = current_memo[char]

        current_memo["."] = None

    def search(self, word: str) -> bool:
        current_memo = self.memo
        for char in word:
            if char not in current_memo:
                return False

            current_memo = current_memo[char]

        return "." in current_memo

    def startsWith(self, prefix: str) -> bool:
        current_memo = self.memo
        for char in prefix:
            if char not in current_memo:
                return False

            current_memo = current_memo[char]

        return True
```

