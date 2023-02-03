# Preparing a Windows Computer for Development in C and Python

This will be the hardest part of the programming course. Typically students struggle more with setup than any of the actual programming content. Once you've managed to get your computer prepared to write code in both C and Python, the rest of the course should be a walk in the park.

## Installing Cygwin to compile C

Different Operating Systems use different programs to compile code (we'll explain what compiling is in a future lecture), in order to maintain a consistent environment across operating systems for this course we are going to use one called **gcc**. Unfortunately for windows users, we cannot directly use this compiler. In order to do so we will need to download a program called **Cygwin** that will allow Windows to act like Linux inside of VS Code. Setup of Cygwin with Windows and VS Code is the easiest place to run into problems, so take your time to get this right before moving forward.

### Downloading and Installing Cygwin

Go to the following address in your preferred internet browser:

https://www.cygwin.com/

Scroll down to the section entitled "Installing Cygwin" and click on the blue text that says "setup-x86_64.exe". The download will begin just like it did with VS Code.

- The "x86_64" lets us know that this application is intended for computers using "x86" processors (intel or AMD) that support 64 bit operations, which all PCs in the last decade should. You don't need to worry about this know, but we will talk about what this means in our "Hardware Model" video.

Open the file when it finishes downloading.

- Again, you may get a popup from windows first asking if you want to allow the program to make changes to your computer. Click "Yes".

On the first page, press "Next".

Check the bubble marked "Install from Internet".

Leave the root directory as **C:\cygwin64**, or change it to **C:\cygwin64** if it is not already. Leave Install For checked with **All Users (RECOMMENDED)** to avoid any issues.

In the local package directory it should read **C:\Users\NAME\Downloads**, with whatever your username is instead of "NAME". Click Next.

Select "Use System Proxy Settings" on the next screen and then click Next.

On the next screen you can select whatever mirror you like, but the top one or whichever is already selected should work fine. Click Next.

- This download may take awhile.

The window should then change to a larger window titled "Cygwin Setup - Select Packages". At the top next to where it says "View", switch the dropdown menu to "Category".

Click the little "+" button next to "All" under "Package"

Click the "+" to expand "Devel".

Scroll down until you find **gcc-core**, **gcc-g++**, and **gdb**. Under the column labeled "New" double click where it says "Skip" next to these entries. 

- If double clicking doesn't work, click the little arrow next to Skip for each of these and select the number at the bottom of the dropdown. At the time of writing this it is "11.3.0-1" for gcc and "11.2-1" for gdb.

- **gcc-core** is the compiler we will use for C.
- **gcc-g++** is the compiler for C++ code that we will be writing in future courses.
- **gdb** is the debugger, which will allow us to figure out what is wrong with our code when we make mistakes.

Click Next. 

A page will pop up with all of the installations that are about to happen, you should see "gcc-core", "gcc-g++" and "gdb" in the list. Click Next.

- If you don't see these in the list, click back and make sure they have a number next to them in the previous list and not "Skip".

- This next download may also take quite a bit of time.

## Installing Python

Go to the following website in your preferred browser:

https://www.python.org/downloads/

Click on the yellow button that says "Download Python 3.11.1", if it has a new number that will be fine. However, make sure the number starts with a 3. Python 3 is different than python 2 and the code won't look exactly the same.

Conisder having a look at this page if you run into any issues later when we try to get Python working in VS Code:

https://code.visualstudio.com/docs/python/python-tutorial

## Installing Visual Studio Code

### What is Visual Studio Code

We will be using Visual Studio Code as our development environment in this and all future courses in the series. Be careful not to confuse **Visual Studio Code** with **Visual Studio**, these are two *different applications*. **Visual Studio** (without the **Code**) is an Integrated Development Environment (IDE), which means all of the tools needed to develop applications, including large scale ones are included (or *integrated*) into the application already. This is overkill for our purposes and obscures parts of the development process we would like to become familiar with.

**Visual Studio Code** (or VS Code) on the other hand is a "Text Editor". This just means that it is an application that can edit any general text, including this file! If you're familiar with Notepad, an application that comes with Windows by default, VS Code is like a really powerful version of Notepad. VS code will give us a file explorer, a text editor, a terminal, and the ability to add even more features with what it calls *extensions*. Using all of this together VS Code almost becomes a complete IDE.

### Downloading and Installing VS Code

Go to this website on whichever browser you prefer (I recommend firefox):

https://code.visualstudio.com/download

Click on the large blue button labeled "Windows". 

- The download should start automatically and your browser should show its progress. The page will also open the intro page to visual studio code, if you would like to become familiar with the software in greater depth, feel free to read through the links on this page, but it won't be necessary for our purposes.

Open the downloaded file. 

- If it is not visible in your internet broswer, open file explorer (the little folder icon at the bottom of your computer) and click on downloads on the left.

A small window will popup with a license agreement. Check **I accept the agreement** in order to move forward, then click next.

- Windows may also warn you that an application is trying to make changes to your computer, if this happens click "Yes".

A list of installation options will popup. I recommend selecting all options.

Click Next.

The final screen will display some information regarding the installation. Click **install** and the installation process will begin.

When the installation process has finished, reboot your computer.

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

This file will likely be filled with some text, for now we can ignore most of it.

Look for a section starting with the text:

    "terminal.integrated.profiles.windows": {

    }
This should be one tab in. If you don't see this anywhere, go ahead and add it now. Notice that it has curly braces **{}** enclosing a section. There will likely already be some terminals there, specifically "Command Prompt" and "Powershell". Between each there is a comma, so add a comma after the last one in the list if some already exist, then paste this in:

    "Cygwin": {
            "path": "C:\\cygwin64\\bin\\bash.exe",
            "args": [
                "--login",
                "-i"
            ],
        }

This tells the settings that we want a new terminal option called "Cygwin", but you can name it whatever you would like. The path tells it where the program to run this terminal can be found, if you followed the cygwin download correctly, it should be at this location, but notice the double back slashes and make sure your path has those.

The "args" tells the terminal what to do when it opens. By giving it these it will login automatically and be ready to begin typing.

Outside of the block enclosed by "terminal.integrated.profiles.windows" add the block:

    "terminal.integrated.env.windows": {
        "CHERE_INVOKING": "1"
    }

Make sure you add a comma to the last block before adding another.

Next, add the following block to the file:

    "launch": {
        "configurations": [
            {
                "name": "Debug (Cygwin)",
                "type": "cppdbg",
                "request": "launch",
                "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
                "args": [],
                "stopAtEntry": false,
                "cwd": "${workspaceFolder}",
                "externalConsole": true,
                "MIMode": "gdb",
                "miDebuggerPath": "C:\\cygwin64\\bin\\gdb.exe",
            }
        ],
        "compounds": []
    }

You don't need to worry about the details of this block right now, but if your curious:

- "name" is just so we know which debugger we are using
- "type": "cppdbg" tells VS Code what debugger this actually is
- "request": "launch" means we are going to launch the program with the debugger when we press play on the debug tab
- "program": "program": "${fileDirname}\\${fileBasenameNoExtension}" tells the debugger which file to actually debug, we'll see how to use this later
- "args": [] tells the debugger not to pass any command line arguments to the program
- "stopAtEntry": false, lets the debugger know not to immediately pause the program when it launches, you can set this to true if you'd prefer
- "cwd": "${workspaceFolder}" tells the debugger what the current working directory should be when launching
- "externalConsole": true, makes the debugger launch a new console rather than using the Cygwin one, this is to avoid issues with Cygwin integration
- "MIMode": "gdb", gives the actually debugger we are using (**gdb**)
- "miDebuggerPath": "C:\\cygwin64\\bin\\gdb.exe", lets VS Code know where to find the **gdb** debugger we want it to actually launch. Make sure this path actually points to a real file. If you followed the Cygwin install properly it *should* be this.

With all of these terminal changes, you should now have the three blocks together that look like this:

    ... Other settings ...

    "terminal.integrated.profiles.windows": {
        "Cygwin": {
            "path": "C:\\cygwin64\\bin\\bash.exe",
            "args": [
                "--login",
                "-i"
            ],
        }
    },
    "terminal.integrated.env.windows": {
        "CHERE_INVOKING": "1"
    },
    "launch": {
        "configurations": [
            {
                "name": "Debug (Cygwin)",
                "type": "cppdbg",
                "request": "launch",
                "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
                "args": [],
                "stopAtEntry": false,
                "cwd": "${workspaceFolder}",
                "externalConsole": true,
                "MIMode": "gdb",
                "miDebuggerPath": "C:\\cygwin64\\bin\\gdb.exe",
            }
        ],
        "compounds": []
    }

*Notice the commas between each block. DON'T FORGET THESE!*

You can now close the settings.json file by clicking the X next to it at the top.

This may also be a good time to close VS Code and reboot your computer one last time so all the changes can take effect.

## Testing Hello World

### Testing C

Open File Explorer on your computer and navigate to your documents folder, or wherever you would like to keep the files for these courses. 

Right click and select "New > Folder" and give it a name like "Programming".

Close file explorer.

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

Next click on the terminal tab at the very top of VS Code and select "New Terminal". A new section at the bottom of VS Code will open where we can type. At the top right of *this new section* there will be a name, either powershell, command prompt, or Cygwin. If it is NOT Cygwin, click the down symbol next to whatever name is there and select Cygwin from the options that appear.

The terminal will refresh and we will see the name "bash" instead. There will still be the other terminal name as well, leave it there as we may use that terminal for python.

The Cygwin terminal will have green and yellow coloring, if you see this congratulations, cygwin was properly connected.

Type **ls** (short for list) and then press enter. A list of all files and folders will appear. Hopefully you will see:

    C Python

Next type **cd C** and then press enter. It will look like nothing happend except the yellow line added a "/C", but if we use the **ls** command again we should now see:

    hello.c

We are now in the same folder as the C file we created. Type 

    gcc hello.c -o hello.exe -Wall

and then press enter. This will build a program out of the code we wrote. After a second, we should see **hello.exe** appear in our folder on the lefthand sidebar. If we run the **ls** command we should now see:

    hello.c hello.exe

Don't worry about what we did quite yet, we'll cover that in the next video.
Next, type:

    ./hello.exe

and press enter. This will actually launch the program we built when we used **gcc**.

You should see

    Hello world!

At this point we are up and running! Before we test Python however, we want to make sure we can debug our code as well. In the C file, next to the line that says **printf("Hello world!);** hover your mouse to the left of the number (it should be line 4). A faint red dot will appear, if you click on it will be added there and will stay when you move your mouse away. This adds a place in our code we want it to pause at when we run the debugger.

Go back to the terminal at the bottom and enter the command:

    rm hello.exe

This will remove/delete the hello.exe file. You can also delete it on the lefthand sidebar.

Next, type:

    gcc -g hello.c -o hello.exe -Wall

This will build our program, but this time with preparations made to debug it. On the lefthand sidebar look for the symbol with a play button and a bug on top of it and select it. The panel will switch to sections with **VARIABLES**, **WATCH**, and **CALL STACK**. At the very top there should be a green play button that says **Debug (Cygwin)**. Click the green play button.

A new console will launch that is completely blank. VS Code will highlight the line of code with the red dot and a menu will appear at the top with a few arrows, a play symbol, and a red block. For now, click the play symbol to finish running the program.

Congrats! Everything you need to write, compile and debug C code is now ready!

### Testing Python

Just like we created a .c file in our C folder, create a file named "hello.py" in our Python folder using the files tab on the left. 

Enter the following code into the python file:

    print("Hello world!)

Up at the top right of the window you should see a play button, if you hover it, it should read "Run Python File". Click this button.
- If nothing happens, close VS Code and reopen it. You should only need to do this once, but when switching between languages VS Code can get confused. 

You'll notice a new terminal gets added to the list below called Python, this is where all of your python input and output will appear throughout this course.

In the python file, to the left of the number 1 showing the line number click on the red dot that appears to add it. 

Click on the little down arrow next to the play button in the python file, and click on "Debug Python File". Just like with our C program, VS Code will then begin running the program and pause at the line of code we have. We have the same options for how we can move the debugger forward. Again click the continue button to simply let the program run till it ends.

## Final Notes

We can see how much easier it was to write the python file, 1 line vs 3-6 in the C file. Running the python program was also much easier, as the VS Code tools allow us to just click a button. This will become a common theme throughout the course. However, what we will notice is that with C we are being very precise about everything we do and will be deeply connected to what the computer is actually doing. Python makes things easy for us, but sacrifices our actual understanding of what it that is happening. By learning the together we can both come to understand how the computer operates as well as learn how to code powerful programs with ease.