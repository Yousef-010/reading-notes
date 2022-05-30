# Reading  02
> TDD with Python

- Test Driven Development is an approach in which we build a test first, then fail the test and finally refactor our code to pass the test.
- >benefits of TDD
- In TDD we build test before adding any new feature to it, that means in TDD approach our entire code is covered under the test. That’s a great benefit of TDD as compared to the code which has no test coverage.
- In TDD one should have a specific target before adding new functionality. This means before adding any new functionality one should be clear about its outcome.
- In an application, one method depends on the other. When we write tests before the method that means we should have clear thoughts about the interfaces between the methods. That allows us to integrate our method with the entire application efficiently and help in making our application modular too.
- As the entire code is covered by the test that means our final application will be less buggy. This is a big advantage of the TDD approach.


> If name equals main
- Before executing code, Python interpreter reads source file and define few special variables/global variables. 
- If the python interpreter is running that module (the source file) as the main program, it sets the special __name__ variable to have a value “__main__”. If this file is being imported from another module, __name__ will be set to the module’s name. Module’s name is available as value to __name__ global variable. 
- A module is a file containing Python definitions and statements. The file name is the module name with the suffix .py appended. 


> Recursion
- The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called a recursive function. Using a recursive algorithm
- **What is base condition in recursion?** 
- In the recursive program, the solution to the base case is provided and the solution of the bigger problem is expressed in terms of smaller problems.


> Modules and Packages
- Modular programming is the process of breaking a large, unwieldy programming task into separate, smaller, more manageable subtasks or modules. Individual modules can then be put together like building blocks to create a larger application.
- > benefits of Modules and Packages
  - Scoping
  - Reusability
  - Maintainability
  - Simplicity
  
> python Lists 
- Python has a great built-in list type named "list". List literals are written within square brackets [ ]. Lists work similarly to strings -- use the len() function and square brackets [ ] to access data.
- **EX** colors = ['red', 'blue', 'green']

> pytest in Python 
 - The pytest framework makes it easy to write small, readable tests, and can scale to support complex functional testing for applications and libraries.

 - > Advantages of pytest :
   - Very easy to start with because of its simple and easy syntax.
   - Can run tests in parallel.
   - Can run a specific test or a subset of tests
   - Automatically detect tests
   - Skip tests
   - Open source
 

