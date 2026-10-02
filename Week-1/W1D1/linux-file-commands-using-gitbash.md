# Cumulative for the  linux file commands using gitbash
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites and Learning Objectives for the Linux File Commands Using GitBash topic

## Prerequisites

- General experience using a computer.

## Learning Objectives

After completing this module, associates should be able to:

- List common file handling commands in UNIX/Linux.
- Perform basic file manipulation functions using an online Linux emulator.
</details>
<details><summary>Description</summary>

# Description for the Linux File Commands Using GitBash topic

Below are some useful UNIX/Linux commands for handling files using GitBash. Always remember that UNIX/Linux commands are case-sensitive.

- ls
  - This command lists directory contents. 
  - It lists files and directories. 
  - Some versions may support color-coding. The names in blue represent the names of directories.

```bash
$ ls -l | more
```
  - This command helps paginate the output so you can view page by page. Otherwise the listing scrolls down rapidly. You can always use ctrl + c to return to the command line.
  - Note: more is not supported in GitBash for Windows.

```bash
$ ls –I 
```
  - This command shows more details of the contents in the directory. It lists the following:
    - Permissions associated with the fileThe owner of the file
    - The group associated with the file
    - The size of the file
    - The timestamp
    - The name of the file
  

- cd
  - This changes the current directory. Note that it uses a forward slash. 

```bash
$ cd /var/log
```


- pwd
  - One way to identify the directory you are working in is the pwd command. It displays the current working directory path and is useful when directory changes are made frequently.

```bash
$ pwd
```

- mkdir
  - The mkdir command makes a directory. The command is written as follows: mkdir [directory name]

```bash
$ mkdir myproject
```

- cat
  - The cat command can be used to create, view, and concatenate files. The example below creates a new file called "newfilename".

```bash
$ cat > newfilename
```

When you type in the command below, the command prompt will disappear. This is because of the ">" (greater than symbol) which is known as "redirection." At this point the keyboard output is being re-directed into the file "newfilename". Type the text that you would like to place in the file. When you are done entering text, press the Control and D keys on your computer keyboard at the same time to save the file and return to the command prompt.

- Another way to create a file using cat:
  - The cat example below will copy the file "sourcefilename" into the file "destinationfilename". 

```bash
$ cat sourcefilename > destinationfilename
```

- touch
  - The touch command creates an empty file for editing later. The command below creates an empty file called "filename". From there you can use a terminal-based editor like "vi" to edit the file.

```bash
$ touch filename
```

- echo
  - The echo command prints the strings that are passed as arguments to the standard output, which can be redirected to a file. To create a new file run the echo command followed by the text you want to print and use the redirection operator > (as explained with `cat` above) to write the output to the file you want to create. 
  - The command below will create the file "file.txt" containing the text "Some line".

```bash
$ echo "Some line" > file1.txt
```

- grep
  - The grep command can be used to search files and directories (and subdirectories) for a string. The example below searches the file "filename" for the string "Aaron".

```bash
$ grep Aaron filename
```

- diff
  - The diffcommand compares two files line by line to find differences. The output will be the lines that are different.

```bash
$ diff file1.txt file2.txt
```
</details>
<details><summary>Real World Application</summary>

# Real World Application for the Linux File Commands Using GitBash topic

### Why use the command line?

GitBash, which we use for code repositories, uses UNIX/Linux based commands in a terminal (text-based) environment. Therefore, it is important to know why using the command line is crucial:

- When Unix Was Developed, There Was No GUI
  - While Linux is not Unix, as it has no code from the system, its behavior is based on it, including its use of the command line. When Unix was developed at Bell Labs in the late '60s and early '70s, there was no such thing as a graphical user interface.
  - Command-line interfaces were natural for this type of terminal. The use of text terminals was also a major reason why Unix developers preferred short command names, as they were faster to type.
-  Programming Tools Use the Command Line
   -  Programmers have been the staunchest advocates of Linux because it has so many tools for them to get their work done: interpreters, compilers, and debuggers. And all of these tools run on the command line.
   -  While you can call all of these from a graphical IDE, it's just a front end to a command line somewhere.
-  The Command Line Is Fast
   -  A lot of Linux users love to claim that the Linux command line is faster than using a GUI. 
   -  Command-line programs start faster than graphical ones because there's less overhead.
-  The Command Line Works Everywhere, Including on Servers
   -  One big reason that the command line has survived on Linux systems is that it works just about everywhere. 
   -  If the X-windows system didn't like your graphics card, a problem that was also more common on early Linux systems, you'll find yourself dumped at the console. 
   -  This means you can fall back on the command line when you need to.
-  Command-Line Programs Can Be Scripted
   -  One big advantage of command-line programs over graphical ones is that programmers can automate them.
   -  For example, if you wanted to copy all your text files to a directory, you'd use this line:

```bash
cp *.txt /example
```
   - A script could be written if there were a need for repeated file copying. 
</details>
<details><summary>Implementation</summary> 

# Implementation for the Linux File Commands Using GitBash

### Online Linux Emulators

To get hands-on experience using Linux commands, select one of the online Linux emulators located here:

[JSLinux](https://bellard.org/jslinux/)

Specifically, you should attempt the following commands (with appropriate parameters) in any order:

- ls
- cd
- pwd
- mkdir
- cat
- grep

Note: The emulators do support file/directory creation and deletion, so feel free to create/delete files as appropriate!
</details>
<details><summary>Summary</summary> 

# Summary for the Linux File Commands Using GitBash topic

Below are some useful UNIX/Linux commands for handling files using GitBash:
- ls
- cd
- grep
- pwd
- mkdir
- diff
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
