# Command Line Basics
BASH is both command line interpriter and programming language.

Command Prompt - is the short text at beginning of command line showing where you are. 

$ indicates the user is unprivilages and the prompt is ready to recieve.

/# Indicates root user

Commands are parced by interpriter and executed by the shell as a process.

Outputs are sent in one of two streams STDOUT and STDERR - can redirect or pipe elsewhere

#0 STDIN

#1 STDOUT

#2 STDERR

### Command Line Syntax


### Variables
Assigning
~~~bash
test_variable="This is a variable"
~~~
Have to use $ to call out the variable
~~~bash
echo $test_variable
This is a variable
~~~
Bourne Shell variables

$HOME current users home directory

$PS1 primary prompt string

$PATH colon separated list of directories

### Quoting
Preserving variables, disable treatments of words

Escape Character \ preserves the following character with the exception of new line (\n)

Single quotes preserv value of every character, including escape character.

Double quotes preserve most values, except Escape Character \, $ for variables, and ' for single quoting.

\ \ \ Is how you do one slash strangely enough.

### Man Pages
Man Pages is traditional forme of software documentation
~~~bash
man <command>
~~~
Includes: NAME, SYNOPSIS, DESCRIPTION, EXAMPLES

Exit Statuses too - return code parameters

Can search through page with a /, and scroll with n & N

man -k [word] will search description for key words

### Info Pages

More detail than man page. Has structure to link pages together.
~~~bash
info <command>
~~~
Uses pages concept. Go up with u, go to next page with n, home page with e, and previous page with p, search for word with /, and q to quit.

Sometimes it will just pull in the man page.

## Directories and Listing Files
### Files and Directories
To get info on `cd`
~~~bash
cd --help
~~~
If you dont specify it takes you to `$HOME`.
To get too root level `cd \`, top of level.

The following is the root directory as the hierarchy (contains I node where it is sectored on the disk):
~~~bash
/     root directory
/bin  user binaries (commands that can be run by user)
/boot static boot files (necessary to boot linux system)
/dev  device files (block terminal and sudo)
/etc  configuration files (often open source config like Apache)
/home user home directories
/lib  shared libraries
/mnt  temporary mounts (NFS or mounting some other drive)
/opt  optional packages
/proc kernel processes and files
/root root user home directory
/run  application state files
/sbin system administration binaries (used by root)
/srv  service data
/tmp  temporary files
/usr  user binaries
/var  variable data files
~~~
#### Moving Around
`pwd` to print working directory. `cd /home` to move to home. Hit tab to show options.
To go back go with `cd .` To go up `cd ..` Two levels `cd ../..` To go back one to last location too `cd -`

### Hidden Files and Directories
Files hidden from basic listing by preceding name with `.`
Can show with `ctrl h` in window. Not used to make secret, use permissions for that. Just used to not clutter. Can make with `touch` `mkdir` etc.

### Home Directories
User home directories containing user's files & directories, typically for ever user. 
~~~bash
/etc/password
~~~
Has a list of all the users, number that is user & root ID, whole name, home directory, and default shell that is recieved. A service account like sshd will have /usr/sbin/nologin because not direcotory. It is the master mapping of user system. `~` represents user home directory. Very handy for moving files.

Can look at variables with `env` command. Nothing implies `-i`. This is all your variables. 

### Absolute and Relative Paths
Path is unique location of file or directory. Absolute when it starts with / or as a relative path. 

Relative Path - relative to working directory
~~~bash
cat file1
~~~
Absolute Path - takes into consideration entire file system - works everywhere - always starts with / to symbolize root level
~~~bash
cat /home/cloud_user/file1
~~~

## Working with Files
### Creating, Moving, and Deleting Files and Directories
~~~bash
mkdir <NAME>
mkdir -p <Directory/Subdirectory> 
cp -r <SOURCE> <DESTINATION>
mv <SOURCE> <DESTINATION>
rm -r <NAME>
~~~
On `cp` you need `-r` so it copies recursivly inside the directories. Can rename directories with `mv` command. For `rm` you need `-r` recursion and can force it with `-f`.
~~~bash
touch <NAME> #Create or update timestamp
cat <NAME> #Prints on STDOUT
cp <SOURCE> <DESTINATION> #Same as directories
rm <FILEL>
file <FILE> #determines file type
~~~

### Case & Space Sensitivity
Most file systems are case sensitive. 
~~~bash
touch newfile
touch Newfile #creates two different files
mkdir New Folder #will create two folders
mkdir New\ Folder #Creates one folder called New Folder
~~~

### Simple Globbing
Globbing is using partial matching to work with groups of files and directories. Uses wildcard character to create the pattern

~~~bash
? #question mark - used to match any single chracter
ls file?
#returns...
file1 file2 file3 file4
ls ????1
#returns...
file1
* #Asterisk match any number of characters
ls file*
#returns any additional
fileCheese file1
ls *4 
#returns anything with 4 at end
file4 new4
[] #Brackets return anything in a range
ls file[1-3]
file1 file2 file3
ls *[1-3]
file1 file2 file3
[[:upper:]]
[[:lower:]]
[[:digit:]]
[[:alpha:]]
[[:alphanum:]]
~~~

~~~bash
^ #used to match starting character
$ #used to match ending character
{} #used to match more than one pattern
| # used for applying more than one condition
~~~