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

## Filters 🔎

* `head` View the first n lines of data.
* `tail` View the last n lines of data.
* `sort` Organise the data into order.
* `nl` Print line numbers before data.
* `wc` Print a count of lines, words and characters.
* `cut` Cut the data into fields and only display the specified fields.
* `sed` Do a search and replace on the data.
* `uniq` Remove duplicate lines.
* `tac` Print the data in reverse order.

Example: 

```
$ nl -s '. ' -w 10 mysampledata.txt
         1. Fred apples 20
         2. Susy oranges 5
         3. Mark watermellons 12
         4. Robert pears 4
         5. Terry oranges 9
         6. Lisa peaches 7
         7. Susy oranges 12
         8. Mark grapes 39
         9. Anne mangoes 7
        10. Greg pineapples 3
        11. Oliver rockmellons 2
        12. Betty limes 14
```

### Grep and Regular Expressions 🎒

egrep is a program which will search a given set of data and print every line which contains a given pattern. It is an extension of a program called grep. It's name is odd but based upon a command which did a similar function, in a text editor called ed. It has many command line options which modify it's behaviour so it's worth checking out it's man page. ie the -v option tells grep to instead print every line which does not match the pattern.

* `egrep [command line options] <pattern> [path]`

Example 

```
$ egrep 'mellon' mysampledata.txt
Mark watermellons 12
Oliver rockmellons 2
```

```
$ egrep -n 'mellon' mysampledata.txt
3:Mark watermellons 12
11:Oliver rockmellons 2
```

```
egrep -c 'mellon' mysampledata.txt
2
```

Basic Regular expressions blocks
* `.` (dot) - a single character.
* `?` - the preceding character matches 0 or 1 times only.
* `*` - the preceding character matches 0 or more times.
* `+` - the preceding character matches 1 or more times.
* `{n}` - the preceding character matches exactly n times.
* `{n,m}` - the preceding character matches at least n times and not more than m times.
* `[agd]` - the character is one of those included within the square brackets.
* `[^agd]` - the character is not one of those included within the square brackets.
* `[c-f]` - the dash within the square brackets operates as a range. In this case it means either the letters c, d, e or f.
* `()` - allows us to group several characters to behave as one.
* `|` (pipe symbol) - the logical OR operation.
* `^` - matches the beginning of the line.
* `$` - matches the end of the line.

```egrep '[aeiou]{2,}' mysampledata.txt```

### Bash Scripting 📝

A Bash script allows us to define a series of actions which the computer will then perform without us having to enter the commands ourselves. If a particular task is done often, or it is repetetive, then a script can be a useful tool.

```
$ cat myscript.sh
#!/bin/bash
# A simple demonstration script
# Ryan 7/8/2022
 
echo Here are the files in your current directory:
$ ls
$ ls -l myscript.sh
-rwxr-xr-x 1 ryan users 2 Jun 4 2012 myscript.sh
$ ./myscript.sh
Here are the files in your current directory:
barry.txt bob example.png firstfile foo1 myoutput video.mpeg
```

* `which bash` to find out the bash
* `#` for comments
* `.sh` file extensions

```
$ cat myscript.sh
#!/bin/bash
# A comment which takes up a whole line
ls # A comment at the end of the line
```

Variables: 
```
$ cat variableexample.sh
#!/bin/bash
# A simple demonstration of variables
# Ryan 7/8/2022
 
name='Ryan'
echo Hello $name
```

Sample backup Script

```
$ cat projectbackup.sh
#!/bin/bash
# Backs up a single project directory
# Ryan 7/8/2022
 
date=`date +%F`
mkdir ~/projectbackups/$1_$date
cp -R ~/projects/$1 ~/projectbackups/$1_$date
echo Backup of $1 completed

$ ./projectbackup.sh ocelot
Backup of ocelot completed
```

IF else statements

```
$ cat projectbackup.sh
#!/bin/bash
# Backs up a single project directory
# Ryan 7/8/2022
 
if [ $# != 1 ]
then
    echo Usage: A single argument which is the directory to backup
    exit
fi
if [ ! -d ~/projects/$1 ]
then
    echo 'The given directory does not seem to exist (possible typo?)'
    exit
fi
date=`date +%F`
 
# Do we already have a backup folder for todays date?
if [ -d ~/projectbackups/$1_$date ]
then
    echo 'This project has already been backed up today, overwrite?'
    read answer
    if [ $answer != 'y' ]
    then
        exit
    fi
else
    mkdir ~/projectbackups/$1_$date
fi
cp -R ~/projects/$1 ~/projectbackups/$1_$date
echo Backup of $1 completed
```




