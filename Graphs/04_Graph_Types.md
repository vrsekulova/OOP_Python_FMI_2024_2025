# Типове графи и алгоритми за разпознаване

## 1. Типове

* Претеглен (непретеглен)
* Ориентиран (неориентиран)
* Цикличен (ацикличен)
* Свързан граф - съществува връзка (рамо) между всяка двойка върхове
  * _двустранно свързан_ - ако премахнем даден връх, графът ще запази възможността всеки един от останалите върхове да бъде достигнат
  * _напълно свързан_ - свързването е тип всеки със всеки

## 2. Алгоритми за разпознаване

### a) Ориентиран (насочен) или неориентиран (ненасочен)
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

### в) Свързан

#### * Двустранно свързан
* ако във вектора със сумите по колони има поне една сума, по-малка от 1 -> не е двустранно свързан

```py
# работи само за неориентиран граф !!!
def is_double_edge_connected(self):
    for j in range(self.size): # колони
        sum = 0
        for i in range(self.size): # редове
            sum += self.adj_matrix[i][j]
        if sum < 1:
            return "не е двустранно свързан"

    return "двустранно свързан"
```

#### * Напълно свързан
* При употреба на матрица на съседство:
  * На главния диагонал не трябва да има стойност 1
  * На останалите позиции трябва да има само стойност 0
```py
def is_fully_connected(self):
    for i in range(self.size):
        for j in range(self.size):
            if i == j and self.adj_matrix[i][j] == 1:
                return "не е напълно свързан"
            if i != j and self.adj_matrix[i][j] == 0:
                return "не е напълно свързан"

    return "напълно свързан"
```