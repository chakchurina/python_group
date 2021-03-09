# Лямбда-функции в Python 

В Python можно определить свою функцию. Для этого мы используем ключевое слово `def`. Например:  

```
def square(a):
    result = a*a
    print result 
```
Такая функция получит имя `square()`. Но в Python также можно определять функции, которые не имеют имен, то есть, анонимные функции: 

Синтаксис: `lambda arguments: expression`
Похоже на: `f      (x)      = y`

Вот это: 
```
def square(a):
    result = a*a
    print result 
```
-- то же, что вот это:
```
lambda_suare = lambda a: a*a 
```
И вызывается одинаково: 
```
>>> square(5)
25 
>>> lambda_square(5))
25 
```
А зачем нам анонимные функции, если функционал такой же, а обычные уже есть? 



As we can see in the above example both the cube() function and lambda_cube() function behave the same and as intended. Let’s analyze the above example a bit more:

Without using Lambda: Here, both of them return the cube of a given number. But, while using def, we needed to define a function with a name cube and needed to pass a value to it. After execution, we also needed to return the result from where the function was called using the return keyword.
Using Lambda: Lambda definition does not include a “return” statement, it always contains an expression that is returned. We can also put a lambda definition anywhere a function is expected, and we don’t have to assign it to a variable at all. This is the simplicity of lambda functions.
Lambda functions can be used along with built-in functions like filter(), map() and reduce().
