# Basic Linux Commands

## Tools
* Terminator (For Terminal)
* Ubuntu or CentOS

## Navigation Commands
* `pwd` for Print working directory
* `ls` for list contents of directory
* `ls -l` for long list of contents
* `~` (tilde) - This is a shortcut for your home directory. eg, if your home directory is `/home/ryan` then you could refer to the directory Documents with the path `/home/ryan/Documents` or `~/Documents`
*  `.` (dot) - This is a reference to your current directory. eg in the example above we referred to Documents on line 4 with a relative path. It could also be written as `./Documents` (Normally this extra bit is not required but in later sections we will see where it comes in handy).
* `..` (dotdot)- This is a reference to the parent directory. You can use this several times in a path to keep going up the hierarchy. eg if you were in the path /home/ryan you could run the command ls `../../` and this would do a listing of the root directory.
* `cd [location]` to move around folders

## Files

* `file` obtain information about what type of file a file or directory is.
* `ls -a` List the contents of a directory, including hidden files.
* `man <command to look up>` For example `man ls`
* `mkdir [options] <Directory>` for creating new directory
* `mkdir -p linuxtutorialwork/foo/bar` -p flag tells the system to create parent directories as well
* `rmdir [options] <Directory>` for removing a directory
* `touch [options] <filename>` Create new file
* `cp [options] <source> <destination>` Copying a file or directory
    ```
      $ ls
      $ example1 foo
      $ cp example1 barney
      $ ls
      $ barney example1 foo
    ```
* `cp -r <source directory> <destination directory>` Copy directories
* `mv [options] <source> <destination>` Move / Cut Directories
* `mv <olddirectoryname> <new directory name>` Renaming files / directories
* `rm [options] <file>` Removing a File (and non empty Directories)
* `rm -r <directory>` Removing non empty directories


    



