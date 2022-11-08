# 最小生成树



Kruskal&#x20;

```python
# Kruskal
class Kruskal:
    def __init__(self, vertices, edges):
        self.vertices = vertices
        self.edges = edges
        self.tree = {}  # tree[i] means the i point belongs to which tree
        self.length = {}
    
    def make_set(self, point):
        self.tree[point] = point
        self.length[point] = 1
    
    def find(self, point):
        while self.tree[point] != point:
            point = self.tree[point]
        return point
    
    def merge(self, point1, point2):
        point1, point2 = self.find(point1), self.find(point2)
        if point1 != point2:
            if self.length[point1] < self.length[point2]:
                self.tree[point1] = point2
                slef.length[point2] += self.length[point1]
            else:
                self.tree[point2] = point1
                self.length[point1] += self.length[point2]
    
    def kruskal(self):
        for vertice in self.vertices:
            self.make_set(vertice)
        minu_tree = []
        self.edges.sort()  
        for edge in self.edges:
            weight, vertice1, vertice2 = edge
            if self.find(vertice1) != self.find(vertice2):
                self.merge(vertice1, vertice2)
                minu_tree.append(edge)
        return minu_tree
```
