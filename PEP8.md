# Стиль кода в Python 

>Code is read much more often than it is written (Guido van Rossum)

>Code is a way you treat your coworkers

>Comments are a love letter to your future self

Compared to other language specifications, I find PEPs to be concise, easy-to-digest, and often fun to read.


The most important PEPs, I would say, are the ones I wish my colleagues would read because the topics within are relevant on an almost daily basis. I consider these to be basic python knowledge for a senior engineer. Take that with a grain of salt, I suppose.


PEP 1: PEP Purpose and Guidelines: https://www.python.org/dev/peps/pep-0001

- skim this to get an idea of what's inside, and read it as you become more curious about PEPs after reading some

PEP 20: The Zen of Python: https://www.python.org/dev/peps/pep-0020/

- a good introduction to Python for any level of experience, but a good reminder of how to write idiomatic code

PEP 484: Type Hints: https://www.python.org/dev/peps/pep-0484/

- invaluable when your code base grows, especially if you use an IDE

# PEP8
PEP8 -- это основной документ, регламентирующий стиль кода в Python. Документ носит рекомендательный характер, но следование ему бывает обязательным в некоторых командах. 

## 1. Отступы 

Для того, чтобы сделать отступы, пользуйтесь пробелами. Количество побелов должно быть кратным 4. 

## 2. Табы или пробелы?

PEP8 предлагает использовать пробелы. Tab'ы тоже можно, если весь проект уже написан с их помощью. Главное -- не смешивать tab'ы и пробелы, это вызовет ошибку. 

## 3. Скобки

Выравниваем либо по последнему непробельному символу:
```
my_list = [
    1, 2, 3,
    4, 5, 6,
    ]
    
result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
    )
```    
либо по первому символу всей конструкции: 
```
my_list = [
    1, 2, 3,
    4, 5, 6,
]

result = some_function_that_takes_arguments(
    'a', 'b', 'c',
    'd', 'e', 'f',
)
```

## 4. Длина строки 

Ограничена 79 символами. Текстовые блоки до 72. 

Сделано для того, чтобы было удобно делать review кода. Так можно открывать по несколько файлов на одном экране. Кроме того, такой код легко читается. 

Поэтому разбивают код на строки. При этом разбивать длинные строки по возможности лучше не с помощью символа `\`, а внутри скобок. 

Некоторые команды предпочитают строки длиннее, в этом случае стандарт предлагает длину строки кода 99 символов при длине текста до 72.

## 5. Перенос и бинарный оператор? 

Лучше -- как в математике. 

Плохо:
```
income = (gross_wages +
          taxable_interest +
          (dividends - qualified_dividends) -
          ira_deduction -
          student_loan_interest)
```
Хорошо:

```
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```
Если в вашей команде уже пишут первым способом, то лучше придерживайтесь его. 

## 6. Пробелы

### В выражениях

Здесь пробелы лишние:

```
spam( ham[ 1 ], { eggs: 2 } )
```

А здесь все хорошо:
```
spam(ham[1], {eggs: 2})
```

### Перед запятой, двоеточием, точкой с запятой 

-- пробел не нужен. 

Хорошо:

```
if x == 4: print x, y
x, y = y, x
```
Плохо:
```
if x == 4 : print x , y 
x , y = y , x
```

### В слайсах

Исключение -- для двоеточия в слайсах. Хорошо:
```
ham[1:9], ham[1:9:3], ham[:9:3], ham[1::3], ham[1:9:]
ham[lower:upper], ham[lower:upper:], ham[lower::step]
ham[lower+offset : upper+offset]
ham[lower + offset : upper + offset]
```
Плохо:
```
ham[lower + offset:upper + offset]
ham[1: 9], ham[1 :9], ham[1:9 :3]
ham[lower : : upper]
ham[ : upper]
```

### При вызове функции 

Пробелы не нужны перед скобкой во время вызова функции. 

Хорошо:
```
spam(1)
```
Плохо:
```
spam (1)
```

### Перед скобками 

Здесь тоже не нужен пробел:

Хорошо:
```
dct['key'] = lst[index]
```
Плохо:
```
dct ['key'] = lst [index]
```

### При присваивании 

Когда присваиваете знчения переменной, больше одного пробела с каждой стороны от `=` не требуется:

Хорошо:
```
x = 1
y = 2
long_variable = 3
```
Плохо:
```
x             = 1
y             = 2
long_variable = 3
```
### В операторах  

Арифметические операторы `=`, `*`, `+=`, `-=` и др., операторы сравнения `==`, `<`, `>`, `!=`, `<=`, `>=`, `in`, `not in`, `is`, `is not`, логические операторы `and`, `or`, `not` окружают пробелами, если приоритет оператора в выражении низкий.

Хорошо:
```
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)
```
Плохо
```
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)
```

### В аргументах функции 
Хорошо:

```
def complex(real, imag=0.0):
    return magic(r=real, i=imag)
```
Плохо:
```
def complex(real, imag = 0.0):
    return magic(r = real, i = imag)
```

## 8. Составные выражения 

Хорошо:
```
if foo == 'blah':
    do_blah_thing()
do_one()
do_two()
do_three()
```

Плохо:
```
if foo == 'blah': do_blah_thing()
do_one(); do_two(); do_three()
```

## 9. Комментарии 
Лучше код без комментариев, чем с комментариями, которые противоречат коду:)
```
x = x + 1  # inline comments are made like that 
```
```
def my_functiom(param1, param2):
""" and we comment functions with docstrings """
    pass 
```

Программистам из не-англоязычных стран: пишите комментарии на английском, если не уверены на 120%, что ваш код будут читать только те, кто говорит на вашем языке. 

## 10. Именование переменных 

Не стоит: `l`, `O`, `I`.

(есть более подробно позже в курсе)
snake_case -- змеиный регистр, например, `my_function` 

Хорошо: 
```
count, salary, user, book_data 
is_digit(), get_user(), update_order() 
```
Константы:

`MAX_OVERFLOW`, `TOTAL`, `PI`

## 13. Рекомендации по программированию 

### Проверка на None

Сравнивайте с `None` только через `is` и `is not`, никогда с помощью сравнения на равенство.

Хорошо:
```
if a is None:
    pass
```
Плохо: 
```
if a == None:
    pass
```

Не пишите `if x` когда имеете в виду `if x is not None`. 

Хорошо:
```
if foo is not None:
```
Плохо: 
```
if not foo is None:
```

### Сравнение логических типов 

Хорошо: 
```
if greeting:
```
Плохо:
```
if greeting == True:
```
Хуже:
```
if greeting is True: 
```

## Сохраняйте здравый смысл 

И знайте, когда нарушать кодстайл:) Иногда эти правила неприменимы или расходятся с мнением команды. Это официальные рекомендации, но всего лишь рекомендации. 

> Когда какой-нибудь показатель начинает использоваться как цель, он теряет свою ценность как инструмент.

# Инструменты для контроля стиля

* код-ривью 
* IDE 
* линтеры 

Lint — первоначально — статический анализатор для языка программирования Си, который сообщал о подозрительных или непереносимых на другие платформы выражениях. В начале XXI века термин стал нарицательным для всех программ такого типа. Как инструмент программа лишь анализирует статический исходный код, не скомпилированный в отличие от отладчиков.

Например, pylint (https://pypi.org/project/pylint/), flake8, Bandit 

Демо: https://flakehell.orsinium.dev/ 
