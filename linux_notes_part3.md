# Command Line
## Archiving
### Archiving Files and Directories
Archive is process of combining multiple files and or directories into a single file. Done as a backup process, usually use `tar`

~~~bash
-c #create archive 
-x #extract archive
-r #append to an archive
-t #list the contents of an archive
-f #read from or write to a file
-z #from zipped file
~~~

~~~bash
tar cf archive.tar test_file_* #creates archive file of the name archive.tar of all name test_file_*
tar tf archive.tar #prints all contents of archive.tar
~~~
It does not remove OG files, but you can delete OG and archive is still alive
~~~bash
tar rf archive.tar file? #appends new files of name file? to the archive
~~~
~~~bash
tar xf archive.tar file3 #extracts specific file from tar, specify directory if within one in the tar
tar xf archive.tar #extracts everything
tar xf archive.tar --wildcards 'test_file_?' #neet to use wildcard tag to use globbing on extraction
~~~
Extraction does not remove from the archive (it is very rare) so...
~~~bash
tar --delete --file=archive.tar file3
~~~
Usually just extract and then recreate the tar file.
### Archives and Compression 
~~~bash
df -h #shows your disk space
~~~
`gzip` is the default compression using `-z`. has a -1 through -9 (the best) to adjust zip speed
~~~bash
tar czf archive.tar file_*
gzip -9 archive.tar #compresses to maximum extent
~~~
`bzip2` alternative a bit slower but with higher compression uses `-z`
~~~bash
tar cjf archive.tar.bz2 file_*
~~~
`zip` uses the `zip` command and all in one popular with lots of OS
~~~bash
zip -r archive.zip file*
~~~
can use other commands

## Searching and Extracting Data From Files
### Command Line Pipes
Piping one command to another. `|`

`grep` utility searches any given input files selecting lines that match patterns. 

~~~bash
file1 file2 file3 file4
ls | grep 1
file1
grep -E  ^M american-english #everything that starts with M in the file -E is for expression search
~~~
~~~bash
cat file | grep Apple #very common cat grep combo by using STDIN of cat
wc #word count command
cat file | grep Apple | wc -l #gives you number of words with Apple
!wc #will rerun last command you used that began with that command
~~~
~~~bash
cut #removes section of files -d is deliniator and -f is field
cat /etc/passwd |grep michael | cut -d: -f6 #returns home directory of user
~~~

### I/O Redirection
Redirecting output to or from a file you use `>`. Append a file with `>>`
~~~bash
cat american-english | grep Apple > apple_result.txt #sends command output to file
cat american-english | grep Ball >> apple_result.txt #appends with ball results
~~~
you can use `sort` to put in order 

You can use `<` to read input in. A way to feed input into a command. Usually you traverse the other way with `cat file |`
~~~bash
grep Apple < sorted.txt #Returns everthing Apple within the file
~~~

### Basic Regular Expressions
Often called (regex) used to match patterns in text similar to globbing. Need to use the `-E` to get regex. `egrep` is an old command still around.
~~~bash
"^Apple" #Matching Start of Line
cat american english | grep -E "^seed" #would only show words beginning with seed in the dictionary
"Apple$" #Matches end of line
"^Apple$" #Matches either start or end
"Apple|Ball" # | servers as an or so it shows both Apple and Ball
"^Apple|Ball$"
"Ap*le" #Match an A followed by zero or more p followed by le
"Ap+le" #Match an A followed one or more p followed by le
"Ap?le" #Match an A followed by maybe more p followed by le
"Ap[p-z]le" #Match an A followed by p through z followed by le
"^l...s$" #Match starts with l and ends with x while having 3 letters between
~~~

## Turining Commands Into a Script
### Basic Shell Scripting
The `#` is called the shabang, beginning the script. Following # are all comments. The following is an example shell script:
~~~shell
#!/bin/bash
# These are comments

echo "Please enter your name: "
read name
echo -e "Hello $name!\n"
~~~

`#!/bin/bash` defines the interpriter to be used & # are comments. Can creat in file with `.sh` file ending and modify with `vim` or `>>` to modify shell script. To make it executable you need to change permissions...
~~~shell
ll script.sh
--rw-r--r--
chmod +x script.sh
ll script.sh
-rwxr-xr-x
~~~
Need to add to $PATH variable to run without specifying path like `./script.sh`

~~~shell
PATH=$PATH:$HOME/bin/ #adds home bin to path of executable
echo $PATH #to check it was added
~~~

#### If Statements
~~~shell
if [some text]
then
 <commands>
fi
~~~
Condition Statements...
~~~shell
![expression] #expression is false (negates it)
-n [string] # the lenght of string is greater than zero
-z [string] # the lenght of the string is zero
string1 = string2
string1 != string2
integer1 -eq integer2
integer1 -gt integer2
integer1 -lt integer2
-d [file] # the file exists and is a directory
-e [file] # the file exists
-r [file] # the file exists and read perm is granted
-s [file] # the file exists and size is greater than zero
-w [file] # the file exists and the write permission is granted
-x [file] # the file exists and the execute permission is granted
~~~

#### For Loops

~~~shell
for <variable> in <list>
  do <command(s)>
done
#Example
for i in 1 2 3; do echo $i; done
1
2
3
#Example
for i in $(ls); do echo $i; done
file1
file2
file3
file4
~~~
### Common Text Editors


~~~shell
head file #first 10 lines
tail file #last 10 line
head -n 100 fiel #first 100 lines
~~~
`vim` common powerfull editor for larger too

~~~shell
vim filename
#Moving around
gg #takes you to first line
G # takes to last line
10G #takes you to 10th line
set nu # gives you line numbers
#Inserting
i #insert at curser
I #insert at start of line
o #append line under curser
esc #get out of insert mode
#exiting
:w # wirte file (saving)
:q #quit file
:wq #write and quit
#Help
vimtutor #interactive helpful vim utility
~~~

`nano` easier more intuative file
~~~shell
nano file.txt
CTRL + x # exit with prompt to save
CTRL + o # exit will prompt to save
~~~