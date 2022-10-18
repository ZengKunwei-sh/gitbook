# 二叉搜索树

```python
class Node:
    def __init__(self, data=None):
        self.data = data
        self.left = None
        self.right = None
        self.parent = None
        self.height = 0
    
    def left_height(self):
        return -1 if self.left is None else self.left.height
    
    def right_height(self):
        return -1 if self.right is None else self.right.height
    
    def update_height(self):
        self.height = max(self.left_height(), self.right_height()) + 1
    
    def balance(self):
        return self.right_height() - self.left_height()
    
    
class BinarySearchTree(BinaryTree):
    def __init__(self, array=[]):
        self.root = None
        for data in array:
            self.insert(Node(data))
    
    def insert(self, new_node, node=0):
        if not self.root:
            self.root = new_node
            return new_node
        if node == 0:
            node = self.root
        if new_node.data < node.data:
            if node.left:
                self.insert(new_node, node.left)
            else:
                new_node.parent = node
                node.left = new_node
        else:
            if node.right:
                self.insert(new_node, node.right)
            else:
                new_node.parent = node
                node.right = new_node
        node.update_height()
    
    def sort(self):
        return self.inorder()
def BST_sort(array):
    my_tree = BinarySearchTree(array)
    print(my_tree._str_())
    return my_tree.sort()
```
