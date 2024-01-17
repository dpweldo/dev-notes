## Commands
~~~bash
whereis <command>
~~~
Shows binary source and manual pages for a command
~~~bash
locate PATTERN
~~~
Searches the database of files containing string and returning match of PATTERN in filename. Much faster than `find` command
~~~bash
updatedb
~~~
Updates system managed database of filenames
~~~bash
cd ~
cd $HOME
~~~
Options to get to home directory
~~~bash
cd ..
~~~
Changes to parent directory
~~~bash
cd /etc
~~~
changes to /etc directory in the root
~~~bash
ln fmt.txt format.txt
~~~
Creates hard link named `format.txt` for the file `fmt.txt`. `ln` creates links between files.
~~~bash
ln -s fmt.txt sym.txt
~~~ 
Creates a symbolic link. Symbolic links to OG file and not the inode itself, unlike a hard link. A file can only be deleted when all inode links are deleted.
~~~bash
touch
~~~
Can be use to update timestamp of file or create a blankfile with that name.
~~~bash
touch -c file1.txt
~~~
`-c` does no-create command which makes it not create any files
~~~bash
echo "Hey There!" > file.txt
~~~
Example of adding text to a `file.txt` file.
~~~bash
cat filename.txt
~~~
Displays content of file
~~~bash
vim sample
~~~
Opens `vi` editor for file named `sample`
~~~bash
wc -c sample
wc -m sample
wc -l sample
wc -w sample
~~~
`wc` print information about file. `-c` shows bytes, `-m` shows character count, `-l` shows line count, `-w` shows word count, 
~~~bash
cut -f 1 /etc/passwd
cut -c 1, 2, 3 /etc/passwd
cut -d ":" -f 3 /etc/shadow
cut -f 3 -d ":" /etc/passwd | sort -n
~~~
`cut` command removes/extracts section from file `-f 1` gets the first field of the file, `-c 1,2,3` gets first three characters, `-d ":" -f 3` gets thirst field and uses `:` separator, since its a colon separated file it will display only content of the third field. Last example displays it on the stdout after a numeric sort.
~~~bash
grep /home /etc/passwd
grep -c /bin /etc/passwd
grep root /etc/shadow
grep -r wlan /etc
~~~
`grep` prints lines that have matches with the pattern. First ex searches for `/home` string. Second `-c` displays the number of lines containing `/bin` string, `root` displays details of root user from the file. `-r wlan` seaches recursuvly (any sub directories) for the string `wlan`
~~~bash
find /etc -name pass*
find /etc -maxdepth 1 -name *.conf
find / -maxdepth 2 -perm 640
find /var/cache -maxdepth 2 -user root
find /var/cache -maxdepth 2 -uid 0
find /root -group root
find /root -gid 0
~~~
`find` command searches for files in directory heirarchy.  First example searches in /etc for files that start with pass. Second searches for extension of .conf. Third searches for permissions set to 640, and limits to 2 search levels. The 4th & 5th list the files in var/cache owned by root user to a limit of 2 levels. 6th & 7th list all the files in /root belonging to root group.
~~~bash
~~~
~~~bash
~~~
~~~bash
~~~
~~~bash
~~~