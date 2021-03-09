## В предыдущей серии 

Напомню, что в прошлый раз мы обсуждали функциональные возможности в Python. 

### map
Синтаксис: `map(function, iterable(s))`

```
chr_list = ['1', '2', '3', '4', '5', '6', '7']
list(map(int, chr_list))
```
В сочетании с другими функциями:

```
pets = ["cat", "dog", "parrot", "fish", "turtle"]
list(map(str.upper, pets))
list(map(len, pets))
```

### filter

Синтаксис: `filter(function, iterable)`

"Фильтрует" значения списка с помощью переданной функции. Отфильтруем только строки, состоящие из чисел:
```
list_of_strings = ['one', 'two', 'list', '', 'dict', '100', '1', '50']
list(filter(str.isdigit, list_of_strings))
```

Например, можно отфильтровать только взрослых, определив дополнительную функцию `is_adult()`: 
```
ages = [18, 5, 12, 32, 17, 24]

def is_adult(x):
    return True if x >= 18 else False

list(filter(is_adult, ages))
``` 

# Лямбда-функции в Python 

Вы знаете, что в Python можно определить свою функцию. Для этого мы используем ключевое слово `def`. Например:  

```
def square(a):
    result = a*a
    print result 
```
Такая функция получит имя `square()`. 

В Python также можно определять функции, которые не имеют имен, то есть, анонимные функции.

Синтаксис: `lambda arguments: expression`

Похоже на: `f(x) = y`

Анатомия поользовательской функции: 
* `def` 
* параметры в скобках  
* `return` 

Вот это:

```
def square(a):
    result = a*a
    print result 
```

-- то же, что вот это:
```
lambda_square = lambda a: a*a 
```

Мы не используем ничего из перечисленного выше, а вместо `return` пишем сразу выражение, результат которого нужно вернуть. А вызываются эти функции одинаково: 
```
>>> square(5)
25 
>>> lambda_square(5)
25 
```

Зачем нам анонимные функции, если обычные уже есть, а функционал такой же? 

## Лямбды и функциональный стиль в Python. 

Попробуем совместить лямбды с `filter` и `map`. 
```
ages = [18, 5, 12, 32, 17, 24]

def is_adult(x):
    return True if x >= 18 else False

list(filter(is_adult, ages))


is_adult = lambda age: True if age >= 18 else False
list(filter(is_adult, ages))
```

Или даже: 

```
ages = [18, 5, 12, 32, 17, 24]
list(filter(lambda age: True if age >= 18 else False, ages))
```

Еще пример: 
```
letters = ['a', 'b', 'd', 'e', 'i', 'j', 'o']

def is_vowel(letter):
    vowels = ['a', 'e', 'i', 'o', 'u']
    return True if letter in vowels else False
   
vowels = list(filter(is_vowel, letters))

```
Переписываем на лямбда-функцию: 
```
letters = ['a', 'b', 'd', 'e', 'i', 'j', 'o']
vowels = list(filter(lambda l: True if l in ['a', 'e', 'i', 'o', 'u'] else False, letters))
vowels
```
Еще пример. Было: 
```
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

def if_odd(x):
    return True if x % 2 != 0 else False

result = filter(if_odd, numbers) 
print(list(result))
```
Стало: 
```
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
list(filter(lambda x: True if x % 2 != 0 else False, numbers))
```

Еще пример. Было -- как в начале в примере со squares. Стало: 
```
li = [5, 7, 22, 97, 54, 62, 77, 23, 73, 61] 
list(map(lambda x: x*2, li)) 
```

## Лямбды и сортировки 
Канонический пример использования 

Синтаксис: `a = sorted(iterable, key=..., reverse=...)`

Например, можно быстро сортировать список кортежей:
```
student_tuples = [
    ('john', 'A', 15),
    ('jane', 'B', 12),
    ('dave', 'B', 10),
]
sorted(student_tuples, key=lambda student: student[2])   # sort by age
[('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
```
От замены переменной внутри лямбда-функции ничего не меняется:   

```
lst = [('candy','30','100'), 
       ('apple','10','200'), 
       ('baby','20','300')]
       
lst.sort(key=lambda x:x[1])
print(lst)
```

Годится для сортировки словаря в тех версиях интерпретатора, где словари сохраняют порядок: 

```
d = {2:3, 1:89, 4:5, 3:0}
d1 = dict(sorted(d.items(), key = lambda x:x[0]))
```

Все! 
