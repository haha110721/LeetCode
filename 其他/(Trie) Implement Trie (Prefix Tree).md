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
