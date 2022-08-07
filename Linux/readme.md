# Basic Linux Commands

## Tools 🔨
* Terminator (For Terminal)
* Ubuntu or CentOS

## Navigation Commands 🗺
* `pwd` for Print working directory
* `ls` for list contents of directory
* `ls -l` for long list of contents
* `ls -ld` for directory contents
* `~` (tilde) - This is a shortcut for your home directory. eg, if your home directory is `/home/ryan` then you could refer to the directory Documents with the path `/home/ryan/Documents` or `~/Documents`
*  `.` (dot) - This is a reference to your current directory. eg in the example above we referred to Documents on line 4 with a relative path. It could also be written as `./Documents` (Normally this extra bit is not required but in later sections we will see where it comes in handy).
* `..` (dotdot)- This is a reference to the parent directory. You can use this several times in a path to keep going up the hierarchy. eg if you were in the path /home/ryan you could run the command ls `../../` and this would do a listing of the root directory.
* `cd [location]` to move around folders

## Files 🗂

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

## Vi Editor 📟

* `vi <file>` Single command line argument which is the file you would like to edit.
* `i` Press to get into insert mode
* `esc` to get back into edit mode
* `:q!` - discard all changes, since the last save, and exit
* `:w` - save file but don't exit
* `:wq` - again, save and exit
* `cat <file>` to view files (Can also be used for concatenating files)
* `less <file>` to view large / long files
* `Arrow keys` - move the cursor around
* `j, k, h, l` - move the cursor down, up, left and right (similar to the arrow keys)
* `^ (caret)` - move cursor to beginning of current line
* `$` - move cursor to end of the current line
* `nG` - move to the nth line (eg 5G moves to 5th line)
* `G` - move to the last line
* `w` - move to the beginning of the next word
* `nw` - move forward n word (eg 2w moves two words forwards)
* `b` - move to the beginning of the previous word
* `nb` - move back n word
* `{` - move backward one paragraph
* `}` - move forward one paragraph
* `u` - Undo the last action (you may keep pressing u to keep undoing)
* `U` (Note: capital) - Undo all changes to the current line

## Wildcards 🦄

* `*` - represents zero or more characters
* `?` - represents a single character
* `[]` - represents a range of characters

## Permissions 🔐

* `r` read - you may view the contents of the file.
* `w` write - you may change the contents of the file.
* `x` execute - you may execute or run the file if it is a program or script.

For every file we define 3 sets of people for whom we may specify permissions.

* `owner` - a single person who owns the file. (typically the person who created the file but ownership may be granted to some one else by certain users)
* `group` - every file belongs to a single group.
* `others` - everyone else who is not in the group or the owner.

```
$ ls -l /home/tanvir/linuxtutorialwork/frog.png

$ -rwxr----x 1 harry users 2.7K Jan 4 07:32 /home/tanvir/linuxtutorialwork/frog.png
```

In the above example the first 10 characters of the output are what we look at to identify permissions.

* The first character identifies the file type. If it is a dash ( - ) then it is a normal file. If it is a d then it is a directory.
* The following 3 characters represent the permissions for the owner. A letter represents the presence of a permission and a dash ( - ) represents the absence of a permission. In this example the owner has all permissions (read, write and execute).
* The following 3 characters represent the permissions for the group. In this example the group has the ability to read but not write or execute. Note that the order of permissions is always read, then write then execute.
* Finally the last 3 characters represent the permissions for others (or everyone else). In this example they have the execute permission and nothing else.

* `chmod [permissions] [path]` change permissions

chmod has permission arguments that are made up of 3 components

    * Who are we changing the permission for? [ugoa] - user (or owner), group, others, all
    * Are we granting or revoking the permission - indicated with either a plus ( + ) or minus ( - )
    * Which permission are we setting? - read ( r ), write ( w ) or execute ( x )

Examples: 
* `chmod g+x frog.png` Add execute permissions to group
* `chmod g+wx frog.png` Add write and execute permissions to group
* `chmod u-w frog.png` Revoke write permission permissions from user









    



