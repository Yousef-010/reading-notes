# Reading 08 
> List Comprehensions
- List comprehension is a powerful and concise method for creating lists in Python that becomes essential the more you work with lists, and lists of lists. 
  - Syntax : 
    - __my_new_list = [ expression for item in list ]__
  - Notes about Lists Comprehensions:
    - List comprehension methods are an elegant way to create and manage lists. 
    - In Python, list comprehensions are a more compact way of creating lists. 
    - More flexible than for loops, list comprehension is usually faster than other methods.
  - EXample : 
``` 
# construct a basic list using range() and list comprehensions
# syntax
# [ expression for item in list ]
digits = [x for x in range(10)]
print(digits)

Output
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
- Example based on condition
``` 
even_numbers = [ x for x in range(1,20) if x % 2 == 0]
Output

[2, 4, 6, 8, 10, 12, 14, 16, 18] 
```
- EXample using function in list comprehension:
``` 
def double(x):
    return x*2

nums = [double(x) for x in range(1,10)]
print(nums)
Output

[2, 4, 6, 8, 10, 12, 14, 16, 18] 
```
> Primer on Python Decorators 
- A decorator gives you the ability to take existing functions or classes, add some functionality, and return them without changing the underlying code.
- Decorators are great for encapsulating code that is being reused often, which leads to cleaner and more pleasant to read code.
- Example ``` @classmethod, @staticmethod, and @property. ```
- Identity crisis: 
  - An unintended consequence of decorating a function is that when we return it, it takes the identity of the inner function.
  - You can fix this by using builtin wraps decorator from functools or update_wrapper for class decorators
``` 
from functools import wraps
def works_for_all(func):
    @wraps(func)
    def inner(*args, **kwargs):
        print("I'm decorating something!")
        return func(*args, **kwargs)
    return inner 
```
- A template
- Most decorators follow the following template,
```
def decorate(func):
    @wraps(func)
    def inner(*args, **kwargs):
        # do something before
        ret = func(*args, **kwargs)
        # do something after with ret
        return ret
    return inner

@decorate
def example():
    pass
```
- Applying multiple decorators
```
@dec2
@dec1
def printer(msg):
    print(msg)
```
- Class decorators
  - class decorators are recommended if you want to maintain the state of an object
  - The **__init__()** method stores a reference to the function we’re decorating and other parameters
  - The **__call__()** method makes the class callable so that it can be called on another function.
  - the **call()** method will be called instead of the decorated function and does the same thing as the **inner()** or **wrapper()** functions
```
from functools import update_wrapper

class emphasis:
    def __init__(self, func):
        update_wrapper(self, func) # preserve identity
        self.func = func
    
    def __call__(self, *args, **kwargs):
        ret = self.func(*args, **kwargs)
        return "<b>" + ret + "<b>"

@emphasis
def hello(name):
    return f"Hello{name}"
```


**_THE END_** _____________________________ 


> **Resources**
- https://www.pythonforbeginners.com/basics/list-comprehensions-in-python 
- https://karishmadaga.ca/python/2020/09/25/a-primer-on-python-decorators.html 

     