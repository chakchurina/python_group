# Встроенные функции для решения задач 

Что удобно использовать в чистом Python для решения задач 

## list comprehension или генераторы списков 

Синтаксис: `[expression for member in iterable]`

Пример: 
```
>>> numbers = [i for i in range(10)]
>>> numbers
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
Пример: 
```
letters = [letter for letter in 'human']
h_letters
```
Пример:
```
>>> squares = [i * i for i in range(10)]
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

### Можно добавить if: 
`[expression for member in iterable if condition]`

Пример: 
```
>>> number_list = [x for x in range(20) if x % 2 == 0]
>>> print(number_list)
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```
Пример: 
```
>>> list_of_strings = ['one', 'two', 'list', '', 'dict', '100', '1', '50']
>>> [s for s in list_of_strings if s.isdigit()]
['100', '1', '50']
```

### Можно добавить else if:  
Синтаксис: `[result if condition else result for member in iterable]`

Заменить число на "четное" или "нечетное":
```
>>> numbers = [1, 2, 4, 7, 9, 6, 3, 7]
>>> obj = ["Even" if i % 2 == 0 else "Odd" for i in numbers]
>>> print(obj)
['Odd', 'Even', 'Even', 'Odd', 'Odd', 'Even', 'Odd', 'Odd']
```

### Вложенные циклы

Синтаксис: `[result if condition else result for member in iterable]`

Транспонировать матрицу: 
```
[[1, 2],
 [3, 4], --> [[1, 3, 5, 7],
 [5, 6],     [2, 4, 6, 8]]
 [7, 8]]
```
можно с помощью генераторов списка: 
```
>>> matrix = [[1, 2], [3,4], [5,6], [7,8]]
>>> transposed = [[row[i] for row in matrix] for i in range(2)]
>>> print(transposed)
[[1, 3, 5, 7], [2, 4, 6, 8]]
```
Можно сделать матрицу плоской:
```
>>> matrix = [[0, 0, 0], 
              [1, 1, 1], 
              [2, 2, 2]]
>>> flat = [num for row in matrix for num in row]
>>> flat
[0, 0, 0, 1, 1, 1, 2, 2, 2]
```

### Вложенные условия 

Синтаксис: `[expression for member in iterable if condition]`

Выбрать только числа, которые одновременно делятся на 2 и на 5:
```
>>> numbers = [y for y in range(100) if y % 2 == 0 if y % 5 == 0]
>>> numbers
[0, 10, 20, 30, 40, 50, 60, 70, 80, 90]
```
Заполнить списки в словаре нулями: 
```
cities = ['Austin', 'Tacoma', 'Topeka', 'Sacramento', 'Charlotte']
temps = {city: [0 for _ in range(7)] for city in cities}
temps
{
    'Austin': [0, 0, 0, 0, 0, 0, 0],
    'Tacoma': [0, 0, 0, 0, 0, 0, 0],
    'Topeka': [0, 0, 0, 0, 0, 0, 0],
    'Sacramento': [0, 0, 0, 0, 0, 0, 0],
    'Charlotte': [0, 0, 0, 0, 0, 0, 0]
}
```
Генераторы списков это красивый способ создавать списки на лету. Обычно они не только более компактные, но и работают быстрее, чем обычные списки. Но все же стоит избегать слишком длинных выражений, чтобы они оставались читаемыми. 

# Функциональное программирование в Python 

## map

Синтаксис: `map(function, iterable(s))`

```
chr_list = ['1', '2', '3', '4', '5', '6', '7']
int_list = list(map(int, chr_list))
```

В курсе: 
```
a, b, c = map(int, input().split())
numbers = list(map(int, input().split()))
```

Можно использовать другие функции: 
```
pets = ["cat", "dog", "parrot", "fish", "turtle"]
list(map(str.upper, pets))
list(map(len, pets))
```

Кстати, у `map` есть еще один аргумент.
```
list(map(pow, range(10), [2, 2, 2, 2, 2, 2, 2, 2, 2, 2]))
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
list(map(pow, range(10), [2]*10))
```

Еще один способ передать список параметров, причем столько, сколько нужно: 
```
from itertools import repeat 
map(pow, range(10), repeat(2))
```

Еще пример для закрепления: 
```
list(map(pow, range(10), range(10)))
[1, 1, 4, 27, 256, 3125, 46656, 823543, 16777216, 387420489]
```

## zip 

Синтаксис: `zip(iterable, iterable)`

Очень полезная функция для решения алгоритмических задач:
```
integers = [1, 2, 3]
letters = ['a', 'b', 'c'] 

for integer, letter in zip(integers, letters):
    print(integer, letter)
```

Можно использовать больше двух списков: 
```
>>> floats = [4.0, 5.0, 6.0]
>>> zipped = zip(integers, letters, floats) 
>>> list(zipped)
[(1, 'a', 4.0), (2, 'b', 5.0), (3, 'c', 6.0)]
```

Из двух последоватльностей `zip` выберет ту, которая короче:  
```
list(zip(range(5), range(100)))
[(0, 0), (1, 1), (2, 2), (3, 3), (4, 4)]
```

## filter 
Синтаксис: `filter(function, iterable)`

"Фильтрует" значения списка с помощью переданной функции. Отфильтруем только строки, состоящие из чисел:
```
list_of_strings = ['one', 'two', 'list', '', 'dict', '100', '1', '50']
list(filter(str.isdigit, list_of_strings))
```

Отфильтруем только взрослых: 
```
ages = [18, 5, 12, 32, 17, 24]

def is_adult(x):
    return True if x >= 18 else False

list(filter(is_adult, ages))
```  
Оставим только гласные: 
```
letters = ['a', 'b', 'd', 'e', 'i', 'j', 'o']

def is_vowel(letter):
    vowels = ['a', 'e', 'i', 'o', 'u']
    return True if letter in vowels else False
    
vowels = list(filter(is_vowel, letters))
```

Выберем только нечетные: 
```
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

def if_odd(x):
    return True if x % 2 != 0 else False

result = filter(if_odd, numbers) 
print(list(result))
```

Выберем только truthy значения: 
```
random = [1, 'a', 0, False, True, '0']
filtered = list(filter(None, random))
print(filtered)
```

Обычно то, что можно сделать через filter, можно сделать и с помощью list comprehension:  
```
[s for s in list_of_strings if s.isdigit()]
newlist = [x for x in fruits if x != "apple"]
```

# Решение последней задачи 

На вход программы подается строка s и массив индексов indices.  

Строку s нужно перемешать так, чтобы символ в i-той позиции исходной строки переместился в позицию indices[i] в перемешанной.

Гарантируется, что s и indices имеют одинаковую длину. 

```
s, indices = "aaiougrt", [4, 0, 2, 6, 7, 3, 1, 5]
s_new = ""

for i in range (0, len(s)):
    index = indices.index(i)
    s_new = s_new + s[index]

print(s_new)
```
Я сделала вот так: 
```
s, indices = "aaiougrt", [4, 0, 2, 6, 7, 3, 1, 5]
result = [None]*(len(s))
for i, letter in zip(indices, s):
    result[i] = letter
    
print("".join(result)) 
```
