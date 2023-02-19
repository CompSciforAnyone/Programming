# Preparing a Windows Computer for Development in C and Python

This will be the hardest part of the programming course. Typically students struggle more with setup than any of the actual programming content. Once you've managed to get your computer prepared to write code in both C and Python, the rest of the course should be a walk in the park. I will be showing the commands for Ubuntu 22.04 LTS, but any version of Linux should work with their specific package managers. Mac instructions will be provided in this document as well.

## Installing gcc on Linux and Mac

Different Operating Systems use different programs to compile code (we'll explain what compiling is in a future lecture), in order to maintain a consistent environment across operating systems for this course we are going to use one called **gcc**. Fortunately, Linux and Mac often ship with gcc already installed. 

First we need to open a terminal. Search for "terminal" in your installed apps, it should look like a black rectangle. A terminal will be our primary means of interacting with the computer throughout this course.

### Linux

Before attempting to install gcc, we can check if it is already installed by typing:

    gcc --version

and then pressing enter to run the command. If you get a message that looks like this:

    gcc (GCC) 11.3.0

then gcc is already installed. If instead it gives you an error, we can run this command to install it:

    sudo apt update
    sudo apt install build-essential

The first command ensures that we will get the most up to date version of the software we want to install.
The second command installs the tools we will need to build C programs.

You may need to enter **y** during the install.

Once the install finishes you can use the `gcc --version` command again to ensure it is working.

### Mac

In the terminal type the command:

    gcc

then prese enter. If the terminal responds:

    clang: error: no input files

then gcc is already installed and you are ready to go. Otherwise, it may prompt you with:

    The gcc command requires the command line developer tools. Would you like to install them now? 

In this case, click install. Once it finishes try running `gcc` again to ensure you get the `no input files` error.


## Installing Python

### Linux

In the terminal type:

    python3 --version

This will check for a python 3 installation, just typing python will search for a python 2 installation which will not be compatible with this course.
If you receive an error message that it is not installed, type the following commands:

    sudo apt update
    sudo apt install python3

Once again, the first line updates your computers listings of software to install, ensuring we get the most up to date software.
The second command will install python, you may need to enter **y** during the install.

### Mac

In the terminal type:

    python3 --version

You should get a version number in response, as the command line developer tools we installed for gcc will have also installed python3.
If you get the prompt mentioning command line developer tools, click install and check the version again.

If you are still unable to get a version for python, go the following link:

https://www.python.org/downloads/

and click on the large yellow button that says download. 

Once it has finished downloading, double click on the file and click next on each of the dialog boxes until the installation completes.

Check the version once more to ensure it has correctly installed.

## Installing Visual Studio Code

### What is Visual Studio Code

We will be using Visual Studio Code as our development environment in this and all future courses in the series. Be careful not to confuse **Visual Studio Code** with **Visual Studio**, these are two *different applications*. **Visual Studio** (without the **Code**) is an Integrated Development Environment (IDE), which means all of the tools needed to develop applications, including large scale ones are included (or *integrated*) into the application already. This is overkill for our purposes and obscures parts of the development process we would like to become familiar with.

**Visual Studio Code** (or VS Code) on the other hand is a "Text Editor". This just means that it is an application that can edit any general text, including this file! VS code will give us a file explorer, a text editor, a terminal, and the ability to add even more features with what it calls *extensions*. Using all of this together VS Code almost becomes a complete IDE, but is still a much smaller application than **Visual Studio**.

### Downloading and Installing VS Code

### Linux (Snap)

I recommend installing VS Code through the snap store on Linux if you have it installed. 

Open the snap store by typing "software" into your applications search bar.

Search for "Visual Studio Code" or "vscode".

Click install.

### Mac

Go to this website on whichever browser you prefer (I recommend firefox):

https://code.visualstudio.com/download

Click on the large blue button labeled "Mac". 

- The download should start automatically and your browser should show its progress. The page will also open the intro page to visual studio code, if you would like to become familiar with the software in greater depth, feel free to read through the links on this page, but it won't be necessary for our purposes.

Open the downloaded file. 

- If it is not visible in your internet broswer, open finder and click on downloads on the left.

A small window will popup with a license agreement. Check **I accept the agreement** in order to move forward, then click next.

A list of installation options will popup. I recommend selecting all options.

Click Next.

The final screen will display some information regarding the installation. Click **install** and the installation process will begin.

## Configuring VS Code

We now have all the tools we need to begin development, but first we will need to make sure VS Code is aware of how to interact with Python and C.

### Extensions

First, click on the tab on the left for extensions. It looks like 4 sqaures, with the top right one floating away from the other 3.

In the search bar type "C/C++". The top option should say "C/C++" and will have "Microsoft" in small text below it to let you know who created this extension. Click on the small blue square labeld "Install".

Next, search "Python". This one will also be from Microsoft. Click install on this one as well.

Finally, search for "File Template". Install the extension by "ralfz". We will use this to auto-generate starter code for our files.

### Preferences

Go to the top bar and click on "File > Preferences > Settings".

In the search bar, type "Auto Save". Click on the dropdown and set it to afterDelay. This will ensure we don't lose our code if something crashes, as well as having issues not saving files before compiling.

Search "Detect Indentation", and make sure the box is selected. This will ensure different files will automatically use the correct indentation format. This will avoid conflicts when dealing with Python.

Search "Insert Spaces" and check this box, this will keep our tabs to a default size unless otherwise overrided by the file we open.

Search "Tab Size" and set the value to 4.

This will match your environment with the one I will be using, but ensures that any other file you open doesn't have issues due to different tab formats.

### Terminal and Debugger Settings

While still on the settings page, look for the icon of a page with an arrow in the top right corner. If you hover it, it should say "Open Settings (JSON)". Click this icon.

This file will likely be filled with some text, for now we can ignore most of it. Add the following block starting with "launch" to the file, make sure it is within the curly braces that contain all of the other text. Also, make sure to add a comma before this block.

    ... other settings ... {
        ... some other settings options ...
    },

    "launch": {
        "version": "0.2.0",
        "configurations": [
            {
                "name": "(lldb) debug active file",
                "type": "lldb",
                "request": "launch",
                "program": "${fileDirname}\\${fileBasenameNoExtension}.out",
                "args": [],
                "cwd": "${workspaceFolder}",
                "terminal": "integrated"
            }
        ]
    }

You can now close the settings.json file by clicking the X next to it at the top.

This may also be a good time to close VS Code and reboot your computer one last time so all the changes can take effect.

## Testing Hello World

### Testing C

Open Files (Linux)/Finder (Mac) on your computer and navigate to your documents folder, or wherever you would like to keep the files for these courses. 

Right click and select "New > Folder" and give it a name like "Programming".

Close the file explorer.

Open VS Code.

At the top menu select "File > Open Folder", and find the folder you just created. VS Code will close and reopen very quickly.

Open the files tab on the lefthand sidebar, it looks like to pages on top of each other with a bent corner. You should see the name of the folder you created at the top of the tab.

This is where we will create all of our new files and the folders we want to keep them organized in. I recommend staying in this folder for the remainder of the course.

Hovering over the folder name we will see a few icons pop up. Select the one that looks like a folder with a + symbol, and name the new folder "C". 

Click on the main folder and do the same thing to create a folder called "Python".

We should now have the following folder structure:

    Programming
        > C
        > Python

Click on C, and then press the new file button. Give the file the name "hello.c". All of our c files will end in ".c" to let the computer know what type they are. Copy and paste this code into the file in the main portion of VS Code, (Next to the number 1 that lets us know how many lines of code there are).

    #include <stdio.h>

    int main() {
        printf("Hello world!");
    }

Next click on the terminal tab at the very top of VS Code and select "New Terminal". A new section at the bottom of VS Code will open where we can type. 

Type **ls** (short for list) and then press enter. A list of all files and folders will appear. Hopefully you will see:

    C Python

Next type **cd C** and then press enter. It will look like nothing happend except the yellow line added a "/C", but if we use the **ls** command again we should now see:

    hello.c

We are now in the same folder as the C file we created. Type 

    gcc hello.c -o hello.out -Wall

and then press enter. This will build a program out of the code we wrote. After a second, we should see **hello.exe** appear in our folder on the lefthand sidebar. If we run the **ls** command we should now see:

    hello.c hello.out

Don't worry about what we did quite yet, we'll cover that in the next video.
Next, type:

    ./hello.out

and press enter. This will actually launch the program we built when we used **gcc**.

You should see

    Hello world!

At this point we are up and running! Before we test Python however, we want to make sure we can debug our code as well. In the C file, next to the line that says **printf("Hello world!);** hover your mouse to the left of the number (it should be line 4). A faint red dot will appear, if you click on it will be added there and will stay when you move your mouse away. This adds a place in our code we want it to pause at when we run the debugger.

Go back to the terminal at the bottom and enter the command:

    rm hello.out

This will remove/delete the hello.out file. You can also delete it on the lefthand sidebar.

Next, type:

    gcc -g hello.c -o hello.out -Wall

This will build our program, but this time with preparations made to debug it. On the lefthand sidebar look for the symbol with a play button and a bug on top of it and select it. The panel will switch to sections with **VARIABLES**, **WATCH**, and **CALL STACK**. At the very top there should be a green play button that says **Debug (Cygwin)**. Click the green play button.

A new console will launch that is completely blank. VS Code will highlight the line of code with the red dot and a menu will appear at the top with a few arrows, a play symbol, and a red block. For now, click the play symbol to finish running the program.

Congrats! Everything you need to write, compile and debug C code is now ready!

### Testing Python

Just like we created a .c file in our C folder, create a file named "hello.py" in our Python folder using the files tab on the left. 

Enter the following code into the python file:

    print("Hello world!")

Open the debug panel on the left sidebar once more. Next to the green arrow, select the dropdown button and find the entry titled "Python" and select it.

A popup will appear with options for your Python debugger, likely with only one option. Select the option titled "Python File:".

Now click the green arrow to run the program. You'll notice a new terminal gets added to the list below called Python, this is where all of your python input and output will appear throughout this course.

In the python file, to the left of the number 1 showing the line number click on the red dot that appears to add it. 

Click the green arrow to run the program just as we did before, this time it should stop at the line like the debugger did with the C file. We have the same options for how we can move the debugger forward. Again click the continue button to simply let the program run till it ends.

## Final Notes

We can see how much easier it was to write the python file, 1 line vs 3-6 in the C file. Running the python program was also much easier, as the VS Code tools allow us to just click a button. This will become a common theme throughout the course. However, what we will notice is that with C we are being very precise about everything we do and will be deeply connected to what the computer is actually doing. Python makes things easy for us, but sacrifices our actual understanding of what it that is happening. By learning the together we can both come to understand how the computer operates as well as learn how to code powerful programs with ease.