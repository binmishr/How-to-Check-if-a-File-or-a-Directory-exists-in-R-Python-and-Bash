# How-to-Check-if-a-File-or-a-Directory-exists-in-R-Python-and-Bash

When we build Data Workflows and Machine Learning Pipelines, it is common to check for the existence of specific files and directories (folders). We will provide some hands-on examples of how you check for files or directories in R, Python and Bash.
Check for the existence of File or a Directory in R

For this example, we have created a file called “myfile.txt” and a directory called “my_test_folder“.
How to Check if a File Exists

We can easily check if a file exists with the file.exists() command from the base package. Let’s have a look at the following example:

if (file.exists("myfile.txt")) {
  
  print("The file exists")
} else {
  
  print("The file does not exist")
}

And we get:

[1] "The file exists"

Let’s try now with a file that does not exist:

if (file.exists("nofile.txt")) {
  
  print("The file exists")
} else {
  
  print("The file does not exist")
}

And we get:

[1] "The file does not exist"

Note that the expression “if not file exists” can be written as follows by adding the ! within the if statement:

if (!file.exists("myfile.txt"))

Finally, if you want to create an empty file, you can run the command:

file.create("mynewfile.txt")

How to Check if a Directory Exists

Similarly, with the file.exists() we can work with the dir.exists() command for the directories. For example:

if (dir.exists("my_test_folder")) {
  
  print("The direcoty exists")
} else {
  
  print("The file does not exist")
}

We get:

[1] "The direcoty exists"

Now, let’s do the following exercise. We will check if the directory exists and if not, then we will create a new one.

if (dir.exists("my_new_folder")) {
  
  print("The direcoty exists")
} else {
  
  # create the "my_new_folder
  dir.create("my_new_folder")
}

And the folder “my_new_folder” created under our working directory.
Check for the existence of File or a Directory in Python

For this example, we have created a file called “myfile.txt” and a directory called “my_test_folder“.
How to Check if a File Exists

We can work with the os module as follows:

import os.path

if os.path.isfile('myfile.txt'):
    print("The file exists")
else:
    print("The file does not exist")


The file exists

We can also work with the pathlib module as follows:

from pathlib import Path

my_file = Path("myfile.txt")
if my_file.is_file():
    print("The file exists")
else:
    print("The file does not exist")

Note that in Python you can create an empty file with the command with open(filename.txt, 'w'). For example:

import os

if not os.path.isfile('myfile.txt'):
    with open('myfile.txt', 'w'): pass

Or

if not os.path.isfile('myfile.txt'):
    file_name = 'myfile2.txt'
    f = open(file_name, 'w')
    f.close()

Keep in mind the following modes when you open a file:

w  write mode
r  read mode
a  append mode
w+  create file if it doesn't exist and open it in (over)write mode
    [it overwrites the file if it already exists]
r+  open an existing file in read+write mode
a+  create file if it doesn't exist and open it in append mode

How to Check if a Directory Exists

Similarly, we can check if a directory exists as follows:

import os.path

if os.path.isdir('my_test_folder'):
    print("The directory exists")
else:
    print("The directory does not exist")


The directory exists

Note that you can create a directory as follows:

import os
if not os.path.isdir('my_folder'):
    os.makedirs('my_folder')

Finally, To check whether a Path object exists independently of whether is it a file or directory, use exists():

from pathlib import Path

my_file = Path("/path/to/file")
if my_file.exists():
    # path exists

Or with the os module:

import os.path

path.exists("myfile.txt")

Check for the existence of File or a Directory in Bash
How to Check if a File Exists

For this example, we have created a file called “myfile.txt” and a directory called “my_test_folder“. We can work with the -f flag which checksfor regular file existence not a directory:

Assume that the mycheck.sh script is the following:

if [ -f myfile.txt ] 
then
    echo "The file exists"
else 
   echo "The file does not exist"
fi

How to Check if a File or a Directory exists in R, Python and Bash 1

And we get the the file exists as expected. Now, if we want to create an empty script we can run the command:

touch filename.txt

How to Check if a Directory Exists

Similarly, we can check for directories by changing the -f flag to -d that checks for directory existence. Assume that the dircheck.sh is the following:

if [ -d my_test_folder ] 
then
    echo "The directory exists"
else 
   echo "The directory does not exist"
fi

How to Check if a File or a Directory exists in R, Python and Bash 2

And as expected, we received the message that the directory exists.

Note, that if you want to create a directory, you can run the following command:

mkdir yourdirectory

Finally, notice that the expression “if not” is with a ! as follows:

if [ ! -d my_test_folder ] 

Finally, we provide the necessary flags for files and directories checks in bash.

-b filename – Block special file

-c filename – Special character file

-d directoryname – Check for directory Existence

-e filename – Check for file existence, regardless of type (node, directory, socket, etc.)

-f filename – Check for regular file existence not a directory

-G filename – Check if file exists and is owned by effective group ID

-G filename set-group-id – True if file exists and is set-group-id

-k filename – Sticky bit

-L filename – Symbolic link

-O filename – True if file exists and is owned by the effective user id

-r filename – Check if file is a readable

-S filename – Check if file is socket

-s filename – Check if file is nonzero size

-u filename – Check if file set-user-id bit is set

-w filename – Check if file is writable

-x filename – Check if file is executable
