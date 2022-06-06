# Reading 04 
> Classes and Objects 
- Objects are an encapsulation of variables and functions into a single entity
- Classes are essentially a template to create your objects
- A class is a user-defined blueprint or prototype from which objects are created. Classes provide a means of bundling data and functionality together. Creating a new class creates a new type of object, allowing new instances of that type to be made.
- Each class instance can have attributes attached to it for maintaining its state. Class instances can also have methods (defined by their class) for modifying their state.
  - Classes are created by keyword class.
  - Attributes are the variables that belong to a class.
  - Attributes are always public and can be accessed using the dot (.) operator. Eg.: Myclass.Myattribute
> Class Objects
- An Object is an instance of a Class. A class is like a blueprint while an instance is a copy of the class with actual values
- a Object consists of : 
  - State: It is represented by the attributes of an object. It also reflects the properties of an object.
  - Behavior: It is represented by the methods of an object. It also reflects the response of an object to other objects.
  - Identity: It gives a unique name to an object and enables one object to interact with other objects.
> Class and Instance Variables
- Instance variables are for data, unique to each instance and class variables are for attributes and methods shared by all instances of the class. Instance variables are variables whose value is assigned inside a constructor or method with self whereas class variables are variables whose value is assigned in the class.

> Thinking Recursively
- Problems (in life and also in computer science) can often seem big and scary. But if we keep chipping away at them, more often than not we can break them down into smaller chunks trivial enough to solve. This is the essence of thinking recursively
- **Recursive Functions in Python**
- A recursive function is a function defined in terms of itself via self-referential expressions.
- This means that the function will continue to call itself and repeat its behavior until some condition is met to return a result
  - **EXAMPLE**
  - ```commandline
    def factorial_recursive(n):
     # Base case: 1! = 1
        if n == 1:
              return 1

        # Recursive case: n! = n * (n-1)!
        else:
             return n * factorial_recursive(n-1)
    ```

> Maintaining State
- Thread the state through each recursive call so that the current state is part of the current call’s execution context
- Keep the state in global scope
  - ``` 
    # Global mutable state
    current_number = 1
    accumulated_sum = 0


    def sum_recursive():
        global current_number
        global accumulated_sum
        # Base case
        if current_number == 11:
            return accumulated_sum
        # Recursive case
        else:
            accumulated_sum = accumulated_sum + current_number
            current_number = current_number + 1
            return sum_recursive()
    ```
> Pytest Fixtures and Coverage
  - > Fixtures
    - do some objects available to all of your tests. Those objects might contain data you want to share across tests, or they might involve the network or filesystem. These are often known as "fixtures" in the testing world, and they take a variety of different forms.
    - In pytest, you define fixtures using a combination of the ```pytest.fixture``` decorator, along with a function definition
      - usege inside code ```@pytest.fixture.```
      - **NOTE** 
        - If your fixture uses "yield" instead of "return", pytest understands that the post-yield code is for tearing down objects and connections. And yes, if your fixture has "module" scope, pytest will wait until all of the functions in the scope have finished executing before tearing it down. 
  - >Coverage
    - its to checking that your tests have run all of the code.
    - installing ```pip pytest-cov```

> Another info about Anatomy of a test to know 
- Arrange
    -  is where we prepare everything for our test.
- Act
    - is the singular, state-changing action that kicks off the behavior we want to test
- Assert
    - is where we look at that resulting state and check if it looks how we’d expect after the dust has settled
- Cleanup
    - is where the test picks up after itself, so other tests aren’t being accidentally influenced by it.

> **References** : https://docs.pytest.org/en/latest/explanation/anatomy.html#test-anatomy 