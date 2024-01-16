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
~~~
test_variable="This is a variable"
~~~
Have to use $ to call out the variable
~~~
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