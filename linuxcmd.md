# CompTIA Linux+ LX0-103 and LPIC-1 (Exam 101): Introduction

# Module 1: Essential Skills

## Lesson 1: Performing Basic Tasks from a Shell Environment

#### 1.3 Finding Files and Commands on Linux System

#### Command Summary
  * finding
  * locate
  * updatedb
  * whereis
  * which
  * /etc/updatedb.conf

#### 1.4 Using Single Shell Commands and One-line Command Sequences

#### Command Summary

  * cal
  * cal 2029
  * cal 2029 > ~/calfile
  * cat ~/calfile
  * ps aux | grep http
  * man many

#### 1.5 Using and Modifying the Shell

To identify what shell that you are using, issue the following ```echo $SHELL```

Shell just interprets commands are transfer them to machine instructions to execute.  

They are internal and external commands to the shell. Remember that internal commands are built in the shell itself and external commands are third party commands that are installed to the Linux system.

[esc] + b  or [esc] + f - allows you jump to begin of a command/word or to the end of a command/word in very long complex string

[esc] + a  or [esc] + e - allows you jump to begin of a line or to the end of a line in very long complex string

#### Command Summary
  * bash
  * echo $SHELL
  * exit
  * env
  * MYDIR=/usr/share/lib
  * echo
  * cd $MYDIR
  * echo $MYDIR - in the subshell an is produced
  * exit
  * export TODAY - friday - allows for all shells displayed
  * exit
  * help - many commands are available
  *	help set	- long list of information
  *	help set | less - this give you a shorten view of the options that provide for the help
  * pwd
  * set
  * unset
  * uname - gives the name for OS
  * uname --help
  *	uname -p
  *	uname -r

#### 1.6 Using and Editing command History

##### Command Summary

  * history
  *	ls -a	- trying to locate the .bash_history file
  *	cat .bash_history - it may hold 500 to 1000 commands base on settings
  *	![line number] - re-run the command on the that line ex: 117
  * !! - will run the previous command that was just issued
  * [up] and [down] keys on the keyboard that allow you to go back to previous commands; this good for two or three commands
  * [ctrl] + r - reverse &#95;i&#95; search - starting typing and it will search the command that starts with those characters
      1.	tree -L 1 /proc - that was enter but wasn't in history
  *	history --help- found more in
  *	history -c	- cl ear out the hi story
  *	history - run this command again and everything is gone
  *	cat .bash_history	- will contain all the history information that was thought to be cl eared out
  * rm .bash_history - to permanently remove history; not really good thing to do

#### 1.7 Invoking Commands Inside and Outside the Defined Path

we need to understand what is happening when you issue a command on the command line.

You need to ask yourself, what actually is happening when issue a command on the command line? First, Linux goes though the system PATH and looks to see if that command is available.

If you try to call a command , ```$ hello``` that isn't in the current path; you need to provide the exact path to locate the command, ```$ ./hello```.

If you would like to call an internal command and you do not know if it is available; just issue ```$ help``` command and Linux will show you list available internal commands

If we type ```$ which time``` and use the complete path that is returned; try to issue the complete path with the command; if you receive a different results

This mean there is an internal command that is placed before the one that we've used eg.	```$ /usr/bin/time``` and ```$ time```

Let issue ```$ time ls``` this tell us how long it take to run the time command

Let issue ```$ /usr/bin/time ls```; this is doing the same but more information this the previous version

There can be a bi nary version and internal version of the same in which can leave many confused on the correct on to use.

By using the ```$ type``` before the command you are trying to issue. Givens us an idea where the command is coming from.

As you can see, the PATH is very important aspect of a Linux system. The PATH is built on the first process when is booted up. If could ```intit``` or ```sysmd``` base on the type of Linux distribution you have installed.

##### Command Summary
  *	ls
  *	env | grep PATH
  *	who
  *	vi m help -> echo hello world
  *	chmod +x hello
  *	hello
  *	./hello
  *	time - how do you know it a Linux command
  *	help
  *	which time
  *	/usr/bin/time
  *	time ls
  *	/usr/bin/time ls
  *	type time type useradd

#### Summary

The previous lesson was a warm-up to Linux OS and on the basic shell operations.

## Lesson 2: Processing and Working with Text Files

#### 2.1 Using Streams, Pipes, and Redirects

By default, ```$ ls``` command will go to the standard output(STDOUT) what is the current screen

You redirected the standard output with  ```>``` to a file like OUTFILE

If we issue the following command  ```$ ls > /dev/zero```

If we issue the following command ``` $ ls > outfile```

If we issue the following command ```$ cat /etc/hosts > outfile```

Now ```$ cat errfile``` checkout what redirected , will see the contains that is normally displayed on the screen in the file.

Single ```>``` will always overwrite the contents in the file that it redirected to.

Double ```>>``` will append the contents to the end of the file. In some case you would like to add information.

Let issue the following command  ```$ find / -name blah``` and you can see the all the errors on the screen. But this can be redirected to a file. I do not want to see the errors.

| Handle | Name 	| Description     |
|--------|--------|-----------------|
| 0	     |  stdin | standard input  |
| 1	     | stdout | standard output |
| 2	     | stderr | standard error	|

Lets issue the following command ```$ find / -name blah 2> /dev/nu11```; this would go no where

But if you like to review the errors, you need to redirect	to a file. Let issue the following command ```$ find / -name blah 2> errfile``` and then issue ```$ cat errfile``` to see what was saved in the file: ```errfile```. Remember that you will lose the previous contents. so use double ```>>```to retain the
previous and add the new data to the bottom.

There are ways to redirect from the STDIN what looks for input from the keyboard.

Issue the following mail command ```$ mai l -s hello root```, use ```mail -h```- for help.

It sits there waiting to for the body to be typed/entered or a dotted ```.``` to end send the mail. ```$
·mai l -s hello root /newline Please learn Linux. /newline. .``` is termation stdinput value that the ```mail``` command is looking to end and send message.

If we would like to do it on all in one command ```$ mail -s hello root <```

It you have a command that sending the standard error and the standard input	then you can take care of both in a single one; ```$ find / -name	hosts &> /dev/nu11```

so what is this doing? Its sending the standard error (STDERR) and the standard input (STDIN) to the same location which is ```/dev/null```
what if you would like to display the results of the  ```$ ls``` and redirect that same output to a fil e like ```ls.out```?

Issue the following command: ```$ ls | tee ls.out```and using ```$ cat l s.out```. You should see that results on the screen and i n the file as well. ```tee``` always works after the ```|``` pipe operation. The pipe will take the output of command and send it as the input to another command. But ```tee``` will send the output in two directions.

The following is an example of types of files that programs may create that are temporary files

```bash
 find / -name
 ```

But that is side not in finding special file any location.
we need to ```$find / -name "blah"``` so we go ahead create to 2 blah files

```bash
$ touch lbl ah
$ touch 2bl ah
```

Re-issue ```$ find I -name "blah"```  and see the results of the above fi l es in the results. Now we can issue ```$ find I -name "blah" | xargs -d "\n" rm```

what does the previous string of commands do?

1. find all the files that has ```blah``` at the end of its filename

2.	take the output and place it to ```xargs``` command force a new line character between the filenames with ```-d "/n"```

3.	remove the files that were provided in the input

###### Note: Many think ```xargs``` is complicated	but sometime is Linux things are improved. Here is the same results with only using the ```find``` command options

Try to issue this command ```find / blah" -exec rm {}\```
  1.	find all the files that has ```blah``` at the end of its filename
  2.	execute the ```rm``` command with the results of the previous ```find``` results defined with ```{}\```


#### Command Summary

* ls
* STDOUT
* 1s > outfile
* cat outfile
* ls » outfile
* cat outfile
*	find / -name blah
*	find / -name blah 2> errfile
* cat errfile
* tee
* xargs

## 2.2 File Viewing commands

Now we are going to look a commands that us look the contents of files.

Let revisit our old friend ```$ cat /etc/passwd``` so we know what it does.

Issue ```$ tac /etc/passwd``` and it is just ```cat``` in reverse, not sure how useful this command is

Issue ```$ cat -E /etc/hosts```, it ends each line with a dollar sign this is useful in some configuration files that may have spaces at the ends

Issue ```$ cat -T /etc/hosts```, it shows all the tabs in that are in a file

Issue ```$ cat -n /etc/hosts``` or $``` cat -n /etc/hosts > myhosts```, it shows all the lines of a file with line number

The command ```cat``` is useful but not for large files; ```less``` is more sui ted for very long files

Issue ```$ less /var/log/messages```, automatically allows you to page through page of content via pager view of the file, you can use up arrow or spacebar.

Issue ```$ tail /var/log/secure```, show the last 10 lines of the authentication related log messages. ```tail``` also have a useful flag called - ```-f``` that allows you follow the file as it is updated and ```-n``` allows ¥OU to see more then then default of 10 if 20	is passed in as ```tail -n 20 /var/log/secure```.

The opposite of tail is head , so try this out ```$ head -n 20 /etc/passwd```

Now we can combine	other commands to focus on a 2 lines like line 19 and 20 of ```/etc/passwd```. For example, ```$ head -n 20 /etc/passwd | tail -n 2```

We can refocus our attention to line 19 only by issuing	```$ head -n 19 /etc/passwd | tail -n 1``` to verify our results, we can issue ```$ cat -n /etc/passwd```

Very interesting command is ```od``` which is an octal dump, not used a lot but it on Linux+ exam.

### command summary
  *	head
  *	less
  *	tail
  *	cat
  *	od
  * cut

## 2.3 File Formatting Commands

Back in the day there wasn't many monitors that we have today. There as just printers that printed output so it was very important to instruct the computer format the file in particular way.

We'll start with the base command ```$ cat /var/log/secure``` and we see the file as normal.

Issue ```fmt -w 50 /var/log/secure```it print only 50 wide characters.

Issue ```$cat /var/log/secure | pr -d``` ,	adding page information to printed page you will have header.

Issue ```$ cat /var/l og/secure | pr -D |  lpr```, will send document to unix lined printer

Issue ```expand /var/hosts |cat -T```, will replace all tabs with spaces

### Command Summary
  * fmt
  *	pr
  *	expand
  * unexpand
  * convert

##  2.4	File Processing Commands

so let's talk about some other nice commands. we need to create a couple of example files.

* file1
  1	susie
  2	jane
  3	tarzan

* file2
 1	amsterdam
 2	antartica
 3	alabama

Issue ```join file1 file2```, will combine the two file base on the first field so the first column have to be similar.

Useful to merge ascii files.

Issue ```paste file1 file2```, it will take first line of both files and paste them to the standard output as well any following lines

Issue ```paste fil el fi l e2 > newfilse```, as above but redirect the output to a file

Issue ```cat /etc/hosts | nl``` ··- , gives you the number of lines but many utilities these days have options to provide this information. But back in the old days Unix gods felt that if there was utility that al ready perform a particular functionality why recreate that functionality

Here we are coming to create a file named ```$ vi m anotherfile``` - with the following contain:

```bash
 hello
 bye
 bye
 andhello
```

Now we are going to look at ```sed``` command , especially the following command and options
```bash
$ sed	-i s/bye/BYE/g anotherfile
 ```
where ```i``` means edit files in place which is interactive with file

where ```s/``` means substitute what follows with the another next string

where ```/g``` means apply globally to the entire file

This very usefully for configuration files that have settings that are placeholder; this save time in opening and editing it manually.

Now we are going to look at ```sort``` command , especially the following command and options

Here we need to create a file named  ```$ vi m sortfile``` with the following contain:
```bash
one
one
1
11
124
bye
beer
sleep
weekend
21
```
Issue	```sort sortfile```, the sortfile results are now sorted

```bash
1
11
124
21
beer
bye one
one
sleep
weekend
```

But note that 124 and 21 are not correct, because it take the first portion of the text not number. To make work with number we need to pass ```-n```

Issue ```	$ sort -n sortfile```, the sortfile results are now sorted
```bash
beer			
bye			
one			
one			
sleep			
weekend			
1			
11			
21			
124
```

Some older version of ```sort``` are case-sensitive. To make it work properly we need to pass ```-f``` version that need this flag will do all lower case and then uppercase

Issue	```sort -r sortfile```, will sort the file in reverse order

Issue ```sort -k2 file2```, the file2 results are now sorted in the second column

```bash
3   alabama
1   ansterdam
2   antartica
```

Good for analyzing data on the screen that is shown on Linux system with having to print it out.

This options above are sort	are frequently used and are not that common.

Now we are going to discuss ```split```;we need to create a bigfile to use.

Issue ```ls -R	/ >	~/bigfile```

##### Note: ```-R``` means list subdirectories recursively

Lets make sure we have that fil e created ```ls -l bigfile``` and it size is big as well
```bash
$	mkdi r
$ mv bigfile
$ cd temp
$ ls
$	split
 ```

Why is this useful?

Maybe your bigfile and plainly to big and you to look at it in small chunks, where you have 1000 lines per fil e

Now we are going to look at ··- tr ···command ; we goi ng to run a simple ```$ echo hi``` -> ```$ hi``` command we will see how ```$ echo hi I [a-z] [A-zJ``` -> ```$ HI```·

As you can see, ```tr```can translate, squeeze, and/or delete characters from standard input, writing to standard output.

This very useful in shell scripts when you will expect characters to be in a particular case.

Let's setup couple of files to tackle our next command.

Here we are need to create a file named ```$ vi m ufile``` with the following contain:

```bash
aa
aa
aa
bb
bb
cc
```
Issue ```$ uniq ufile ```command ; here is what we expect to get back

```bash
aa
bb
cc
```

Here we are need to create a file named ```$ vim somenames```	with the following contain:

```bash
linda
lisa
lori
bob
lori
bob
```
Issue ```$ uniq ufile``` command; here is what we expect to get back But we do see that same output with the same values

```bash
linda
lisa
lori
bob  
lori
bob
```
Remember that Linux/Unix philosophy is that commands/utilities should be combined	to get the functionality that each is good at to achieved the correct results.

Issue ```$ sort somenames | uniq``` and check out the results

```bash
bob
linda
lisa
lori
```

very useful command ```wc``` stands for word count checkout these results ```$ ls -R |  wc```

Now check out , ```cat /etc/passwd``` allows you to see the contents of this file. Now we combine that with ```wc``` and try ```cat /etc/passwd | wc```  

```bash
$ 23	36	1138
```
As you can see there are 23 lines so we have 23 users.

In total there are very useful commands and some that are not so useful. ```sed```, ```WC```	and	```sort``` are the ones that you should think about using more often.

##### command summary
* join
* paste
* nl
* sed
* sort
* split
* tr
* uniq
* wc


## 2.5 Understanding vi

The default editor in Linux is ```vi``` and it very oldest editor that been available for years.

Its a good idea to always give the name of the file that you want to work on when issuing the ```vi``` command

```bash
$ vi [filename]
```
By default, ```vi``` is opened in command mode this allows you to type command. To type, you must switch to input mode by issues the following commands:

  * i
  * o
  * a

When you are done in input mode, you must exit out of input mode by issue ```[esc]``` key

To save the file you need to issue ```:wq```

## 2.6 Editing Text Files with vi

There is ```vi``` and ```vim```, ```vim``` is a	Vi IMproved - enhanced ```vi``` editor version

Now let use the ```bigfile``` that we have created previously

```bash
$ vi ~/bigfile
```  

Issue ```:/run``` to search for any accordance of text 'run'
Issue ```[n]``` key to get to the next accordance of text 'run'

By issuing ```:/[sometext]``` you are looking downward and by issuing ```:?[sometext]``` you are looking upward.

Here is an example from our ```~/bigfile:```;  ```:?run``` go upward in the list and like we saw earlier  ```:/run``` will go downward in text

Remember that not all Linux systems have up and down keys. So will have to use a standard unix version which ```[h], [j], [k], [l]```

  * k - up
  * j - down (jump)
  * h - right  
  * l - left  

Now let talk about editing a file. We can use ```i``` for inserted and that will insert at the point of te cursor. The text will be insert at that location and the original text moved over one.

To append that location, we can use ```a``` for append after the point of the cursor.

To create a empty newline, we can use lower case ```o``` which stands for open a newline below the cursor

To create a empty newline, we can use upper case ```O``` which stands for open a newline above the cursor

Using ```d``` by itself does not do nothing  but use ```v``` and above direction keys: ```[h], [j], [k], [l]``` then ```d``` will delete the selected text, that it appears.

You are not deleting the text but placing that text within a buffer and allow it to be accessed later.

If you are not happy with your changes, you can use ```u``` for undo, all the way back to you ```vi``` session.

The caret key ```^``` allows you to go to the beginning of the line; [Shift] + 6

Let try the follow ```vi``` commands,   ```^```, ```v``` and ```G``` and this brings us to the bottom of the document. But it not all the data will need to do ```$```; [Shift] + 4 to get the result of the text.

Now that we issue ```d``` will remove the text and ```u``` will undo the deleted changes.

By pressing  ```v```, we can ```k``` to go up the several lines and then issue ```y``` this will invoke the yank operation

In our case, your yanked 11 lines which is like copy within ```vi``` then press ```p``` to paste the yanked lines to the  

```bash
11 lines yanked
```
If you haven't made a selection, you can do a ```yy``` on the line and it will copy that line then press ```p```

Placing your cursor on a line and issuing ```dd``` allows to remove a single

To get to the beginning of a file by issuing ```gg``` that send you to the beginning of file.

Very interesting command that allows you to go word by word is using ```w```

Within command mode, ```:%/lori/Lori``` this will run substitution with the values supplied. By adding ```g``` at the end, will apply global
to the file.   

To remove a single letter is by using the ```x``` on top of the letter to remove.

Each editor ```vi``` and ```vim``` display syntax differently. ```vim``` applies syntax highlighting while ```vi``` doesn't have this type of features. This is the reason to use ```vim``` instead of ```vi```

##### Command Summary
  * /, ?
  * h, j, k, l
  * i, o, a
  * c, d, p, y, dd, yy
  * ZZ, :w!, :q!, :e!
  * r, O
  * w, $, gg, G
  * :%s/old/new/g
  * u

## 2.7 Using Regular Expressions to Work with Text Files

Regular expression are very handle in grabbing text within text files.

There's a difference between basic and extended regular expressions!

Some regular expression will not work will all utilities because of this fact.

Bracket expressions: grep b[iae]g &#42; - look for all files that contains big &#42;, bag &#42;, beg &#42;,  

Range expressions: grep [0-9][0-9]&#42; - look for all the files that contain 2 numbers.

Any character: grep .&#42;

Line position: grep ^lisa$&#42; - looking for lines that start with lisa

Repetition operators:
    * &#42;:zero or more of preceding character
    * &#43;:one or more of preceding character
    * &#63;:zero or one of preceding character

Multiple strings: grep cat|dog &#42;
Parentheses: to define subexpressiions

##### Command Summary

None

## 2.8 Searching Text Patterns with grep

Here is a utility that uses regular expression allot is ```grep```

The following command ```$ ps aux``` that returns overview all processes on the Linux system

Lets see how ```grep``` can assist us here, we issue ```$ ps aux | grep nfs```

Let look at other ways ```grep``` can be used first go to ```$ cd /etc``` directory; issue ```$ grep sys * ``` and this will produce ```Is a directory``` results; we do not care for those messages in our output.

But we can send those message ```stderr```somewhere else and have our output look cleaner then what we saw before with ```$ grep sys * 2> /dev/null```

But it shows all files that contains any combination of ```sys``` but can use a regular expression to narrow it down to only lines that start with ```sys``` by issuing ```$ grep ^sys * 2> /dev/null```

#### Note: Remember that we have the filename:line that contains the text followed.

```bash
subgid:systemd-timesync:100000:65536
subgid:systemd-network:165536:65536
subgid:systemd-resolve:231072:65536
subgid:systemd-bus-proxy:296608:65536
subuid:systemd-timesync:100000:65536
```

We can also do combination searches that allows us to grep multiple text strings: ```$ grep -E "sys|nat" * 2> /dev/null```

More last option that we should be aware of is ```-i```, when used with grep is allows us to search with worrying about the case in which the text is in. So we can issue ```$ grep -i sys * 2> /dev/null```

The option are those that used most often but we still go to the ```$ man grep``` to learn more.

grep stands for: general regular expression processor

##### Command Summary
  * grep -R root/
  * grep -E "cat|dog" ~
  * ps aux | grep -v grep
  * grep -i bash *

## Summary

Make sure you can recognize the correct commands and the options that can be passed to them. We've went though some of the common options that is used most frequently.

## Lesson 3: Performing Basic File Management Tasks  

#### 3.1 Copying, Moving, and Removing Files

Basic file and directory manipulation

Here we can create directories and remove directories:

```bash
$ mkdir files
$ rmdir files
```

Sometimes it useful to create entire directory tree structures in a single command. If we try to create a two level like ```$ mkdir some/files```

It will produces the following error: ```$ mkdir somes/files```

``` bash
$ mkdir: cannot create directory 'some/files': No such file or directory
```

To properly create this type of structure you need to issue, ```$ mkdir -p some/files``` and then ```$ cd some```

Now let's copy files into this directory over by issuing ```$ cp /etc/h * .```

If we have directories in the source folder we can copy them over as well by issuing ```$ cp -R /etc/G* .``` Issue a ```ls``` to check the results.

Let try to remove a directory,

```bash
$ rm gss
rm: cannot remove 'gss': Is a directory
$ rmdir gss
rmdir: failed to remove 'gss': Directory not empty
$ rm -rf gss
```  
We need to use ```rm -f``` force the  ```rm``` command to remove a directory with content

Issue  ```$ ls -a``` - list all files and  hidden files
Issue ```$ ls -l``` - long listing of files

Another useful command is ```mv``` that moves or renames files

```bash
$ ls gai.conf
-rw-r--r--  1 root root    2584 Sep  2 20:29 gai.conf
$ mv gai.conf blah
$ ls blah ga*
ls: cannot access ga*: No such file or directory
blah
```
As you can see, the message shows that we do not have ```gai.conf```

Beware of using ```rm -rf / blah``` because it will remove you entire root directory

##### Command Summary
  * mv
  * ls
  * rm
  * rmdir

## 3.2 Using Wildcards

Wildcards are useful to return items that you do not know exact name but portions of the name.

```bash
$ cd /etc
$ ls h*
```
 Issue  ```$ ls -d h*```, is will list directories themselves, not their contents

Wildcards look like regular expressions but they are not

For example, ```$ grep 1[h*] 2[h*]```
  1. is a regular expression
  2. is a shell wildcard

Issue, ```$ s -d [abc]*``` - show me anything that starts with a, b, or c

Issue, ```$ ls -d [abc]?t*``` - show me anything that starts with a, b, or c and the second position I do not care but the third position it must be 't'

This is called globbing; Globbing interprets the standard wild card characters * and ?, character lists in square brackets, and certain other special characters (such as ^ for negating the sense of a match).

## 3.3 Other File Management Tools

These commands do not felt in with the other sections.

```bash
$ touch file1
$ touch file2
$ ls -l
-rw-r--r-- 1 root root 0 Sep  3 02:39 file1
-rw-r--r-- 1 root root 0 Sep  3 02:40 file2
$ date
Sun Sep  3 02:41:16 UTC 2017
$ date -s 02:51
$ touch *
$ ls -l
-rw-r--r-- 1 root root 0 Sep  3 02:50 file1
-rw-r--r-- 1 root root 0 Sep  3 02:50 file2
```
In case, we are focus on the timestamps on the files we created. This is useful when we have backup process that needs a particular time a file was last accessed.

The next useful command is ```file```  
```bash
$ file /etc/passwd
/etc/passwd: ASCII text
$ file file1
file1: empty
$ file /usr/bin/md5sum
/usr/bin/md5sum: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=38ef10c94031487d564682a4683cf2d41049c0b8, stripped
```
This command is very useful because Linux do not have extensions so this command allows you recognize the type of file you are working with

Next going back to review additional features of the ```find``` command. First we need to setup the demo by issuing the set of commands:

```bash
$ cd /
$ find / -name 'hosts'
/etc/hosts
/var/spool/postfix/etc/hosts
```
We well familiar with this usage for ```find```

Now we can issue,
```bash
$ find / -iname 'hosts'
/etc/hosts
/var/spool/postfix/etc/hosts
/home/cem/.rbenv/versions/2.3.3/share/ri/2.3.0/system/Resolv/Hosts
```
but iname is for case-insensitive searching

Now we going to look at ```-user``` flag

```bash
$ find / -user root
all files that root owns
```

Ok, lets looks a common user account and login as them plus we will create a couple of files. But first, issue ```useradd -m lori``` this will create a common user account with home directory

```bash
$ cat /etc/passwd
lori:x:1003:1003::/home/lori:/bin/sh
$ su - lori
$ cd /tmp
$ touch lori1
$ touch lori2
$ touch lori3
$ exit
$ find / -user lori
/home/lori
/home/lori/.bash_logout
/home/lori/.bashrc
/home/lori/.profile
find: `/proc/12511/task/12511/fd/5': No such file or directory
find: `/proc/12511/task/12511/fdinfo/5': No such file or directory
find: `/proc/12511/fd/5': No such file or directory
find: `/proc/12511/fdinfo/5': No such file or directory
/tmp/lori3
/tmp/lori1
/tmp/lori2
```
This type of ```find``` is very useful but we can go the next steps and provide additional operations with results that ```find``` command returns.

```bash
$ find -user lori -exec cp {} /root/dir \;
```
What can this type command be used for?

When there a ton of files on your system that you will like to clean up that was created by a particular user. This command comes in handle.

Note: ```{}``` refers to the results from find command and  ```\;``` closes out the ```-exec``` portion of the command

We've looked at ```find``` command options on ```-user``` and  ```-name```. Now we going check out ```-size```

Let review the man page on find first: ```$ man find```

```bash
$ find -size gt 10M
```
This may work but we try it later.

##### Command Summary
  * touch
  * file
  * find

## 3.4 Creating Backups

   Mother of all mothers of backups is ```tar``` command

   First we try to issue and explain what are different parts of this command, ```$ tar cvf /root.tar /root /home```


```bash
-c, --create       : create a new archive
-v, --verbose      : verbosely list files processed
-f, --file ARCHIVE : use archive file or device ARCHIVE
```
followed by [source] [destination]

Remember that order matters, make sure use this utility with the same options in the same order.

Another backup utility is ```cpio``` is good to know; stand for copy files to and from archives.

Another backup utility is ```dd``` is convert and copy a file not cc because that is the of C compile.
developer took the next letter in alphabet.

Remember Linux/Unix works with devices, so we can do something like ```$ dd if=/dev/sda1 of=sda1.img```  

```bash
if=FILE : read from FILE instead of stdin
of=FILE : write to FILE instead of stdout
```
This allows you to have to two identical hard disc by issuing ```$ dd if=/dev/sda1 of=/dev/sda2``` but you would have make sure that ```/dev/sda2``` is mounted on the Linux system.

Warning: ```$ dd if=/dev/zero of=/dev/sda2``` will ripe clean your entire hard disk. If are clearly do not care what happens to your hard drive.

Let's go back to ```tar``` command and we want to compress the tar file that we've created. We have several compression tools to choice from ```gzip, bzip2, and xz```.

```bash
$ gzip ~/cem.tar
$ ls -ld cem*
-rw-r--r-- 1 root root 81666628 Sep  3 19:59 cem.tar.gz
$ bzip2 cem.tar.gz
$ ls -ld cem*
-rw-r--r-- 1 root root 81416477 Sep  3 19:59 cem.tar.gz.bz2
```

After we compress the file gzip we compress it again with bzip2. It only compressed it a 200MB more with bzip2. Cool but not very useful.

```bash
$ bunzip2 cem.tar.gz.bz2
$ ls -ld cem*
-rw-r--r-- 1 root root 81666628 Sep  3 19:59 cem.tar.gz
$ gunzip cem.tar.gz
$ ls -ld cem*
-rw-r--r-- 1 root root 232028160 Sep  3 19:59 cem.tar
```
This isn't the most convenient way of creating a tar and zip file.

```bash
$ rm -f cem.tar
$ tar czvf backup /home/cem /home
$ ls -l backup
-rw-r--r-- 1 root root 255078377 Sep  3 20:50 backup
$ file backup
backup: gzip compressed data, last modified: Sun Sep  3 20:49:23 2017, from Unix
```

Here we see the same operations with fewer steps. Notice how useful the file command can be if you download or recive a file with or without an extension. You can alway use a handy ```file``` command.

##### Command Summary
  * tar
  * cpio
  * dd
  * gzip
  * bzip2
  * xz

#### 3.5 Analyzing and Extracting tar Backups

Now we have the this file called ```backup```, we can extract the contents but it would nice to see what is in it before extract the content. ```tar``` provides options the do such a task ```tar tvf backup```; this will show all the contents in the backup before extracting it.

All the files are relative and not absolute file names this means that the files can be placed anywhere and they will work as the originals.

Think very clearly what you are doing when you run the following ```tar xvf``` command and options. It would good idea to place it in a temporary location by including option flag ```-C```

```
-x, --extract, --get : extract files from an archive
-C, --directory DIR  : change to directory DIR
```

```bash
$ mkdir /restore
$ tar xvf backup -C /home/cem/linux+/restore/
```

This allows us to analyze what we extracted before it may cause files to be overwritten by a headache to recover from.

Another thing that backups are good for is when a user's home directory is removed by accident and the backups are all we have.

```bash
$ cd /home
$ rm -rf lisa
$ tar xvf backup home/lisa
```
Be carefully not to use ```tar xvf backup /home/lisa``` because we do not havethat but we do have ```tar xvf backup home/lisa``` from our backup file.

This means we can select certain portions of the backup file and not the entire backup structure.

##### Command Summary
  * tar -tvf myfile.tar
  * tar -xvf myfile.tar -C /mydestination  

#### 3.6 Understanding Links and Inodes

This section is to be able to understand how Linux system is organize on a hard disk.

Files data is stored in blocks; blocks is the basic structure of a hard drive. A block is basic a 4 kilobytes or more.

A collection of blocks are typical a type file. All the metadata/administrative data of a file is stored in an inode.

Every file has a single inode. The inode references each block with in the file. Each inode has a number on the Linux system. For an user, usinng the number system wouldn't be very easy to use. So that way we are working with filenames instead.

For example, ```/etc/hosts``` is used; which is the entry point to the inode. The relationship with filename and inode is one direction where filename is the parent and the inode is the child. The node do not know about the filename it may or not be pointed to.

Inode just keep track the filenames that is pointed with a counter. Each filename is considered to be a hardlink; with type of setup you can have multiple hardlinks attached to the same inode.

This allows multiple filenames pointing to the same file. This not a copy of the original file but a reference to the inode. In a file copy, you would get a new inode and a new hardlink would be created.

If anything changes in the original blocks the all the filenames that refer to the block's inode will is the changes. In the case when a filename is removed, the other hardlinks are still pointing to the inode so the data is still able to be referenced.

Linux provide a secondary method of creating links which is called ```symbolic links```. Symbolic link doesn't point to a inode it points to a filename. Symbolic allows you to work on files on a other device.

If a filename is deleted then the symbolic link becomes invalid.      

## 3.7 Managing Hard and Symbolic Links

Let's create some links in Linux.

```bash
$ cp /etc/passwd users
$ ls -il /etc/passwd users
19911 -rw-r--r-- 1 root root 1679 Sep  3 13:07 /etc/passwd
144031 -rw-r--r-- 1 cem  cem  1679 Sep  4 13:20 users
```
You can see that the inode number is different.

```bash
$ echo hello >> users
$ ls -il /etc/passwd users
 19911 -rw-r--r-- 1 root root 1679 Sep  3 13:07 /etc/passwd
144031 -rw-r--r-- 1 cem  cem  1685 Sep  4 13:23 users
```
You can see that the size has changed. So these two file totally independent of each other.

Now we are going to create a hard link  on users

```bash
$ ln users hard
$ ls -il users hard
144031 -rw-r--r-- 2 cem cem 1685 Sep  4 13:23 hard
144031 -rw-r--r-- 2 cem cem 1685 Sep  4 13:23 users
```
If you notice that they same the same inode number. Now execute:

```bash
$ echo someusers >> hard
$ ls -il users hard
144031 -rw-r--r-- 2 cem cem 1695 Sep  4 13:30 hard
144031 -rw-r--r-- 2 cem cem 1695 Sep  4 13:30 users
```

Now you can see that they both have the same size.

```bash
$ ln -s users hard
144031 -rw-r--r-- 2 cem cem 1695 Sep  4 13:30 hard
144031 -rw-r--r-- 2 cem cem 1695 Sep  4 13:30 users
```

```bash
$ ln -s symlink hard
ln: failed to create symbolic link 'hard': File exists
$ ln -s hard symlink
$ ls -il users hard symlink
144031 -rw-r--r-- 2 cem cem 1695 Sep  4 13:30 hard
144032 lrwxrwxrwx 1 cem cem    4 Sep  4 13:34 green[symlink] -> hard
144031 -rw-r--r-- 2 cem cem 1695 Sep  4 13:30 users
```
As you can see, new inode has been created for the symbolic and the symbolic only have a size of 4 bytes. Why? The word ```hard``` it only for characters and so that it only need that many characters to reference.

```bash
$ rm hard -f
$ ls -il users hard symlink
ls: cannot access hard: No such file or directory
144032 lrwxrwxrwx 1 cem cem    4 Sep  4 13:34 red[symlink] -> red[hard]
144031 -rw-r--r-- 1 cem cem 1695 Sep  4 13:30 users
$ cat symlink
cat: symlink: No suc fie or directory
```

The color has changed that indicates that the link is broken.
To fix this issue simply running the following commands.

```bash
$ ln users hard
$ cat symlink
```
### Summary

Learn how to work on the file system, how work basic file system commands and how to work on backups plus hard and symbolic links

## Lesson 4: Managing Processes

#### 4.1 Running Jobs in Foreground and Background

What is a job?

When you run a command from the shell that is considered a job. So issuing ```$ ls``` is a job. These type of jobs are executed immediately and run for a very short period of time.  

Ok. let issue this ```$ sleep 3600``` seconds or 1 hour. We'll not want that long so will do [ctrl]+z this will stop the job temporary.  Do not wait to long to make it a background job. ```bg``` command places the job in the background after it has been issued.

```bash
$ sleep 3600
^Z
[1]+  Stopped                 sleep 3600
$ bg
[1]+ sleep 3600 &
```
```
[1]+ means it is showing up as job 1 wit append sign behind it
```
Append sign is a method that allows you to place a command in the background immediately.

But we can move jobs to foreground by going though the filling steps:

```bash
$ jobs
[1]-  Running                 sleep 3600 &
[2]+  Running                 sleep 36000 &
$ fg 1
sleep 3600
```

If you do not want to have the job going anymore you can issue [ctrl] + c

A job usually sticks in the shell that it is running in. For example you opened a terminal session and decide to run background job and later you close you shell all the children processes will terminate as well. This is not what we would to happen for background jobs.

We like to have the background not attached to the shell. To accomplish this, you can use the ```nohup```

```bash
$ nohup find / -xdev -type f -perm +u=s -print > ~/findsuid.txt &
```
nohup - run a command immune to hangups, with output to a non-tty

screen is anohter technqie to accomplish the same task

```bash
$ ssh server201
$ screen
```
## Command summary
  * &
  * jobs
  * fg
  * bg
  * nohup
  * screen

#### 4.2 Sending Signals to Processes

To manage processes on a Linux system by sending signals to a process.

```bash
$ man 7 signal
```

This gives us an overview all the signals

```
Signal     Value     Action   Comment
----------------------------------------------------------------------
SIGHUP        1       Term    Hangup detected on controlling terminal
                              or death of controlling process
SIGINT        2       Term    Interrupt from keyboard
SIGQUIT       3       Core    Quit from keyboard
SIGILL        4       Core    Illegal Instruction
SIGABRT       6       Core    Abort signal from abort(3)
SIGFPE        8       Core    Floating point exception
SIGKILL       9       Term    Kill signal
SIGSEGV      11       Core    Invalid memory reference
SIGPIPE      13       Term    Broken pipe: write to pipe with no readers
SIGALRM      14       Term    Timer signal from alarm(2)
SIGTERM      15       Term    Termination signal
SIGUSR1   30,10,16    Term    User-defined signal 1
SIGUSR2   31,12,17    Term    User-defined signal 2
SIGCHLD   20,17,18    Ign     Child stopped or terminated
SIGCONT   19,18,25    Cont    Continue if stopped
SIGSTOP   17,19,23    Stop    Stop process
SIGTSTP   18,20,24    Stop    Stop typed at terminal
SIGTTIN   21,21,26    Stop    Terminal input for background process
SIGTTOU   22,22,27    Stop    Terminal output for background process

The   signals  SIGKILL  and  SIGSTOP  cannot  be  caught, blocked, or ignored.
```

Some signals are always implemented or some are not implemented. ```SIGTERM``` is a nice way to ask a process to please stop it work. ```SIGKILL``` is not a nice way to tell a process to stop doing its work. It will cause all the items that have opened to be closed which can cause damage. ```SIGHUP``` is used to reinitialize a process.

```bash
$
```

# Module 2: Administration Tasks

## Lesson 9: Managing Software

#### 9.1 Understanding Packages and Meta Package Handlers

#### 9.2 Understanding variations in Linux software Management

Major Linux distributions and their subversion distributions.

Red hat has rpm which standard for red hat package manager and Debi an has dpkg stands for Debi an package manager
  * Red Hat - rpm
    * Centos
    * Fedora
    * SUSE
  * Debian - dpkg (deb)
    * Ubuntu
    * Mint

Two different worlds; there a tool called alien to assist in using either other distributions package manager but it would be very difficult to install rpm on Debian distributions and vise a versa.

Issue the following commands to figure out what distributions is currently running on you favor of Linux Here are several method different listed below:

Issue ```$ cat /etc/*-release```- to provide simple output
Issue ```$ lsb_release -a``` - to find out the Linux distributions name/version
Issue ```$ /proc/version``` - to see kernel version and gcc version used to build the same

#### 9.3 Installing , Reinstalling , Upgrading , and Removing Packages using RPM and YUM

For the exam, be able to reproduce the correct command either its for rpm, yum or debian related package manager.

On Red hat system, most important is to use yum.

Issue	```yum search nmap``` looks in the repo for any that matches the nmap or search parameter .

Issue ```yum info nmap``` to get more information about the package

Issue	```yum install nmap``` if you like what you it will install directly from the repo and all the dependencies that is associated with that	package.

Issue	```yum search sealert``` may produce no matches.

yum is great tool to search and install packages but sometimes you will not found what you are looking for search. The search looks in the package description but you need to look at the actual files within the packages.

Issue	```yum whatprovides */sealert``` receive a list of packages that meet the supplied package name. If the result you will see the package name, package version	and platform.

ex: setroubleshoot-server-3.2.1 7.el7.x86_64

Issue	```yum upgrade``` without any arguments will upgrade everything on your system.

Issue ```yum upgrade kernel``` this will try to upgrade the kernel only

Issue ```yum repo list``` returns a list of repos that are currently being used

To locate or define the available repos, ```cd /etc/yum.repos.d/``` and then ```ls``` You will see a list of files that end will ```.repo```; each entry may contain mirror list that is considered import if that is used if it can connect to the base url.

##### Command Summary

Include in this are	commands not used often but are need for the exam:
*	rpm -ivh - used to install rpm without yum
*	rpm -uvh - used to update rpm without yum
*	rpm -e	- erase (uninstall) package
* rpm -F	- upgrade package(s) if already installed
*	rpm2cpi o - used to retrieve tar fil e within rpm; results cpio file
*	/etc/yum/repos.d
*	yum search
*	yum whatprovides
*	yum install
*	yum reinstall - when recent installed is accedient removed
*	yum remove
*	yum check-update
*	yum upgrade
*	yum clean
*	yum local install	- better then rpm -ivh
*	yum local update
* yum downloader


#### 9.4 Obtaining Information on RPM Packages

On Red hat system, allows you to do rpm queries to get information about packages. Let try this out from ``` $ cd /usr/sbin``` or ``` $ cd /sbi n``` and then ```$ ls``` Issue	```rpm -qf /sbin/ipmaddr```, it tells what package that is utility came from


Issue	```rpm -qi net-tools-l.60-110.el6_2.x86_64```, it tells what package that is utility came from

Issue	```rpm -ql net-tools```	it returns list of files in this package

Issue	```rpm -qd net-tools``` it returns all documentation within this package

Issue	```rpm -qc net-tools```	if a package has additional configuration files you can use this This feature uses the rpm database that holds all the information for all installed packages.


# CompTIA Linux+ LX0-104 and LPIC-1 (Exam 102)

## Lesson 3: Managing User and Group Accounts

#### 3.1 Adding, Modifying, and Removing Users

#### 3.2 Adding and Modifying Groups

```bash
$ useradd linda
$ groupadd sales
$ sudo ulindasermod -g sales linda
$ userdel linda
```
If you want to manage permissions on Linux system, you do not want to manage permission for individual users.

To add groups, we will start with ```groupadd --help```  
 ```
 -g, --gid GID                 use GID for the new group
```
 ```bash
  $ groupadd sales
groupadd: group 'sales' already exists
$ groupmems -g sales -l
linda
```
Users are assigned a primary group in which there name/username but its better to add them  

When you are adding or modifying groups there a several files that involved. Let check out /etc/passwd file

```
$ tail -n 5 /etc/passwd
```
##### Command Summary
