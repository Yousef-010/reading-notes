# Reading 19 Automation 
> Regular Expression 
- Regular Expressions, often shortened as regex, are a sequence of characters used to check whether a pattern exists in a given text (string) or not.  
- regular expressions are supported by the re module. That means that if you want to start using them in your Python scripts, you have to import this module with the help of import:
  - import re :
- example 
```
Examples are 'A', 'a', 'X', '5'.
pattern = r"Cookie"
sequence = "Cookie"
if re.match(pattern, sequence):
    print("Match!")
else: print("Not a match!")
output : 
Match!
```
- Function Provided by 're'
The re library in Python provides several functions to make your tasks easier. You have already seen some of them, such as the re.search(), re.match()
- compile(pattern, flags=0)
  - Regular expressions are handled as strings by Python. However, with compile(), you can computer a regular expression pattern into a regular expression object. 
  - When you need to use an expression several times in a single program, using compile() to save the resulting regular expression object for reuse is more efficient than saving it as a string.
- search(pattern, string, flags=0)
  - With this function, you scan through the given string/sequence, looking for the first location where the regular expression produces a match.
- match(pattern, string, flags=0)
  - Returns a corresponding match object if zero or more characters at the beginning of string match the pattern. Else it returns None, if the string does not match the given pattern.


> shutil — High-level File Operations¶
- Purpose:	High-level file operations.
- The shutil module includes high-level file operations such as copying and archiving.
- Copying Files¶
  - copyfile() copies the contents of the source to the destination and raises IOError if it does not have permission to write to the destination file
```
shutil_copyfile.py
import glob
import shutil

print('BEFORE:', glob.glob('shutil_copyfile.*'))
shutil.copyfile('shutil_copyfile.py', 'shutil_copyfile.py.copy')
print('AFTER:', glob.glob('shutil_copyfile.*'))
```
```
$ python3 shutil_copyfile.py

BEFORE: ['shutil_copyfile.py']
AFTER: ['shutil_copyfile.py', 'shutil_copyfile.py.copy']
```
- Copying File Metadata
- By default when a new file is created under Unix, it receives permissions based on the umask of the current user. To copy the permissions from one file to another, use copymode()
```
shutil_copymode.py
import os
import shutil
import subprocess

with open('file_to_change.txt', 'wt') as f:
    f.write('content')
os.chmod('file_to_change.txt', 0o444)
print('BEFORE:', oct(os.stat('file_to_change.txt').st_mode))
shutil.copymode('shutil_copymode.py', 'file_to_change.txt')
print('AFTER :', oct(os.stat('file_to_change.txt').st_mode))
```
```
$ python3 shutil_copymode.py

BEFORE: 0o100444
AFTER : 0o100644
```
- Finding Files 
- The which() function scans a search path looking for a named file. The typical use case is to find an executable program on the shell’s search path defined in the environment variable PATH
```
shutil_which.py
import shutil

print(shutil.which('virtualenv'))
print(shutil.which('tox'))
print(shutil.which('no-such-program'))
```
```
$ python3 shutil_which.py

/Users/dhellmann/Library/Python/3.5/bin/virtualenv
/Users/dhellmann/Library/Python/3.5/bin/tox
None
```


> Watchdog 
- Python API library and shell utilities to monitor file system events.
- Directory monitoring made easy with
  - A cross-platform API.
  - A shell tool to run commands in response to directory changes.
- $ pip install watchdog
```
# import the modules
import sys
import time
import logging
from watchdog.observers import Observer
from watchdog.events import LoggingEventHandler

if __name__ == "__main__":
	# Set the format for logging info
	logging.basicConfig(level=logging.INFO,
						format='%(asctime)s - %(message)s',
						datefmt='%Y-%m-%d %H:%M:%S')

	# Set format for displaying path
	path = sys.argv[1] if len(sys.argv) > 1 else '.'

	# Initialize logging event handler
	event_handler = LoggingEventHandler()

	# Initialize Observer
	observer = Observer()
	observer.schedule(event_handler, path, recursive=True)

	# Start the observer
	observer.start()
	try:
		while True:
			# Set the thread sleep time
			time.sleep(1)
	except KeyboardInterrupt:
		observer.stop()
	observer.join()
```
- output will be 
![image](https://media.geeksforgeeks.org/wp-content/uploads/20191022110201/watchdog-python.png)


> Resources
- https://pythonhosted.org/watchdog/ 
- https://pymotw.com/3/shutil/
- https://www.datacamp.com/community/tutorials/python-regular-expression-tutorial