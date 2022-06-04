# Reading 03 

> Read & Write Files in Python
- file is a contiguous set of bytes used to store data
- This data is organized in a specific format and can be anything as simple as a text file or as complicated as a program executable

- > file systems are composed of three main parts:
  - Header: metadata about the contents of the file (file name, size, type, and so on)
  - Data: contents of the file as written by the creator or editor
  - End of file (EOF): special character that indicates the end of the file
  
- >Opening and Closing a File in Python
    - file = open('dog_breeds.txt')
    - file name dot close()
    - with open('dog_breeds.txt', 'r') as reader:
      - Further file processing goes here

| Character   | Meaning                   |
|-------------|---------------------------|
| 'r'     | Open for reading (default)|
|'w'    | Open for writing, truncating (overwriting) the file first |
 |'rb' or 'wb'    | Open in binary mode (read/write using byte data) |


>Reading and Writing Opened Files

| Character   | Meaning                   |
|-------------|---------------------------|
|.read(size=-1)  | This reads from the file based on the number of size bytes. If no argument is passed or None or -1 is passed, then the entire file is read.|
|.readline(size=-1)  | This reads at most size number of characters from the line. This continues to the end of the line and then wraps back around. If no argument is passed or None or -1 is passed, then the entire line (or rest of the line) is read. |
|.readlines()   | This reads the remaining lines from the file object and returns them as a list. |


>### Exceptions in Python
- >Exceptions versus Syntax Errors
   - Syntax errors occur when the parser detects an incorrect statement. 
    ``` 
   print( 0 / 0 ))
      File "<stdin>", line 1
        print( 0 / 0 ))
                      ^
    SyntaxError: invalid syntax 
    ```
  ```
   print( 0 / 0)
     Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
     ZeroDivisionError: integer division or modulo by zero
  ```
- >Raising an Exception
    - We can use raise to throw an exception if a condition occurs. The statement can be complemented with a custom exception.
    ```
    x = 10
     if x > 5:
    raise Exception('x should not exceed 5. The value of x was: {}'.format(x))  
  ```
    ```
     Traceback (most recent call last):
      File "<input>", line 4, in <module>
     Exception: x should not exceed 5. The value of x was: 10
  ```
  
- >The AssertionError Exception
    - Instead of waiting for a program to crash midway, you can also start by making an assertion in Python. We assert that a certain condition is met. If this condition turns out to be True, then that is excellent! The program can continue. If the condition turns out to be False, you can have the program throw an AssertionError exception.
   ```
    import sys
    assert ('linux' in sys.platform), "This code runs on Linux only."
  ```
    ```
         Traceback (most recent call last):
         File "<input>", line 2, in <module>
         AssertionError: This code runs on Linux only.
    ```
  
- >he try and except Block: Handling Exceptions
  - The try and except block in Python is used to catch and handle exceptions. Python executes code following the try statement as a “normal” part of the program. The code that follows the except statement is the program’s response to any exceptions in the preceding try clause
  ```
    try:
    linux_interaction()
    except AssertionError as error:
    print(error)
    print('The linux_interaction() function was not executed')
  ```
  
> here is my result in the quize 

- Reading and Writing Files in Python

- Your Score: 62%

- You completed Real Python's Reading and Writing Files in Python quiz with 5 correct answers out of 8 questions.

