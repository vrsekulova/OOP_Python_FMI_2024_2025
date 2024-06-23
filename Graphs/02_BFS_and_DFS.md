# Търсене в ширина (BFS) и дълбочина (DFS)

## 1. Търсене в ширина (BFS)
* структура от данни - deque
### Общ вид на програмата

```py
from collections import deque
def bfs(self, start):
    visited = set()
    queue = deque([start])

    while queue:
        vertex = queue.popleft()
        if vertex not in visited:
            visited.add(vertex)
            
            list_neighbors = []
            # list_neighbors - списък със съседите на върха / алгоритъм /:
            # .
            # .
            # .
            # .
            # ...

            for neighbor in list_neighbors:
                if neighbor not in visited:
                    queue.append(neighbor)
    return visited
```

## 2. Търсене в дълбочина
* структура от данни - stack

```py
def dfs(self, start):
    visited = set()
    stack = [start]

    while stack:
        vertex = stack.pop()
        if vertex not in visited:
            visited.add(vertex)
            
            list_neighbors = []
                # list_neighbors - списък със съседите на върха / алгоритъм /:
                # .
                # .
                # .
                # .
                # ...

            for neighbor in list_neighbors:
                if neighbor not in visited:
                    stack.append(neighbor)
```

## 3.Имплементация на list_neighbors

### а) Матрица на съседство
```py
for i in range(len(self.adjMatrix[vertex])):
    if self.adjMatrix[vertex][i] == 1:
        list_neighbors.append(i)
```
### б) Матрица на инцидентност
```py
for i in range(len(self.adjMatrix[vertex])):
    if self.adjMatrix[vertex][i] == -1:
        list_neighbors.append(i)
```
### в) Свързан списък
```py
temp = self.graph[vertex]
while temp:
    list_neighbors.append(temp.vertex)
    temp = temp.next
```