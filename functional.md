# Встроенные функции для решения задач 

Что вам будет удобно использовать в чистом Python для решения задач 

## list comprehension или генераторы списков 

### Синтаксис: 
`[expression for member in iterable]`

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
`[result if condition else result for member in iterable]`

Заменить число на "четное" или "нечетное":
```
>>> numbers = [1, 2, 4, 7, 9, 6, 3, 7]
>>> obj = ["Even" if i % 2 == 0 else "Odd" for i in numbers]
>>> print(obj)
['Odd', 'Even', 'Even', 'Odd', 'Odd', 'Even', 'Odd', 'Odd']
```

### Вложенные циклы

`[result if condition else result for member in iterable]`

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

`[expression for member in iterable if condition]`
Выбрать только числа, которые одновременно делятся на 2 и на 5:
```
>>> numbers = [y for y in range(100) if y % 2 == 0 if y % 5 == 0]
>>> numbers
[0, 10, 20, 30, 40, 50, 60, 70, 80, 90]
```

>>> cities = ['Austin', 'Tacoma', 'Topeka', 'Sacramento', 'Charlotte']
>>> temps = {city: [0 for _ in range(7)] for city in cities}
>>> temps
{
    'Austin': [0, 0, 0, 0, 0, 0, 0],
    'Tacoma': [0, 0, 0, 0, 0, 0, 0],
    'Topeka': [0, 0, 0, 0, 0, 0, 0],
    'Sacramento': [0, 0, 0, 0, 0, 0, 0],
    'Charlotte': [0, 0, 0, 0, 0, 0, 0]
}

# List comprehension is an elegant way to define and create lists based on existing lists.
# List comprehension is generally more compact and faster than normal functions and loops for creating list.
# However, we should avoid writing very long list comprehensions in one line to ensure that code is user-friendly.
# Remember, every list comprehension can be rewritten in for loop, but every for loop can’t be rewritten in the form of list comprehension.


# Функциональное программирование в Python 

f(x) = y

# map, zip, filter, reduce 

# map 

# map(function, iterable(s))

chr_list = ['1', '2', '3', '4', '5', '6', '7']
int_list = map(int, chr_list)

В курсе: 

a, b, c = map(int, input().split())

numbers = map(int, input().split())

Можно использовать другие функции: 

pets = ["cat", "dog", "parrot", "fish", "turtle"]

map(str.upper(), pets)

map(len(), pets)

Кстати, у map есть еще один аргумент.

map(pow, range(10), [2, 2, 2, 2, 2, 2, 2, 2, 2, 2])
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

map(pow, range(10), [2]*10)

from itertools import repeat 
map(pow, range(10), repeat(2))

list(map(pow, range(10), range(10)))
[1, 1, 4, 27, 256, 3125, 46656, 823543, 16777216, 387420489]

# zip 

>>> integers = [1, 2, 3]
>>> letters = ['a', 'b', 'c'] 

for integer, leter in zip(integers, letters):
    print(integer, letter)

>>> integers = [1, 2, 3]
>>> letters = ['a', 'b', 'c']
>>> floats = [4.0, 5.0, 6.0]
>>> zipped = zip(integers, letters, floats)  # Three input iterables
>>> list(zipped)
[(1, 'a', 4.0), (2, 'b', 5.0), (3, 'c', 6.0)]

list(zip(range(5), range(100)))
[(0, 0), (1, 1), (2, 2), (3, 3), (4, 4)]


# filter 

# filter(function, iterable)

# 1 

list_of_strings = ['one', 'two', 'list', '', 'dict', '100', '1', '50']

In [2]: filter(str.isdigit, list_of_strings)

# 1

ages = [5, 12, 17, 18, 24, 32]

def filter_func(x):
    return True if x >= 18 else False

adults = list(filter(filter_func, ages))

for x in adults:
  print(x)
  
# 2

letters = ['a', 'b', 'd', 'e', 'i', 'j', 'o']

def filterVowels(letter):
    vowels = ['a', 'e', 'i', 'o', 'u']
    return True if letter in vowels else False
    
filteredVowels = filter(filterVowels, letters)


# 3

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

def if_odd(x):
    return True if x % 2 != 0 else False

result = filter(if_odd, seq) 
print(list(result))

# 4

randomList = [1, 'a', 0, False, True, '0']

filteredList = filter(None, randomList)

for element in filteredList:
    print(element)

# То же можно сделать с помощью list comprehension:

[s for s in list_of_strings if s.isdigit()]

newlist = [x for x in fruits if x != "apple"]


# all 


# any 



