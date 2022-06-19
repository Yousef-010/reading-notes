# Reading 09
###### ___________________________________________
> Dunder Methods
- What Are Dunder Methods? 
- special methods are a set of predefined methods you can use to enrich your classes. They are easy to recognize because they start and end with double underscores, for example __ init __ or __ str __.
``` 
class LenSupport:
    def __len__(self):
        return 42

>>> obj = LenSupport()
>>> len(obj)
42
```
- Object Initialization: __init__
- Right upon starting my class I already need a special method. To construct account objects from the Account class I need a constructor which in Python is the __init__ dunder:
```
class Account:
    """A simple account class"""

    def __init__(self, owner, amount=0):
        """
        This is the constructor that lets us create
        objects from this class
        """
        self.owner = owner
        self.amount = amount
        self._transactions = []
```

- Object Representation: __ str __, __ repr __
- It’s common practice in Python to provide a string representation of your object for the consumer of your class (a bit like API documentation.) There are two ways to do this using dunder methods:
  - __ repr __: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.

  - __ str __: The “informal” or nicely printable string representation of an object. This is for the enduser.
  - ```
        class Account:
    # ... (see above)

    def __repr__(self):
        return 'Account({!r}, {!r})'.format(self.owner, self.amount)

    def __str__(self):
        return 'Account of {} with starting amount: {}'.format(
            self.owner, self.amount)
    ```
    
- Context Manager Support and the With Statement: __ enter __, __ exit __
- ```
    class Account:
    # ... (see above)

    def __enter__(self):
        print('ENTER WITH: Making backup of transactions for rollback')
        self._copy_transactions = list(self._transactions)
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        print('EXIT WITH:', end=' ')
        if exc_type:
            self._transactions = self._copy_transactions
            print('Rolling back to previous transactions')
            print('Transaction resulted in {} ({})'.format(
                exc_type.__name__, exc_val))
        else:
            print('Transaction OK')
  ```
>  Statistics in Python — Probability 
- What is probability? 
- An event is some outcome of interest. To calculate the chance of an event happening, we also need to consider all the other events that can occur. 
- The quintessential representation of probability is the humble coin toss
  - Flipping a heads
  - Flipping a tails
- Example 
```
import random
def coin_trial():
heads = 0
for i in range(100):
    if random.random() <= 0.5:
        heads +=1
    return heads
def simulate(n):
    trials = []
    for i in range(n):
        trials.append(coin_trial())
    return(sum(trials)/n)
simulate(10)
>>> 5.4
simulate(100)
>>> 4.83
simulate(1000)
>>> 5.055
simulate(1000000)
>>> 4.999781
```
- The data and the distribution 
  - The most important qualities to notice about the normal distribution is its symmetry and its shape.
- Revisiting the normal 
  - The normal distribution is significant to probability and statistics thanks to two factors:
  - Central Limit Theorem
    - the closer the average of these trials approach the true probability, even if the individual trials themselves are imperfect
  - Three Sigma Rule.
    - The Three Sigma rule, also known as the empirical rule or 68-95-99.7 rule, is an expression of how many of our observations fall within a certain distance of the mean.








> Resources: 
- https://dbader.org/blog/python-dunder-methods 
- 