# Типове графи и алгоритми за разпознаване

## 1. Типове

* Претеглен (непретеглен)
* Ориентиран (неориентиран)
* Цикличен (ацикличен)
* Свързан граф - между всяка двойка възли има ребро

## 2. Алгоритми за разпознаване

### a) Претеглен или непретеглен
* Използва се **_матрица на съседство_**
* Ако елементите са симетрично разположени спрямо главния диагонал -> ненасочен граф

#### Алгоритъм:
```py
def is_directed(self):
    for i in range(1, self.size): # i - ред (излиза ребро)
        for j in range(self.size-1): # j - колона (влиза ребро)
            if self.adj_matrix[i][j] != self.adj_matrix[j][i]:
                return "насочен граф"

    return "ненасочен граф"
```
#### Примери:
```py
graph = Graph(5)
graph.add_edge(0, 1) # !
graph.add_edge(1, 0) # !
graph.add_edge(0, 2)
graph.add_edge(2, 0)

print(graph.is_directed()) # ненасочен граф

graph1 = Graph(5)
graph1.add_edge(0, 1) # !
graph1.add_edge(1, 2) # !
graph1.add_edge(0, 2)
graph1.add_edge(2, 0)

print(graph1.is_directed()) # насочен граф
```

### б) Цикличен (ацикличен)
* Отново се проверява чрез **_матрица на съседство_**
* Ако поне един елемент от матрицата е равен на 1 -> цикличен граф

#### Алгоритъм:
```py
def is_cycled(self):
    for i in range(self.size):
        if self.adj_matrix[i][i] == 1:
            return "цикличен граф"
    
    return "ацикличен граф"
```

#### Примери:
```py
graph = Graph(5)
graph.add_edge(0, 1)
graph.add_edge(1, 2)
graph.add_edge(2, 2) ## !
graph.add_edge(3, 0)

print(graph.is_cycled()) # цикличен граф

graph1 = Graph(5)
graph1.add_edge(0, 1)
graph1.add_edge(1, 2)
graph1.add_edge(0, 2)
graph1.add_edge(2, 0)

print(graph1.is_directed()) # ацикличен граф
```