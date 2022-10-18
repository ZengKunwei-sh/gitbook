# 二叉树

```python
class Node:
    def __init__(self, data=None):
        self.data = data
        self.left = None
        self.right = None
        self.parent = None
        self.height = 0

class BinaryTree:
    def __init__(self):
        self.root = None
    
    def _str_(self, node=0, depth=0, direction_label=""):
        if node == 0:
            node = self.root
        if node:
            height_info = f"(H: {str(node.height)})" if node.height > 0 else ""
            return depth * "\t" + direction_label + height_info + str(node.data) + "\n" + \
                self._str_(node.left, depth+1, "L:") + self._str_(node.right, depth+1, "R:")
        else:
            return ""
    
    def inorder(self, node=0, result=[]):
        if node == 0:
            node = self.root
        if node:
            self.inorder(node.left, result)
            result.append(node.data)
            self.inorder(node.right, result)
        return result
```
