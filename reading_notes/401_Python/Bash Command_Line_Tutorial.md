## Bash Command Line Tutorials

> The Command Line
- it is a text based interface to the system. You are able to enter commands by typing them on the keyboard and feedback will be given to you similarly as text.

- from another resorce : Command Prompt is a command line interpreter application available in most Windows operating systems. It's used to execute entered commands. 


- Openning  
  - If you're on a Mac then you'll find the program Terminal under Applications -> Utilities. An easy way to get to it is the key combination 'command + space' which will bring up Spotlight, then start typing Terminal and it will soon show up.
  - If on Linux then you will probably find it in Applications -> System or Applications -> Utilities. Alternatively you may be able to 'right-click' on the desktop and there may be an option 'Open in terminal'.
  - If you are on Windows and intend to remotely log into another machine then you will need an SSH client. A rather good one is Putty (free) 

- **My opnion :**
 - it is so important to deal with it because is simplify your task on your OS and the pro use it a lot :)  

<br>
 
> Basic Navigation 
- the basics of moving around the system Many tasks rely on being able to get to, or reference the correct location in the system.
- A directory is a file the solo job of which is to store the file names and the related information. All the files, whether ordinary, special, or directory, are contained in directories.
- Unix uses a hierarchical structure for organizing files and directories. This structure is often referred to as a directory tree. The tree has a single root node, the slash character (/), and all other directories are contained below it.

- how to get around it 
  - In order to move around in the system we use a command called **cd** which stands for change directory  **cd [location]**
  - pwd
    Print Working Directory - ie. Where are we currently.
  - ls
    List the contents of a directory.
  - cd
    Change Directories - ie. move to another directory.

- **My opnion :**

  - it likes easy to use you just type tow up to five chars to do a lot of things so it is perfect for the speed of proccesing 


> More About Files

- file.exe - an executable file, or program.
- file.txt - a plain text file.
- file.png, file.gif, file.jpg - an image.
- **__Linux is Case Sensitive__**

- characteristics of files and directories
- A file always has a name.
- A file always takes up storage space.
- A file is always saved in a certain format: a body of text is saved in one of the many text file formats, a photo in one of the many image file formats, etc.
- A file contains information on when it was created and when it was last modified.
- Files usually have access rights, especially if they are online.
- Files are saved on the user’s own computer or in a remote location.

- **My opnion :**
- there is a lot of intersting characteristics in actual this is not for just intersting, it is to check your work and save it correctly 


> Manual Pages 
- The manual pages are a set of pages that explain every command available on your system including what they do, the specifics of how you run them and what command line arguments they accept

- man <command>
Look up the manual page for a particular command.
man -k <search term>
- Do a keyword search for all manual pages containing the given search term.
<term>
- Within a manual page, perform a search for 'term'
- n  After performing a search within a manual page, select the next found item.

- _ _please visit this link_ _
 [see this link ](https://medium.com/javarevisited/top-10-unix-and-linux-productivity-tips-for-programmers-and-developers-c748129cf3e8)

- **My opnion :**
- it is so important to learn the most commonly used commands to deal fastly with the whole ENV 

> File Manipulation

- How to make files and directories 
  - mkdir [options] <Directory>
- How to remove files and directories
  - rmdir [options] <Directory>
- How to rename files and directories 
  - mv
- How to copy files and directories
  - cp [options] <source> <destination>
- How to move files and directories
  - mv [options] <source> <destination>

- **My opnion :**
- easy to learn and use 

> Cheat Sheet 
>> you can see this link to get the summary of the above or read the more important in the below  
   [Cheat Sheet](https://ryanstutorials.net/linuxtutorial/cheatsheet.php)

>>> 
   - pwd
Where am I in the system. 
   - ls [path]
Perform a listing of the given path or your current directory.
Common options: -l, -h, -a
   - cd [path]
Change into the given path or into your home directory.
   - Path
A description of where a file or directory is on the filesystem.
   - Absolute Path
One beginning from the root of the file system (eg. /etc/sysconfig ).
   - Relative Path
One relative to where you currently are in the system (eg. Documents/music ).
   - ~ (tilde)
Used in paths as a reference to your home directory (eg. ~/Documents ).
   - . (dot)
Used in paths as a reference to your current directory (eg. ./bin ).
   - .. (dot dot)
Used in paths as a reference to your current directories parent directory (eg. ../bin ).
   - TAB completion
Start typing and press TAB. The system will auto complete the path. Press TAB twice and it will show you your alternatives.
   - file [path]
Find out what type of item a file or directory is.
   - Spaces in names
Put whole path in quotes ( " ) or a backslash ( \ ) in front of spaces.
   - Hidden files and directories
A name beginning with a . (dot) is considered hidden.
   - man <command>
View the man page for a command.
   - man -k <search term>
Search for man pages containing the search term.
   - Press q to exit man pages
   - mkdir <directory name>
Create a directory 
   - rmdir <directory name>
Remove a directory (only if empty).
   - touch <file name>
Create a blank file.
   - cp <source> <destination>
Copy the source file to the destination.
   - mv <source> <destination>
Move the source file to the destination.
   - rm <path>
Remove a file or directory.
Common options: -r -f
   - du -sh ./*
Find the size of every directory in your current directory.
   - df -h
Display how much disk space is used and also free.
   - basename -s .jpg -a *.jpg | xargs -n1 -i cp {}.jpg {}_original.jpg
Make a copy of every jpg image file in the current directory and rename adding _original
   - find /home -mtime -1
Find all files in the given directory (and subdirectories) which have been modified in the last 24 hours.
   - shutdown -h now
Shutdown the system. (Replace -h with -r for reboot.)
 

***THE END : )***



