# Reading 07 
> Python Scope 
 - > Names and Scopes in Python
   - Since Python is a dynamically-typed language, variables in Python come into existence when you first assign them a value. 
 - > Python Scope vs Namespace 
   - Python scope determines where in your program a name is visible. Python scopes are implemented as dictionaries that map names to objects. 
   - These dictionaries are commonly called namespaces. These are the concrete mechanisms that Python uses to store names
> Using the LEGB Rule for Python Scope
   - > Local (or function) scope
     - the code block or body of any Python function or lambda expression. This Python scope contains the names that you define inside the function. These names will only be visible from the code of the function.
   - > Enclosing (or nonlocal) scope 
     - a special scope that only exists for nested functions. If the local scope is an inner or nested function, then the enclosing scope is the scope of the outer or enclosing function.
     - This scope contains the names that you define in the enclosing function. The names in the enclosing scope are visible from the code of the inner and enclosing functions.
   - > Global (or module) scope
     - is the top-most scope in a Python program, script, or module.
     - This Python scope contains all of the names that you define at the top level of a program or a module. Names in this Python scope are visible from everywhere in your code.
   - > Built-in scope 
     - is a special Python scope that’s created or loaded whenever you run a script or open an interactive session
     - This scope contains names such as keywords, functions, exceptions, and other attributes that are built into Python. 
     - Names in this Python scope are also available from everywhere in your code. It’s automatically loaded by Python when you run a program or script.

> Modifying the Behavior of a Python Scope
   - nonlocal names can be accessed from inside nested functions, but they can’t be modified or updated from there.
  > The global Statement
   - The statement consists of the global keyword followed by one or more names separated by commas. You can also use multiple global statements with a name (or a list of names).
     - All the names that you list in a global statement will be mapped to the global or module scope in which you define them.
       - example where you try to update a global variable from within a function:
       ```
       >>> counter = 0  # A global name
        >>> def update_counter():
          ...     counter = counter + 1  # Fail trying to update counter
          ...
        >>> update_counter()
          Traceback (most recent call last):
            File "<stdin>", line 1, in <module>
            File "<stdin>", line 2, in update_counter
          UnboundLocalError: local variable 'counter' referenced before assignment 
         ```
       
       ```
        >>> counter = 0  # A global name
        >>> def update_counter():
          ...     global counter  # Declare counter as global
          ...     counter = counter + 1  # Successfully update the counter
          ...
        >>> update_counter()
        >>> counter
          1
        >>> update_counter()
        >>> counter
          2
        >>> update_counter()
        >>> counter
          3
       ```
       
   >  The nonlocal Statement
   - The nonlocal statement consists of the nonlocal keyword followed by one or more names separated by commas.
   - These names will refer to the same names in the enclosing Python scope. The following example shows how you can use nonlocal to modify a variable defined in the enclosing or nonlocal scope:
   - EX 
   ```
>>> def func():
...     var = 100  # A nonlocal variable
...     def nested():
...         nonlocal var  # Declare var as nonlocal
...         var += 100
...
...     nested()
...     print(var)
...
>>> func()
200
```

> Using Enclosing Scopes as Closures
- Closures are a special use case of the enclosing Python scope.
- When you handle a nested function as data, the statements that make up that function are packaged together with the environment in which they execute.
- **The resulting object is known as a closure.**
- EX
```commandline
>>> def power_factory(exp):
...     def power(base):
...         return base ** exp
...     return power
...
>>> square = power_factory(2)
>>> square(10)
100
>>> cube = power_factory(3)
>>> cube(10)
1000
>>> cube(5)
125
>>> square(15)
225
```

> Bringing Names to Scope With import
- you’ll need to bring the names in those separate modules to your __main__ module. 
- EX 
```commandline
>>> dir()
['__annotations__', '__builtins__',..., '__spec__']
>>> import sys
>>> dir()
['__annotations__', '__builtins__',..., '__spec__', 'sys']
>>> import os
>>> dir()
['__annotations__', '__builtins__',..., '__spec__', 'os', 'sys']
>>> from functools import partial
>>> dir()
['__annotations__', '__builtins__',..., '__spec__', 'os', 'partial', 'sys']
```

> Discovering Unusual Python Scopes
  - Comprehensions : A comprehension is a compact way to process all or part of the elements in a collection or sequence. 
```
>>> [item for item in range(5)]
[0, 1, 2, 3, 4]
>>> item  # Try to access the comprehension variable
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    item
NameError: name 'item' is not defined
```
  - Exception blocks :The exception variable is a variable that holds a reference to the exception raised by a try statement.
```commandline
>>> lst = [1, 2, 3]
>>> try:
...     lst[4]
... except IndexError as err:
...     # The variable err is local to this block
...     # Here you can do anything with err
...     print(err)
...
list index out of range
>>> err # Is out of scope
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    err
NameError: name 'err' is not defined
```
  - Classes and instances : The names assigned at the top level of the class live in this local scope. The names that you assigned inside a class statement don’t clash with names elsewhere.
```commandline
>>> class A:
...     attr = 100
...
>>> A.__dict__.keys()
dict_keys(['__module__', 'attr', '__dict__', '__weakref__', '__doc__'])

```

__THE END__ **THANK YOU FOR READING**
> resources: 
-https://realpython.com/python-scope-legb-rule/#modifying-the-behavior-of-a-python-scope 