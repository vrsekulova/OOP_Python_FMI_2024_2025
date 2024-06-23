# Dijkstra - Алгоритъм за намиране на най-къс път между два възела

## 1. Имплементация

```py
import heapq

def dijkstra(graph, start, target):
    pq = [(0, start)]
    shortest_paths = {start: (None, 0)} # {възел1: (възел2, разстояние между възел1 и start)}
    while pq:
        # heapq.heappop(pq) --> присвоява стойността, 
        # която има най-кратко разстояние, 
        # ако няма такова - най-десния елемент
        current_distance, current_node = heapq.heappop(pq)
        if current_node == target:
            break
        
        list_neighbors = []
        # list_neighbors - списък със съседите на върха / алгоритъм /:
            # .
            # .
            # .
            # .
            # ...
        
        for neighbor in list_neighbors:
            distance = current_distance + 1
            if neighbor not in shortest_paths or \
                distance < shortest_paths[neighbor][1]:
                shortest_paths[neighbor] = (current_node, distance)
                heapq.heappush(pq, (distance, neighbor))
                
        path = []
        current = target
        while current is not None:
            path.append(current)
            current = shortest_paths[current][0]
        
        path = path[::-1]
        return path
```
## 2.Имплементация на list_neighbors

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