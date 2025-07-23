LRU Cache (Medium)
===

Problem: https://leetcode.com/problems/lru-cache/

---

1. (超麻煩，不過很好想)     
講解：https://www.youtube.com/watch?v=7ABFKPK2hD4
```python
# 要自訂一個 Node 的類別
class Node:
    def __init__(self, key, value):
        self.key, self.value = key, value
        self.prev = self.next = None

class LRUCache:
    def __init__(self, capacity: int):
        self.capacity = capacity
        self.cache = {} # map key to node

        # left = least recent, right = most recent
        self.left, self.right = Node(0, 0), Node(0, 0) # 因為這兩個是 Node，所以可以用 .prev & .next
        self.left.next, self.right.prev = self.right, self.left # 設定兩個指標


    # 兩個 helper function: remove, insert 
    def remove(self, node): # remove node from left (用 linked list)
        # 假裝這個 node 在中間
        prev, next = node.prev, node.next
        prev.next, next.prev = next, prev

    def insert(self, node): # insert node at right (用 linked list)
        # 假裝這個 node 在中間
        prev, next = self.right.prev, self.right # 因為從右邊插
        prev.next = next.prev = node
        node.prev, node.next = prev, next


    def get(self, key: int) -> int:
        if key in self.cache:
            self.remove(self.cache[key]) # 因為有用到了，所以要更新他變成 most recent
            self.insert(self.cache[key])
            return self.cache[key].value
        else:
            return -1

    def put(self, key: int, value: int) -> None:
        if key in self.cache:
            self.remove(self.cache[key])
        self.cache[key] = Node(key, value)
        self.insert(self.cache[key])

        # 檢查容量
        # remove from the list and delete the LRU from the hashmap
        if len(self.cache) > self.capacity:
            lru = self.left.next # lru 是 Node
            self.remove(lru)
            del self.cache[lru.key]
```

```python
# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```
