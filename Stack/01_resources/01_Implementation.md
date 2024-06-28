# Стек
* линейна структура от данни
* **_LIFO_** (Last In First Out)
* реализация в Python - чрез списък, чрез deque
* основни операции:
  * **push(element)** - добавя елемент в края на стека
  * **pop()** - премахва и връща последния добавен елемент в стека
  * **peek()** - връща последния добавен елемент в стека
  * **isEmpty()** - проверява дали стекът е празен

## 1. Реализация чрез списък
```py
class Stack:
    def __init__(self, list_elems: list):
        self.list_elems = list_elems
    
    def push(self, element):
        self.list_elems.append(element)
        
    def pop(self):
        return self.list_elems.pop()
    
    def isEmpty(self):
        return self.list_elems == []
    
    def peek(self):
        return self.list_elems[-1]
```

## 2. Реализация чрез deque
* deque = double queue (лесен достъп на първи и последен елемент с по-малка сложност спрямо списъка)

```py
from collections import deque

class Stack:
    def __init__(self, list_elems = deque()):
        self.list_elems = list_elems

    def push(self, element):
        self.list_elems.append(element)

    def pop(self):
        return self.list_elems.pop()

    def isEmpty(self):
        return self.list_elems == deque()

    def peek(self):
        last_el = self.list_elems.pop()
        self.list_elems.append(last_el)
        return last_el
```