UNIX is an operating system which was first developed in the 1960s and has been under constant development ever since. There are many types of UNIX with the most popular versions being macOSX and GNU/Linux.

# Goals
1. Understand how to use the command line
2. Learn basic commands:
    * `cd`
    * `ls`
    * `touch`
    * `mkdir`
    * `rm`

# Guide

## Getting Started
In order to get started with UNIX first you should make sure that you have access to a UNIX shell. If you have macOS, or Linux you can skip this step and move on to the next part. However if you have windows you will need to get access to a shell. In order to get a shell on windows there are two methods. Install a virtual machine, or install [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?rtc=1&activetab=pivot:overviewtab).

### Setting up a Virtual Machine
1. Install [Virtual Box](https://www.virtualbox.org/wiki/Downloads) onto your computer.
2. Download [Ubuntu](https://ubuntu.com/download/desktop) 
3. Follow Virtual Box's [setup instructions](https://www.virtualbox.org/manual/ch01.html#gui-createvm).

## Navigating Directories
Now that you should have access to a linux shell we can start walking through how to navigate directories using the command line. The first command to learn is `ls`. `ls` lists the files and directories in the current directory. This is useful for finding out where you are in a directory as well as planning your movement through the directory.

While`ls` allows you to see all the files in your current directory, you are unable to change your current directory with `ls`. To change your current directory the command `cd` must be used. For example if you wanted to change your current directory to the *Code* directory which is withing the *Documents* directory you would use the command:

```
cd Documents/Code
```

By using these two commands you are able to fully navigate your filesystem without any outside help.

## Modifying Files & Directories 
Being able to navigate your files is important but it is not necesarilly helpful if you are unable to modify the files. By using the command `touch` you are able to create new files of anytype easily. For example if you wanted to create a python file called *wolf_pack.py* you would enter the following command into your shell:

```
touch wolf_pack.py
```

In order to then edit that file you could use a number of different programs but in this case I will demonstrate two. The first one would be `open` which would open the chosen file in any application you choose. For example to open *wolf_pack.py* in xcode you would use the command:

```
open wolf_pack.py -a xcode
```

Another way to edit the file would be to use a program called `vim`. `vim` is a text editor that is standarad on almost every computer system and runs in the terminal. It is very difficult to learn however if the time is put into it it is incredibly customizable. To learn more about vim you can read this article.

Now that we know how to create and modify files you should learn how to delete files. To delete files the command `rm` would be used. For example to delete *wolf_pack.py* you would use the command:

```
rm wolf_pack.py
```

Besides these basic file manipulation commands there are a few other important ones, namely `mv` and `cp`. `mv` allows you to move a file from one directory to another and also allows you to rename files if they stay in the same directory such as renaming *wolf_pack.py* to *dog_pack.py* using the command:

```
mv wolf_pack.py dog_pack.py
```

The `cp` command allows you to copy a file to another path such as copying *dog_pack.py* to the *packs* directory using the command:

```
cp dog_pack.py packs/dog_pack.py
```

Now that most of the file manipulation commands are known we can start learning how to create and manipulate directories as they share a lot of commands. One command that they do not share is regarding the creation of a directory, `mkdir`. `mkdir` creates a directory. An example of this is shown below by creating a directory name *groups*.

```
mkdir groups
````

Now the commands to manipulate a directory overlap with the file commands and so they are the same. The only command that is slightly different is that instead of just `rm` the command `rm -r` is used as the `-r` flag signifies that it will delete recursivley.

# Exercise

# Resources
* http://www.ee.surrey.ac.uk/Teaching/Unix/unixintro.html
* https://en.wikipedia.org/wiki/List_of_Unix_commands
