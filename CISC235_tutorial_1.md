## Tutorial 1: Coding and debugging in IDE with package mangement tool

*Note: I am using a non-M1 MacBook Pro. The setup steps might be different on your machine.*

### Step 1: Install Visual Studio Code 

Follow the following official document to download and install Visual Studio Code based on the operation system of your machine.

[VS download page](https://code.visualstudio.com/Download)

If you have difficulty in installing VS code, check the installation guide 

[VS install guideline page](https://code.visualstudio.com/docs/setup/mac)

Once you successfully installed VS code, your should be able to see the welcome page. 

Mine is shown as below (note, yours would be different because i have created python projects using VS code before)

<img width="1500" alt="image" src="https://user-images.githubusercontent.com/122241609/211230262-0ea269c0-959a-424b-a368-09cb70dbd3d1.png">


### Step 2: Getting Started with Python in VS Code

Follow the following official document to setup your Python development environment. You need to install Python extension for VS code.

[Python setup in VS code guideline page](https://code.visualstudio.com/docs/python/python-tutorial)

Note, you need to install Python 3 on your machine first and verify in terminal that Python 3 has been succesfully installed. 

[Python 3 download page](https://www.python.org/downloads/)

The above tutorial introduces you to VS Code as a Python environment, primarily how to edit, run, and debug code through the following tasks:

- Write, run, and debug a Python "Hello World" Application
- Learn how to install packages by creating Python virtual environments
- Write a simple Python script to plot figures within VS Code

### Step 3: Install Ananconda on your machine

Anaconda helps you create an environment for many different versions of Python and package versions. Anaconda is also used to install, remove, and upgrade packages in your project environments. 
I believe it is always a good practice to manage Python environments using package management tool, though you might not feel the benefits if you just start experience it and do not have many complex Python projects.

Similar to above stpes, you need to follow the official documentation to install Ananconda based on your machine type. 

[Ananconda installation page](https://docs.anaconda.com/anaconda/install/index.html)

Remember to verify your installation: 

[Verifying Ananconda installation](https://docs.anaconda.com/anaconda/install/verify-install/)

### Step 4: Create a Python environment for CISC235 course using Ananconda

In Ananconda Navigator (the UI of Ananconda), you should be able to see all created environments in your machine. 

Follow the below official document, you can create your first Python environment for hosting all CISC235 work. I suggest you pick a Python version higher than 3.5.

[Create Python environment in Ananconda guidline page](https://docs.anaconda.com/navigator/tutorials/create-python35-environment/)

For instance, I just created a new Python environment named "cisc235w23" : 



### Step 5: Putting Ananconda and VS Code together
Like many other IDEs, VS code support global and virutal Python environment. 
By default, the Python extension looks for and uses the first Python interpreter it finds in the system path. 
To select a specific environment, you can use the Python: Select Interpreter command from the Command Palette (⇧⌘P).

Or simply click the version number, i.e., 3.x in the below example, at the right bottom of the VS code interface. 
You can observe all the created Python environments previously using Aanconda, including "cisc235w23".

<img width="1048" alt="image" src="https://user-images.githubusercontent.com/122241609/211232700-ad6c4038-a998-4ab2-a9f8-168067ec3036.png">

The selection of Python interpreter appears once you have created your Python project and Python file, i.e., test.py in the above example.


### Step 6: A Hello World test

Write a simple printing function and execute is using the selected Python environment, you would be able to see the execution result in the Terminal tab.

<img width="1052" alt="image" src="https://user-images.githubusercontent.com/122241609/211232900-67e9a5a9-5749-4e72-985f-166e3d576da5.png">

### Step 7: Debug in VS code

I highly recommend you read the following official document that introduces the debugging function of VS code. 

[Debugging in VS code guideline page](https://code.visualstudio.com/Docs/editor/debugging)

To help you better use VS code for this course, you should understand the following concepts (they are listed in the above document):
- What is a breaking point, how to add it in VS code.
- What are the differences between debug actions, including Step Over, Continue/Pause, Step Into, Step Out, Restart, Stop.
- Where is the debug console panel and how to access to status of variables during debug process.
- How to start a debug process after adding breaking point

For instance, let's see what's the status of the program when key "4" is hitted while running the following online sample program:

```Python

# Function calling
def dictionary():
    # Declare hash function
    key_value = {}
 
# Initializing value
    key_value[2] = 56
    key_value[1] = 2
    key_value[5] = 12
    key_value[4] = 24
    key_value[6] = 18
    key_value[3] = 323
 
    print("Task 1:-\n")
 
    print("key_value", key_value)
 
    # iterkeys() returns an iterator over the
    # dictionary’s keys.
    for i in sorted(key_value.keys()):
        print(i, end=" ")
 
 
def main():
    # function calling
    dictionary()
 
 
# Main function calling
if __name__ == "__main__":
    main()
```

First, I added two breaking points at line 21 and line 31:

<img width="411" alt="image" src="https://user-images.githubusercontent.com/122241609/211234656-2bc3a8ab-a38f-43fd-9a80-549f734014de.png">

Next, I click the "Debug Python File" on the right top corner:

<img width="205" alt="image" src="https://user-images.githubusercontent.com/122241609/211233634-c8f72acb-a1ce-4391-bb7c-29c9d8aaeff7.png">

You will observe that the program starts and stopped at the first breaking point, i.e., line 31. The debug panel is automatically pulled out. Information about local and global variables are shown on the left top pannel.

<img width="1206" alt="image" src="https://user-images.githubusercontent.com/122241609/211234606-ca385d70-d3e1-40db-bd30-3338f9fe8f2f.png">

I then click "Continue"

<img width="298" alt="image" src="https://user-images.githubusercontent.com/122241609/211233818-202da4c5-7c27-445f-9aac-66757764cf3b.png">

The program will run until it hits line 21. This means, we have run the program before entering line 21. You can observe the value of i equals 1 at this moment in the variables panel:

<img width="731" alt="image" src="https://user-images.githubusercontent.com/122241609/211234231-f5269457-1713-48f0-a67d-7d69039b653c.png">

You can also observe the call stack (functions being executed before entering the breaking point line). If you click "main", a green line will highlight the line before entering the dictionairy function.

<img width="625" alt="image" src="https://user-images.githubusercontent.com/122241609/211234212-92e78b2a-22ff-48ca-b018-188b8f777ce1.png">

If you click "Continue" (to debug), you will see the line 21 highlighted again, and the variable i now equals to 2:

<img width="608" alt="image" src="https://user-images.githubusercontent.com/122241609/211234307-5ee77d3d-3d56-4c15-8b94-346c27bd7707.png">

Continue, until you see the variable i equals to 4

<img width="619" alt="image" src="https://user-images.githubusercontent.com/122241609/211234354-fd511874-435a-49fc-a72d-75ed1878df65.png">

You can now stop debugging program, modify as you want and play with the debugging mode in VS code.

<img width="269" alt="image" src="https://user-images.githubusercontent.com/122241609/211234451-0eac33a6-2220-48b0-9856-efcf9a726ed7.png">

### Congralutations! You have completed the first tutorial. Let me or TA know if you have any problem in the procee.


