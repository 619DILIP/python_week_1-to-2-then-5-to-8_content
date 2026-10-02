# Cumulative for the  moving and deleting files using gitbash
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites and Learning Objectives for the Moving and Deleting Files Using GitBash topic

## Prerequisites

- General experience using a computer.

## Learning Objectives

After completing this module, associates should be able to:

- List commands for moving and deleting files in UNIX/Linux.
- Perform basic file moving and deleting functions using an online Linux emulator.
</details>
<details><summary>Description</summary>

# Description for the Moving and Deleting Files Using GitBash topic

Below are some useful UNIX/Linux commands for moving and deleting files using GitBash. Always remember that UNIX/Linux commands are case-sensitive.

### mv

The mv command moves a file or renames it. Some examples; inline comments denoted with //

```bash
$ mv file1 directory1 // moves 'file1' to 'directory1'
```

```bash
$ mv file1 file2 file3 dir1 // moves 'file1', 'file2', and 'file3' to 'dir1'
```

```bash
$ mv file1 file2 // renames 'file1' with the new name 'file2'. This can also be used to rename directories.
```

```bash
$ mv -i file1 directory1 // just as above, this will move 'file1' into 'directory1' but the -i flag will prompt the operator should the command result in overwriting an existing file.
```

```bash
$ mv -n file1 directory1 // similar to the above, however the -n flag will not move 'file1' to 'directory1' if it causes an overwrite.
```

```bash
$ mv -u file1 directory1 // The -u flag will only move 'file1' to 'directory1' if the source file is newer than the destination file.
```

```bash
$ mv -b file1 directory1 // The -b flag will create a backup of any existing destination file overwritten by 'file1'.
```

### cp 
The cp command copies a file. Some examples; inline comments denoted with //

```bash
$ cp second.txt third.txt // copies 'second.txt' into a file 'third.txt'
```

```bash
$ cp -i second.txt third.txt // -i stands for Interactive copying. With this option system first warns the user before overwriting the destination file.
```

```bash
$ cp -b second.txt third.txt // -b will create a backup of the destination file in the same folder
```

```bash
$ cp -f second.txt third.txt // -f stands for force; if the system cannot open the destination file then the destination file is deleted first before the copying proceeds.
```

```bash
$ cp -r directory1 directory2 // -r is for Recursive copying which is used for copying the contents of 'directory1', including all subdirectories, into 'directory2'.
```

```bash
$ cp -p second.txt third.txt // -p stands for preserve. The command preserves some characteristics of 'second.txt' in the destination file 'third.txt' including times of last modification and access, ownership, and file permissions.
```

## rm
The rm command deletes files/directories. Some examples; inline comments denoted with //

```bash
$ rm file1 // deletes 'file1' in the current working directory.
```

```bash
$ rm -i file1 // -i stands for interactive; this prompts the operator before deleting each file.
```

```bash
$ rm -f file1 // -f forces deletion if a file is write protected. It will not remove a write-protected directory.
```

```bash
$ rm -r directory1 // -r (recursive) will delete all files in 'directory1' and all subdirectories of 'directory1' and their contents.
```
</details>
<details><summary>Real World Application</summary>

# Real World Application for the Moving and Deleting Files Using GitBash

### Advantages of using the Command Line Interface (CLI)

- When using a command-line interface, you can use detailed commands more efficiently and faster than you can with a graphical user interface. It demonstrates the advantages of using a command-line interface in this case, as it can handle extremely repetitive tasks across a wide range of systems.
- With the assistance of a program like the computer cli or code, it is easier for the user to control everything. The user’s interface is slow when they navigate through different icons. This enables CLI to operate more quickly as commands are directly delivered to the computer. CLI is preferred by many professionals due to its speed and performance.
- All options and operations are invoked in consistent form, while with GUIs similar operations often appear on different menus with different interfaces and different applications have different approaches.
- All options and operations are documented (or should be), meaning that it is no more difficult to perform a rare operation than a common one.
- CLIs double as scripting languages (see shell script) and can perform operations in a batch processing mode without user interaction. That means that once an operation is analyzed, it can be saved in a script and consistently performed without further effort. With GUIs, users must start over at the beginning every time, as GUI scripting is more limited (and often nonexistent). Simple commands do not even need a script, as the completed command can usually be assigned a name and executed simply by typing that name into the CLI.
</details>
<details><summary>Implementation</summary> 

# Implementation for the Moving and Deleting Files Using GitBash topic

### Online Linux Emulators

To get hands-on experience using Linux commands, select one of the online Linux emulators located here:

[JSLinux](https://bellard.org/jslinux/)

Specifically, you should attempt the following commands (with appropriate parameters) in any order:

- cp
- mv
- rm

Note: The emulators do support file/directory creation and deletion, so feel free to create/delete files as appropriate!
</details>
<details><summary>Summary</summary> 

# Summary for the Moving and Deleting Files Using GitBash topic

Here some useful UNIX/Linux commands for moving and deleting files using GitBash. Always remember that UNIX/Linux commands are case-sensitive.

- mv: The mv command moves a files or directories.
- cp: The cp command is used to copy files or group of files or directories.
- rm: The rm command is used to remove objects such as files, directories, symbolic links and so on from the file system.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
