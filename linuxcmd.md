# CompTIA Linux+ LX0-103 and LPIC-1 (Exam 101): Introduction

# Module 1: Essential Skills

## Lesson 1: Performing Basic Tasks from a Shell Environment

### Learning objectives

Let's get started with lesson one now.

In this lesson, you'll learn how the files on a Linux computer are organized.

This is important knowledge because as a Linux administrator you'll work a lot on the file system.

We'll cover basic tools as well and working with the shell, which is the environment you'll be using to work with the commands.

#### 1.1 Understanding the File System Layout in the FHS

So let's talk about file system hierarchy.

In your computer, you probably have a hard disk.

Let's say this is the hard disk.

If you install Linux on the hard disk, you are going to have a root directory on your hard disk.

And below the root directory, you will have many different directories.

These directories can be on the hard disk itself or somewhere else:

    * /boot - standard directory that holds everything your computer needs to startup
    * /usr - default directory where Linux keeps the binaries
    * /var - where Linux places logs files
    * /home - where your users home directories are

On a Linux system, it is probably to connect different devices to standard or new created directories.

This technqie is called mounting; this is a important aspect of Linux system what is happening with mounting.

Imagine that your home directory is becaming very full, you decide to install a different hard disk. Tell your current ```/home``` directory to mount on the new hard disk filesystem. This allows you to extend your Linux operating system is organized.

To understand the detail layout of Linux system you need to know FHS - filesystem handling standard. It indicates that you filesystem should have a detail layout.

That means FHS creates a standard for any Linux distribution. So any Linux will have the same directories listed above.

#### 1.2 Knowing the Location and Purpose of Important Files and Directories as Defined in the FHS

Now let we log into this CentOS box so that we can talk about how the file system hierarchy is organized on a typical Linux machine.

As I just mentioned, it's not random at all, how Linux is organized.

There's a standard, and if you want to know all about this hierarchy standard, you just type ```$ man hier```.  

```bash
$ cd /
$ ls

```    

#### 1.3 Finding Files and Commands on Linux System

This lesson is about finding stuff.

Especially about finding files and commands and anything else that is useful on a Linux system.

There's a couple of commands to help you do that.

The most important command, well, it's not difficult to guess, is ```find```.

If you use ```find```, there are many, many options, but let me just start by doing an example.

#### Command Summary
  * finding
  * locate
  * updatedb
  * whereis
  * which
  * /etc/updatedb.conf

#### 1.4 Using Single Shell Commands and One-line Command Sequences

So now that we have a basic understanding of the layout of the Linux file system and how we can find stuff let's have a look at working from the shell.

The shell is the default command interpreter environment.

Basically the thing that we are looking at right now that's the shell.

In this shell you type commands such as ```ls``` for a listing of files or ```pwd``` for print working directory.

#### Command Summary

  * cal
  * cal 2029
  * cal 2029 > ~/calfile
  * cat ~/calfile
  * ps aux | grep http
  * man many

#### 1.5 Using and Modifying the Shell

Now let's talk about some features of the shell, because the shell as a command interpreter environment has a lot of internal commands to make working with the shell possible.

So the name of the default shell in Linux is ```bash```.

You can type that as a command and if you do, you start with subshell.

You cannot really see that but if you type exit again, you leave the subshell, basically this is something that is

To identify what shell that you are using, issue the following ```echo $SHELL```

Shell just interprets commands are transfer them to machine instructions to execute.  

They are internal and external commands to the shell. Remember that internal commands are built in the shell itself and external commands are third party commands that are installed to the Linux system.

* ```[esc] + b```  or ```[esc] + f``` - allows you jump to begin of a command/word or to the end of a command/word in very long complex string

* ```[esc] + a```  or ```[esc] + e``` - allows you jump to begin of a line or to the end of a line in very long complex string

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

One of the more useful features of the Shell, is the command ```history```.

Let's type ```history```.

And you can see a long list of commands that have previously been executed on this computer.

The interesting thing about the
command ```history``` is that it survives log out.

By default, the command ```history``` is written to a file with the name bash ```history```.

```bash
$ ls
$ ls -a
$ cat .bash_history
$ !75
$ !!
$

```
If we try to issue just ```ls``` at the ```/home/[user]``` we will not be able to see the ```.bash_history``` file

We need to are trying to locate the ```.bash_history``` file with issuing ```ls -a``` command, we need to add more aguments to ```ls``` because ```.bash_history``` is a hidden file .

 To display the contents of ```.bash_history```we need to  issue: ```cat .bash_history```, this file can hold 500 to 1000 commands base on settings

We can also use	![line number] to re-run the command on that line: ex: 117

Issuing: ```!!``` - will run the previous command that was just issued

Here are some command that aslo can be use with Shell history:

  * [up] and [down] keys on the keyboard that allow you to go back to previous commands; this good for two or three commands
  * [ctrl] + r - reverse &#95;i&#95; search - starting typing and it will search the command that starts with those characters
      1.	tree -L 1 /proc - that was enter but wasn't in history
  *	history --help- found more in
  *	history -c	- clear out the hi story
  *	history - run this command again and everything is gone
  *	cat .bash_history	- will contain all the history information that was thought to be cl eared out

We can remove the current history by issusing ```rm .bash_history``` - to permanently remove history; not really good thing to do

##### Command Summary

  * history
  * .bash_history

#### 1.7 Invoking Commands Inside and Outside the Defined Path

Now we need to understand how a Linux system is behaving when you type a command,  mean, I type ```ls``` and it is doing something, but what exactly is it doing?

I don't know, but I'm going to explain to you.

On a Linux system in the environment there is a path setting.

You need to ask yourself, what actually is happening when issue a command on the command line? First, Linux goes though the system PATH and looks to see if that command is available.

If you try to call a command , ```$ hello``` that isn't in the current path; you need to provide the exact path to locate the command, ```$ ./hello```.

If you would like to call an internal command and you do not know if it is available; just issue ```$ help``` command and Linux will show you a list of available internal commands

If we type ```$ which time``` and use the complete path that is returned; try to issue the complete path with the command; if you receive a different results

This mean there is an internal command that is placed before the one that we've used eg.	```$ /usr/bin/time``` and ```$ time```

Let issue ```$ time ls``` this tell us how long it take to run the time command

Let issue ```$ /usr/bin/time ls```; this is doing the same but more information this the previous version

There can be a binary version and internal version of the same in which can leave many confused on the correct on to use.

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
  *	type time
  * type useradd

#### Summary

So this was our first lesson.

This lesson was to get warmed up with the Linux operating system.

You have learned some of the Linux basics and we have had a look at some of the basics of shell operation.

We've seen shell environment and we have seen how the shell is working to interpret whatever you are typing.

Let's move on to lesson number two.

## Lesson 2: Processing and Working with Text Files

### Learning objectives

In this lesson, you'll learn how to work with text files.

This is an important lesson also for the exam.

On Linux, many utilities exist to view, process, and modify text files, and in this lesson, you'll learn about them.

You'll also learn how to create your own text files using the vi editor and how to work with regular expressions to make processing text files easier.

#### 2.1 Using Streams, Pipes, and Redirects

Let's talk about using streams, pipes and redirects.

Now what exactly is all that?

Well if a command is running, it produces output.And the output basically goes to the standard output.

Standard output, in fact, is something that is defined on a Linux box and we call it STDOUT.

STDOUT is your screen.

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

Lets issue the following command ```$ find / -name blah 2> /dev/null```; this would go no where

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

Issue the following command: ```$ ls | tee ls.out``` and using ```$ cat l s.out```. You should see that results on the screen and i n the file as well. ```tee``` always works after the ```|``` pipe operation. The pipe will take the output of command and send it as the input to another command. But ```tee``` will send the output in two directions.

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

This brings us to the end of the long lesson two, processing and working with text files.

In this lesson you have learned about some very useful commands and some very obsolete commands.

But even if the commands are obsolete, if you go to the LPI exam it will be good if you have a good understanding and knowledge of all of these commands.

You should be prepared to recognize the correct commands and the options that can be passed to them. We've went though some of the common options that is used most frequently.

## Lesson 3: Performing Basic File Management Tasks  

### Learning objectives

Hi, welcome to lesson three.

In this lesson, you will learn how to apply basic file management tasks.

We will talk about moving and copying files, about links and inodes, and about backup.

All of these are important topics on the exam and essential skills for a Linux administrator.

So, let's get started.

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

Now wildcards are about the shell, and they make matching files easier.

Wildcards are useful to return items that you do not know exact name but portions of the name.

We've basically already seen a couple of wildcards when I did ```ls h*``` for example, it tells me to check all files that have a name starting with an ```h```.

Oh by the way, if you notice this weird behavior, in ls ```h*```, I asked it, show me everything

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

So let's talk about some other file managements tools.

These are some tools, that don't really fit into anywhere, but we need to talk about them anyway.

First, there's touch.

Touch is a useful command.

And just create a temporary directory, so that we cans tart from an empty directory.

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

The mother of all backup utilities is ```tar```, ```tar``` stands for tape archiver. Mother of all mothers of backups is ```tar``` command

And if you want to create a backup using ```tar``` you start with the argument c.

By the way, in ```tar``` there is no dash in front of the argument, just ```type c``` and ```tar``` will understand what you want to do.

    * ```C``` stands for create by the way.

Then you will also like ```v``` for verbose.

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

Here we see the same operations with fewer steps. Notice how useful the file command can be if you download or receive a file with or without an extension. You can always use a handy ```file``` command.

##### Command Summary
  * tar
  * cpio
  * dd
  * gzip
  * bzip2
  * xz

#### 3.5 Analyzing and Extracting tar Backups

So, we have just created this file with the name backup,
and we know that it's backup because the name of the file is backup.

Sometimes life makes sense.

So, let's see what we can do with it.

Now, you can use tar to extract the backup, but I would always recommend first to show what is in it, and to do that, you use tar ```tvf```. T stands for type, but basically, it will show us the contain.  

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

Every file has a single inode. The inode references each block with in the file. Each inode has a number on the Linux system. For an user, using the number system wouldn't be very easy to use. So that way we are working with filenames instead.

For example, ```/etc/hosts``` is used; which is the entry point to the inode. The relationship with filename and inode is one direction where filename is the parent and the inode is the child. The node do not know about the filename it may or not be pointed to.

Inode just keep track the filenames that is pointed with a counter. Each filename is considered to be a hardlink; with type of setup you can have multiple hardlinks attached to the same inode.

This allows multiple filenames pointing to the same file. This not a copy of the original file but a reference to the inode. In a file copy, you would get a new inode and a new hardlink would be created.

If anything changes in the original blocks the all the filenames that refer to the block's inode will is the changes. In the case when a filename is removed, the other hard links are still pointing to the inode so the data is still able to be referenced.

Linux provide a secondary method of creating links which is called ```symbolic links```. Symbolic link doesn't point to a inode it points to a filename. Symbolic allows you to work on files on a other device.

If a filename is deleted then the symbolic link becomes invalid.      

## 3.7 Managing Hard and Symbolic Links

Now that we all understand how hard and symbolic links are working on Linux, let's create some links.

So, I will first make a copy of ```/etc/passwd```, and I will call it users.

I want to work on an independent file.

What I want to show you is ```ls -il```.

    * ```- i``` stands for iNote number.

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

So this was Lesson 3.

In this lesson, youhave learned how to work

on the file system.

We have learned working with some basic filesystem management commands, such as CP and so on, and you have learned how to work with backups and links.

So now that you have acquired pretty the basic experience, let's move on to Lesson 4.

Learn how to work on the file system, how work basic file system commands and how to work on backups plus hard and symbolic links

## Lesson 4: Managing Processes

### Learning Objectives

Welcome to lesson four.

In this lesson, you'll learn how to manage processes.

This is an important skill because everything that is happening on a Linux system is happening as a process

This lesson teaches you how to monitor processes and also shows you how to manage processes which includes terminating processes and changing process priority.

#### 4.1 Running Jobs in Foreground and Background

Now in this lesson, we are talking about jobs and processes.

What you should know is what exactly is a job?

Well, if you run a command from the shell, that's a job.

Now this is a job that is executed and it exits immediately because it runs for a short time only.

Some jobs run for a long time.

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

To manage processes on a Linux machine, you can send signals to the process.

Many signals are defined in the Linux kernel.

Let's type, man seven signal to get an overview of all the signals that exist.

And these signals are just specific instructions that a process cannot ignore.

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

Hi, welcome to part two of this course.

In this part you will learn about common Linux administration tasks.

At this point, you have acquired the basic skills to work with Linux, so it's time to get a bit deeper into exploring the Linux operating system.

Learn about common Linux administration tasks. At this point you have the basic down to work with Linux, it time to go deeper with Linux OS.

## Lesson 5: Design Hard Disk Layout

### Learning Objectives

In lesson five, you'll learn how a hard disk layout is organized.

You'll learn about different file systems and partitions, about swap space and logical volumes, about requirements to boot a system and why a Linux system typically consists of different partitions and logical volumes.

### Summary

So this concludes lesson five.

In this lesson you have learned how to organize this layout.

We have looked at the different file systems that are mounted into the Linux file system hierarchy.

And you have seen how petitions or electrical volumes can be used to compose all that.

Let's move on to the next lesson.

## Lesson 6: Creating Partitions and Filesystems

### Learning Objectives

Hello, and welcome to lesson six.

It's good to see that you're still around, and I hope you like this course so far.

In this lesson we continue talking about partitions and filesystems.

First you'll learn about the differences between GPT and MBR bootloaders and how it affects the way you create partitions on a Linux system.

Next, we'll look at the fdisk and gdisk utilities.

The utilities that I use to create partitions.

### Summary

So this brings us to the end of Lesson Six.

In this lesson you have learned how to create Partitions, and we have seen the difference between Primary Partitions, Extended Partitions, Logical Partitions.

We have also seen that on GPT it behaves different than on NBR.

You've also learned how to create Filesystems, and how to check file system problems.

Now let's move on to the next lesson

## Lesson 7: Common Filesystem Management Tasks

### Learning Objectives

Hi, welcome to lesson seven.

This is the last lesson that is about file system management.

This lesson has two important topics.

You'll learn how to mount and un-mount file systems and how to make sure this happens automatically while booting.

You'll also learn how to limit the amount of disk space that is available to users by working with quota.

#### Summary

In this lesson, you have learned how to mount file systems.

We've talked about mounting and unmounting file systems manually, and how to automate that through the ```fstab```.

We've also talked about quota management, and you have learned how to set a quota so that you can limit the amount of disk space that is available to users.

Now, let's move on to Lesson Eight.

## Lesson 8: Managing Permissions

### Learning Objectives

Hello, and welcome to lesson eight.

This is one of the most important lessons in this course.

You'll learn how to work with permissions.

We'll talk about the basic read, write and execute permissions, as well as the advanced SUID, SGID, and sticky bit partitions.

You'll also learn how to apply these permissions to your systems.

#### 8.6 Using Access Modes such as SUID, SGID, and Sticky Bit

So we've learned that there is set user id: ```SUID```, set group id ```SGID``` and sticky bit.

We will demonstrate all three special permission below.

```bash
$ cd  /home/laura
$ vim game
```

```
#!/bin/bash

echo Do you want play a game?
read

rm -rf /
```
```bash
$ su laura
$ chmod +x game
$ ls -l
```
Now is going to happen?

At this point user: laura is trying to run as laura. This script will try to remove everything on the hard drive with the wrong permissions and the danger will be limited.

So let talk about ```SUID```, in order to set issue
```bash
$ chmod u+s game
$ ls -l
-rwsr-xr-x 1 root root 58 Sep 16 06:39 game
```  

Now if laura try to run the game script she will be using the user ```root``` with more permissions

Now will look a ```SGID```, this very useful on a share group directory. We have a shared group directory ```/group/sales```  

```bash
$ cd /group
$ ls -l
drwxrwx--- 2 lisa sales 4096 Sep 16 01:04 sales
$ su - laura
```
laura should be able to make files in this directory because we set that this up already in the ```/etc/group```

```
sales:x:1002:lisa,laura
```
```bash
$ cd /group/sales
$ ls -l
-rw-r--r-- 1 laura laura 0 Sep 16 07:04 file1
```
##### Note that the permissions are not set properly it should be, I might have to fix later:
```
-rw-rw-r-- 1 laura laura 0 Sep 16 07:04 file1
```

As you can see, the user owner is laura and the group owner is laura.

So what does this means for laura's co-workers in the sales group?

They will get access to the file under the others permission. Because they are not members of the group laura.

This is not very useful in a shared group environment. The solution to this is to apply ```SGID``` on the sales directory.   

```bash
$ chmod g+s sales
$ ls -l
total 4
drwxrws--- 2 lisa sales 4096 Sep 16 07:04 sales
$ su - laura
$ cd /group/sales
$ touch file2
$ ls -l
total 0
-rw-r--r-- 1 laura laura 0 Sep 16 07:04 file1
-rw-r--r-- 1 laura sales 0 Sep 16 07:16 file2
```

The ```set group id``` on a directory has automatically set the group id to the parent directory and this will work for even subdirectories.

```bash
$ mkdir sub
$ cd sub
$ touch ff
$ ls -l
-rw-r--r-- 1 laura sales 0 Sep 16 07:20 ff
$ exit
```

Let do something else,

```bash
$ su - lisa
$ id
uid=1004(lisa) gid=1004(lisa) groups=1004(lisa),1002(sales)
$ ls -l
total 4
-rw-r--r-- 1 laura laura    0 Sep 16 07:04 file1
-rw-r--r-- 1 laura sales    0 Sep 16 07:16 file2
-rw-r--r-- 1 lisa  sales    0 Sep 16 07:24 lisa1
-rw-r--r-- 1 lisa  sales    0 Sep 16 07:24 lisa2
-rw-r--r-- 1 lisa  sales    0 Sep 16 07:24 lisa3
drwxr-sr-x 2 laura sales 4096 Sep 16 07:20 sub

```
Look that ```SGID``` is still doing its job.

```bash
$ su - laura
$ cd /group/sales/
$ ls
file1  file2  lisa1  lisa2  lisa3  sub
```

Is laura allowed to issue ```$ rm -f lisa2```?

Well we need to consult the group permissions that laura is a part of?

Yes, she can but we only want owner to be able to delete they own file. Here is where sticky bit plays a important part.

#### Note: For some reason my files did not have group write permission set, so I had to run from root - ```$ cd /group/sales && chmod g+w *```  

```bash
$ chmod +t sales
$ su - laura
$ cd /group/sales
$ rm -f lisa2
rm: cannot remove 'lisa2': Operation not permitted
```
This how sticky bit can be used to protect our environment.

We've been using chmod in relative mode via now will see in absolute mode.

Now we are using 4 digits, where the first digit special permission.  

 ```bash
$ exit
$ chmod 4770 sales
$ ls -l
drwsrws--- 3 lisa sales 4096 Sep 16 07:34 sales
$ chmod 3770 sales
$ ls -l
drwsrws--T 3 lisa sales 4096 Sep 16 07:34 sales
$ chmod +t sales
$ ls -l
drwsrws--T 3 lisa sales 4096 Sep 16 07:34 sales
```
#### 8.7 Modifying the File Creation Mask

We probliy notice when a user creates file some default permission are applied.

This comes from the ```umask``` : 0022

We'll start from 666 because will never grant 777 what is execute permission automatically on files.

Fir file: 666 - 022  = 644

For directory: 777 - 022 = 755

```bash
$ mkdir dir
$ ls -ld dir/
drwxr-xr-x 2 root root 4096 Sep 16 07:58 dir/
```

umask is a varible set in the shell environment

On distributions, there is a difference in umask for user root and ordinary users.

#### Note: 0002 on Centos not on Debain

It not good to use anything in the first position of the umask but its always 4 digits.

The digit can be ignored like ```$ umask 007``` and issue ```$ umask``` again

```bash
$ su - laura
$ umask 007
$ touch home
$ umask 022
$ touch home2
$ ls -l
-rw-rw---- 1 laura laura   0 Sep 16 08:06 home
-rw-r--r-- 1 laura laura   0 Sep 16 08:07 home1
$ exit
```

Remember that umask is a shell variable setting and you will have to take care of it in a setup script.

```bash
$ cd /etc
$ ls bash
$ vim bashrc
```
This not need for for 101 exam - thought its for 103 exam

#### Course Summary
   * umask

### Summary

learn work with basic permissions and special permissions. Also learned about concept of ownership. Also learned about chown, chgrp and chmod. Plus how umask is used as default setting when creating files and directories.

## Lesson 9: Managing Software

You learn how to manage software on Linux. You will also learn the Debian
approach and Red Hat approach. How to work with the respective package managers.
Know when to which commands because it is an important topic on the exam.  

#### 9.1 Understanding Packages and Meta Package Handlers

Before we begin, we need to understand the one fundamental difference in managing software. That is the between a ```package``` and a ```meta package handler```.

Let look at ```rpm``` or ```dpgk```, a package has something called ```dependency```
dependency means that in order to install specify software you need other software.
Because many software packages are using libraries that allow you to get functionality from some else.

In Linux before the ```meta package handler```, this was often problematic. This means,
you would download some software on the web and the installer would complain about missing dependencies. What meant that you had to go back on the web and download all the dependencies before you can install the original software you were trying to install in the first place.

This process was so painful that it had its own name: ```dependency hell```

The solution for ```dependency hell```  is the ```meta package handler```

What is in the ```meta package handler```?

A repository, it is topically a web server, directory or anything that provides installable packages.

When a user install software, they will go though the ```meta package handler``` and ```meta package handler``` will to repository to retrieve the package. During the installation phase it automatically check the repository for dependencies.

On Red Hat the ```meta package handler``` is ```yum```and Ubuntu it is ```apt``` but on SUSE it is the ```zyppor``` utility. There are others out there but it doesn't matter what one you are using the solution behind it is always the same.    

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

Issue	```rpm -qc net-tools```	if a package has additional configuration files you can use this feature uses the rpm database that holds all the information for all installed packages.

Issue	```rpm -qpc net-tools```	if have a package that you haven't installed yet  you can also query it plus the configuration files on it

Issue	```rpm -V```	is for verify a package compares information about the installed files in the package with information about the files taken from the package metadata stored in the rpm database. Checks the status of what has been changed since installation.

##### Command Summary
  * yum info
  * rpm -qpi
  * rpm -q on installed and uninstalled
  * rpm -qi
  * rpm -V

#### 9.5 Understanding Debian/Ubuntu Package Management

Debian packages are organized in the same way as rpm. To work with these packages we use ```dpkg``` utility. This is useful to work with package and database that is already installed on your system; just like ```rpm``` for RedHat.

```bash
$ dpkg --get-selections
```

Now that we know what the type of packages are installed. We can see what files are installed with the package by issuing:

```bash
$ dpkg -L vim
```

If would like to know which package that a file come from:

```bash
$ dpkg -S  /usr/bin/eject
eject: /usr/bin/eject
```

So it returns the name of package and the name of the file (that searching for)

```bash
$ dpkg -S eject
eject: /usr/lib/eject/dmcrypt-get-device
eject: /usr/share/locale/pt/LC_MESSAGES/eject.mo
eject: /usr/share/doc/eject/README
linux-image-3.16.0-4-amd64: /lib/modules/3.16.0-4-amd64/kernel/net/ipv4/netfilter/nft_reject_ipv4.ko
eject: /usr/share/doc/eject/copyright
eject: /usr/share/locale/de/LC_MESSAGES/eject.mo
eject: /usr/share/locale/ru/LC_MESSAGES/eject.mo
eject: /usr/lib/eject
linux-image-3.16.0-4-amd64: /lib/modules/3.16.0-4-amd64/kernel/net/netfilter/nft_reject_inet.ko
eject: /usr/share/locale/tr/LC_MESSAGES/eject.mo
eject: /usr/share/doc/eject/changelog.Debian.gz
linux-image-3.16.0-4-amd64: /lib/modules/3.16.0-4-amd64/kernel/net/netfilter/nft_reject.ko
eject: /usr/share/locale/fr/LC_MESSAGES/eject.mo
eject: /usr/share/locale/sl/LC_MESSAGES/eject.mo
eject: /usr/share/doc/eject/changelog.gz
eject: /usr/share/locale/zh_TW/LC_MESSAGES/eject.mo
eject: /usr/share/locale/cs/LC_MESSAGES/eject.mo
eject: /usr/share/locale/it/LC_MESSAGES/eject.mo
eject: /usr/share/doc/eject/TODO
eject: /usr/share/man/man1/eject.1.gz
eject: /usr/share/locale/sv/LC_MESSAGES/eject.mo
linux-image-3.16.0-4-amd64: /lib/modules/3.16.0-4-amd64/kernel/net/ipv6/netfilter/nft_reject_ipv6.ko
eject: /usr/share/lintian/overrides/eject
eject: /usr/share/doc/eject/AUTHORS
eject: /usr/share/doc/eject
eject: /usr/share/doc/eject/NEWS.gz
eject: /usr/share/locale/pt_BR/LC_MESSAGES/eject.mo
eject: /usr/share/locale/es/LC_MESSAGES/eject.mo
eject: /usr/share/locale/ja/LC_MESSAGES/eject.mo
eject: /usr/bin/eject
```
This does a regular expression on every that matches all the files that meet the search value

```bash
$ dpkg -p wget

Package: wget
Priority: important
Section: web
Installed-Size: 1725
Maintainer: NoÃ«l KÃ¶the <noel@debian.org>
Architecture: amd64
Multi-Arch: foreign
Version: 1.16-1+deb8u1
Depends: libc6 (>= 2.17), libgnutls-deb0-28 (>= 3.3.0), libidn11 (>= 1.13), libnettle4, libpsl0 (>= 0.4.0), libuuid1 (>= 2.16), zlib1g (>= 1:1.1.4)
Recommends: ca-certificates
Conflicts: wget-ssl
Filename: pool/main/w/wget/wget_1.16-1+deb8u1_amd64.deb
Size: 495812
MD5sum: 1cca36679c3dad4adec9121c4fab47b4
Description: retrieves files from the web
Description-md5: 63a4a740bcd9e8e94bf661e4f1806e02
Homepage: http://www.gnu.org/software/wget/
Tag: implemented-in::c, interface::commandline, network::client,
 protocol::ftp, protocol::http, protocol::ssl, role::program,
 suite::gnu, use::downloading, works-with::file
SHA1: 1103a7e4f82bebd3fe85ef26cc4200b896355c44
SHA256: 0982f09bf056fb0be9c2a519a20009c4c7dc8df45e05de983ae2c04e82cd1ab8
```
This basically gives you information on a package.

Here is a listing of the most important package commands:

dpkg, dselect and apt-get are the tools
  * dpkg -i - install
  * dpkg --configure - reconfigure
  * dpkg -r - removes, but leaves configuration; use -P to purge config
  * dpkg --get-selections - show currently installed
  * dpkg -p - prints information about an installed package
  * dpkg -l packagename - gives info about an uninstalled package
  * dpkg -L - lists installed files associated with a package
  * dpkg -S - pattern locates the packages that own a specific file
  * dpkg -C - checks for partially installed packages

Here is the  ```$ dselect ``` command that is a menu driven interface. It is not
installed by default but it very useful    

Here ```cat /etc/apt/sources.list``` we have the location where all repositories
are stored at when issue ```sudo apt-get install```

Before using ```sudo apt-get install``` it is good practice to use ```apt-get check```;
this command makes sure all the information  updated and available by comparing
the current state with state of the packages listed in the repositories and
rebuilding the local cache.

Now that we use commands like ```apt-get show [whatever package]```- it displays
the latest information on that package.

Another useful command is ```apt-cache search [whatever package]``` - if you do
not know the exact name of the package; you pass generic name like ```ldap```.  
Getting a list of packages with ```ldap``` in its description.

To add to the command above ```apt-cache depends [whatever package]``` - allows
you query all dependencies for package. For example:

```bash
$ apt-cache depends sudo
Depends: libaudit1
  Depends: libc6
  Depends: libpam0g
  Depends: libselinux1
  Depends: libpam-modules
  Conflicts: sudo-ldap
  Replaces: sudo-ldap
```

In for reverse operation, we can get all the packages that is depended on the
package. ```apt-cache rdepends [whatever package]```

```bash
$ apt-cache rdepends sudo
Depends: libaudit1
sudo
Reverse Depends:
  ctdb
    sudo-ldap
  xfce4-session
    sudo-ldap
  wicd-curses
    sudo-ldap
  wicd-cli
    sudo-ldap
  wajig
    sudo-ldap
  ubuntu-dev-tools
    sudo-ldap
  sudo-ldap
    sudo-ldap
  sudo-ldap
......
```

To get any stats on the installed packages, you can run the following command:

```bash
$ apt-cache stats

Total package names: 54297 (1086 k)
Total package structures: 54300 (3041 k)
  Normal packages: 41905
  Pure virtual packages: 407
  Single virtual packages: 4724
  Mixed virtual packages: 460
  Missing: 6804
Total distinct versions: 43759 (3151 k)
Total distinct descriptions: 84911 (2038 k)
Total dependencies: 271981 (7615 k)
Total ver/file relations: 45188 (1085 k)
Total Desc/File relations: 84911 (2038 k)
Total Provides mappings: 7702 (154 k)
Total globbed strings: 80 (655 )
Total dependency version space: 1115 k
Total slack space: 52.3 k
Total space accounted for: 15.1 M
```

The meta-package handler for Debian is ```apt-get install``` but before you us this command
you must ensure that the state of the packages installed on your Linux system is
in sync with the packages that are listed in the ```/etc/apt/sources.list```. You
can do this by issuing ```sudo apt-get update```.

You may get errors message on downloading; it fix that just re run
the ```sudo apt-get update``` command.

Now lets install ```nmap``` package -
```bash
$sudo apt-get install nmap
sudo apt-get install nmap
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
 libc-ares2 libv8-3.14.5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
 libblas-common libblas3 libgfortran3 liblinear1 liblua5.2-0
 libpcap0.8
Suggested packages:
 liblinear-tools liblinear-dev
Recommended packages:
 ndiff
The following NEW packages will be installed:
 libblas-common libblas3 libgfortran3 liblinear1 liblua5.2-0
 libpcap0.8 nmap
0 upgraded, 7 newly installed, 0 to remove and 84 not upgraded.
Need to get 4651 kB of archives.
After this operation, 20.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://http.us.debian.org/debian/ jessie/main libgfortran3 amd64 4.9.2-10 [255 kB]
Get:2 http://http.us.debian.org/debian/ jessie/main libblas-common amd64 1.2.20110419-10 [8496 B]
Get:3 http://http.us.debian.org/debian/ jessie/main libblas3 amd64 1.2.20110419-10 [167 kB]
Get:4 http://http.us.debian.org/debian/ jessie/main liblinear1 amd64 1.8+dfsg-4 [32.9 kB]
Get:5 http://http.us.debian.org/debian/ jessie/main liblua5.2-0 amd64 5.2.3-1.1 [82.4 kB]
Get:6 http://http.us.debian.org/debian/ jessie/main libpcap0.8 amd64 1.6.2-2 [133 kB]
Get:7 http://http.us.debian.org/debian/ jessie/main nmap amd64 6.47-3+deb8u2 [3973 kB]
Fetched 4651 kB in 0s (11.1 MB/s)
Selecting previously unselected package libgfortran3:amd64.
(Reading database ... 32933 files and directories currently installed.)
Preparing to unpack .../libgfortran3_4.9.2-10_amd64.deb ...
Unpacking libgfortran3:amd64 (4.9.2-10) ...
Selecting previously unselected package libblas-common.
Preparing to unpack .../libblas-common_1.2.20110419-10_amd64.deb ...
Unpacking libblas-common (1.2.20110419-10) ...
Selecting previously unselected package libblas3.
Preparing to unpack .../libblas3_1.2.20110419-10_amd64.deb ...
Unpacking libblas3 (1.2.20110419-10) ...
Selecting previously unselected package liblinear1:amd64.
Preparing to unpack .../liblinear1_1.8+dfsg-4_amd64.deb ...
Unpacking liblinear1:amd64 (1.8+dfsg-4) ...
Selecting previously unselected package liblua5.2-0:amd64.
Preparing to unpack .../liblua5.2-0_5.2.3-1.1_amd64.deb ...
Unpacking liblua5.2-0:amd64 (5.2.3-1.1) ...
Selecting previously unselected package libpcap0.8:amd64.
Preparing to unpack .../libpcap0.8_1.6.2-2_amd64.deb ...
Unpacking libpcap0.8:amd64 (1.6.2-2) ...
Selecting previously unselected package nmap.
Preparing to unpack .../nmap_6.47-3+deb8u2_amd64.deb ...
Unpacking nmap (6.47-3+deb8u2) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up libgfortran3:amd64 (4.9.2-10) ...
Setting up libblas-common (1.2.20110419-10) ...
Setting up libblas3 (1.2.20110419-10) ...
update-alternatives: using /usr/lib/libblas/libblas.so.3 to provide /usr/lib/libblas.so.3 (libblas.so.3) in auto mode
Setting up liblinear1:amd64 (1.8+dfsg-4) ...
Setting up liblua5.2-0:amd64 (5.2.3-1.1) ...
Setting up libpcap0.8:amd64 (1.6.2-2) ...
Setting up nmap (6.47-3+deb8u2) ...
Processing triggers for libc-bin (2.19-18+deb8u7) ...
```

Other commands like; ```apt-get upgrade``` and ```apt-get dist-upgrade``` perfroms
a dependencies resolution process that determines from important to not so important
packages are not dropped.

To check for breaking installing by issuing ```apt-get check```

To clean the package cache by issuing ```apt-get clean``` - this is also good
to free up disk space for packages that are not used anymore.

Here is a listing of the most useful apt-get commands:

* ```apt-get``` installs from repository
  * uses /etc/apt/sources.list
  * ```apt-get update```: updates infromation about pacages (cache)
  * apt-get upgrade: upgrades all installed packages
  * apt-get dist-upgrade: smart, doesn't upgrade if the breaks a dependency
   * apt-get install/remove
   * apt-get clean: cleans cache
* Some additional options can be used, with specific commands as listed above
    * -d upgrade -> download only
    * -m upgrade -> ignore missing packages
    * -s ALL simulate install
    * -y feeds a yes if you do not want to interact with prompt

Do not forget about ```alien``` utility that allow you install rpm or tar achieves on Debian Linux system .

#### 9.6 Finding Packages Containing Specific Files.

There are tools on Debian that allow you find specific files.

Like ```dpkg -L``` - lists installed files associated with a package   

Or ```dpkg -S``` - _pattern_ locates the packages that own a specific file  

#### 9.7 Obtaining Package Information about Debian Packages

You get package infromation on Debian packages on you Linux system

* ```dpkg --get``` - shows currently installed  

* ```dpkg -p``` - prints Information about an installed package

* ```dpkg -l``` - gives info about uninstalled packages

#### Summary

In this lesson we went a ton commands, for the exam go over as many a you can.

Also take in consideration the configuration files  for Red Hat and Debian especially Debian repositories that are being used, with ```/etc/apt/source.list```. Need to know which files are where. Be prepared to enter command name and fill the blanks and select the right options.

Pretty Important items here.

# Module 3: Advanced Management Tasks

## Lesson 10: System Architecture

#### 10.1 Enabling and Disabling Integrated Peripherals

Enabling and disabling integrated peripherals

This one of those topics on the LPI Exam that make you question what were they thinking about.  

There are different approaches, it not that simple as want to use it then connect it or you do not want to use then disconnect it. But you should know there are computer bios that plays a role in enabling and disabling integrated peripherals but there is also a process named ```udev```. This process helps the kernel to activate and deactivate peripherals.

With ```udev```, we can use rules that determine what we can do with a peripheral. That could be interesting because that could be one way to instruct the hardware to take action when a piece of hardware is plugged in. Using ```udev``` rules allows you to specify that only usb keys from particular brand can be are accepted.

After we've defined the ```udev``` rules, we can see actually what on own our computer that is used.

Remember, with ```/proc``` filesystem we can see the current state of our Linux system. We can drill down to specific hardware or device information like ```scsi``` details. The ```/proc``` filesystem works together with ```sys``` files, where ```sys``` are like a hardware interface to the kernel. We can get very detailed information on everything that is installed. When you get down to the block level from the ```/proc/scsi/sys/block/```, you can see that you have symbolic links for hardware to ```/devices/...``` that points you to the exact location of the device.

```bash
$ cd /proc
$ ls
{output results goes here}
$ cd scsi
$ ls
{output results goes here}
$ cd sys
$ ls
{output results goes here}
$ cd block/
$ ls
{output results goes here}
$ ls -l
{output results goes here}

```

If you want a easy access to the hardware there; are the ```ls*``` utilities. Like ```lsblk``` which list block devices. This gives a convenient overview of block devices or ```lscpu``` which gives us
detail information on cpu . ```lsusb``` which gives us detail information on usb devices. ```lspci``` which gives us detail information on pci devices.

```bash
$ ls [tab]
ls           lsblk        lslocks      lspci
lsattr       lscpu        lsmod        lspgpot
lsb_release  lsinitramfs  lsof
$ lsblk
{output results goes here}
$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 61
Model name:            Virtual CPU a7769a6388d5
Stepping:              2
CPU MHz:               2394.454
BogoMIPS:              4788.90
Hypervisor vendor:     KVM
Virtualization type:   full
L1d cache:             32K
L1i cache:             32K
L2 cache:              4096K
NUMA node0 CPU(s):     0
$ lsusb
{output results goes here}
$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:01.2 USB controller: Intel Corporation 82371SB PIIX3 USB [Natoma/Triton II] (rev 01)
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:02.0 VGA compatible controller: Cirrus Logic GD 5446
00:03.0 Ethernet controller: Red Hat, Inc Virtio network device
00:04.0 SCSI storage controller: Red Hat, Inc Virtio block device
00:05.0 Unclassified device [00ff]: Red Hat, Inc Virtio memory balloon
00:06.0 Unclassified device [00ff]: Red Hat, Inc Virtio RNG
```
Basically, how you can get an overview if what is configured hardware wise on your Linux system.

#### 10.2 Configuring Systems with or without External Peripherals

Here is another specification in the LPI exam objective is configuring systems with or without external peripherals.

So what exactly is this about?

This about servers that can be configured with or without a keyboard.

So how can you do this?

On some types of servers, you will have blade servers that do not have keyboard or any type of optical device.

So how do you interact with them as administrator?

As a Linux administrator, you should have a idea how to approach these type of servers. To install these types of servers you can use a unattended installation, like an installation server. An installation server, doing a PXE boot from the network. Here it will get information, like the installation image, from the network everything is prepared that allow the server to install itself. Once these systems are installed, we need to be able to remote access them via ```ssh``` - secure shell allows you to get remote or VNC - that give graphical access to a remote server. A service can be configured with a ```management board```, what is contains its own operating system that allows you to do remote connection to the system.  

What is PXE boot used for?

In computing, the Preboot eXecution Environment (PXE, sometimes pronounced as pixie) specification describes a standardized client-server environment that boots a software assembly, retrieved from a network, on PXE-enabled clients.

#### 10.3 Differentiating Between the Various Types of Mass Storage Devices

Let talk about different block devices.

The single most important part of information about block device is the ```/proc/partations``` file

This the kernel perspective of the block devices installed on the Linux system.

```bash
$ cat /proc/partations
```

major minor  #blocks  name

 254        0   15728640 vda
 254        1   15727227 vda1
  11        0    1048575 sr0

On most Linux systems, you will see the ```sd``` devices that stands for SCSI and SATA controllers device file name is - sda, sdb, sdc.


### Note: ```/dev/sda``` is the first disk that's either SCSI or (more likely) providing the SCSI drive API to user land. This includes SATA drives and IDE drives using libata. This can also be an IDE/SATA/SCSI/etc. drive emulated by the hypervisor.

#### ```/dev/vda``` is the first disk using the virtualization-aware disk driver. The performance should be much better, as the hypervisor doesn't have to emulate some hardware interface.

#### If the disk has been exposed to your VM under both interfaces, you should prefer ```/dev/vda``` as it'll almost certainly be faster.

  * sda  - first SCSI
  * sda1 - second SCSI   

If you see ```sdb``` then you can that this system may have 2 different ```SCSI``` disc.

If you see ```sr``` thats the optical drive. So if you see ```sr0``` is the first optical drive.

Don't forget about ```fd0```, there are not used often these days

There other devices like ```hd``` which are classic IDE devices.   

KVM visual machine - ```vda``` discussed above

And ```xvd``` devices are used Xen visual machines.

SAN devices are not seen with a different type; they are labelled as ```sda``` devices

Remember that you can see these devices by issuing ```$ cat /proc/partations``` or ```$ lsblk```; just a different way to see the same information.

```bash
$ cat /proc/partations
major minor  #blocks  name

 254        0   15728640 vda
 254        1   15727227 vda1
  11        0    1048575 sr0

$ lsblk
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sr0     11:0    1 1024M  0 rom
vda    254:0    0   15G  0 disk
#&39;-vda1 254:1    0   15G  0 part /
```

But with ```lsblk``` you can see additional information in the major and minor (MAJ:MIN)  column how the kernel see the device. The kernel doesn't care about ```sda``` labels
it mainly care about major and minor device category.

This devices are defined as files in the ```/dev``` directory. The Linux kernel automatically takes cares of creating these files.

```bash
$ cd /dev
....
dvd              sg0                 tty27  tty53  vcsa
fd               shm                 tty28  tty54  vcsa1
full             snapshot            tty29  tty55  vcsa2
fuse             snd                 tty3   tty56  vcsa3
hidraw0          sr0                 tty30  tty57  vcsa4
hpet             stderr              tty31  tty58  vcsa5
hugepages        stdin               tty32  tty59  vcsa6
hwrng            stdout              tty33  tty6   vda
initctl          tty                 tty34  tty60  vda1
input            tty0                tty35  tty61  vfio
...
$ ls -l sd*
ls: cannot access sd*: No such file or directory
$ ls -l vd*
brw-rw---- 1 root disk 254, 0 Sep 16 00:46 vda
brw-rw---- 1 root disk 254, 1 Sep 16 00:46 vda1
```  

The  column of the permissions indicates what of file that is references. For example, b in ```brw-rw---- ``` stands for block device.

```bash
$ ls -l
crw-rw---- 1 root tty       7, 128 Sep 16 00:46 vcsa
crw-rw---- 1 root tty       7, 129 Sep 16 00:46 vcsa1
crw-rw---- 1 root tty       7, 130 Sep 16 00:46 vcsa2
crw-rw---- 1 root tty       7, 131 Sep 16 00:46 vcsa3
crw-rw---- 1 root tty       7, 132 Sep 16 00:46 vcsa4
crw-rw---- 1 root tty       7, 133 Sep 16 00:46 vcsa5
crw-rw---- 1 root tty       7, 134 Sep 16 00:46 vcsa6
brw-rw---- 1 root disk    254,   0 Sep 16 00:46 vda
brw-rw---- 1 root disk    254,   1 Sep 16 00:46 vda1
drwxr-xr-x 2 root root          60 Sep 16 00:46 vfio
```
Here we have ```c``` in the first column in ```crw-rw----```, which mean character devices.

#### 10.4 Differentiating between Coldplug and Hotplug Devices

Coldplug device is a device in which you have shutdown you Linux system to plug it in and boot you system back up; the new device is put up. Add a new CPU is a prime example.

Hotplug device is a device that is detected automatically; like a USB key. In order to use hotplug devices, the kernel works together with ```udev``` process.

The kernel and ```udev``` are trying detect devices and they will construct the device configurations at the moment that a hotplug device is detected.

There is a nice command to monitor the activity ```udev```.

```bash
$ cd
$ udevadm monitor
{output results goes here }
```
The above command just starts the monitoring logs. This is just for fun, to see how ```udev``` process works.

This not from the exam but it give you idea how ```udev```
works in the background.

```bash
$ cd /dev
$ ls sd*
sdc sdc1
```
In order to access the device, you need kernel modules. To get a overview, of kernel modules we can issue ```$ lsmod``` this will show all the kernel modules that are currently loaded. A long list of modules are shown.

When a hotplug become active and it detects a new device. In order to initiate the devise, ```udev``` found out which kernel module that is needed. And the kernel modules we need added automatically.

In the case of a coldplug, you may have initalize the kernel modules. In this case, will usw the ```modprobe``` command and you will need to name of the kernel module to load.

Here is dummy example

```bash
$ modprobe vfat
$ modinfo vfat
{output results goes here}
$ lsmod | grep vfat
```

If you load the manually, you must unload it manually as well.

```bash
$ modprobe -r vfat
```

This will remove the kernel module. If the hardware is not in use you can remove it but if it is  you will get a error message below:

```
modprobe: FATAL: Module vfat is in use.
```

#### 10.5 Determining Hardware Resources for Devices

Determining hardware resources for devices involves a couple of commands, basically commands that we've already seen.

```bash
$ lspci
```
This is showing the pci bus and all the devices that are connected pci bus as well. There is a verbose mode that show all the hardware resources that is available on that device.

```bash
$ lspci -v
```

It is showing us what type of network controller that we have. The subsystem tells us what type of controller we have and the physical slot , memory addresses, show the capabilities<access denied> and plus the kernel drivers.

This was ran on a VPS system but need to check out results on other platforms.

```
00:03.0 Ethernet controller: Red Hat, Inc Virtio network device
        Subsystem: Red Hat, Inc Device 0001
        Physical Slot: 3
        Flags: bus master, fast devsel, latency 0, IRQ 10
        I/O ports at c060 [size=32]
        Memory at febf1000 (32-bit, non-prefetchable) [size=4K]
        Memory at fc000000 (64-bit, prefetchable) [size=8M]
        Capabilities: <access denied>
        Kernel driver in use: virtio-pci

```
So if you need to found more information about device ```$ $ lspci -v``` command is used.

```bash
$ lsusb -v
{output results goes here}
```
Same as above.

All this information comes from ```/sys``` directory but you want to stand clear of this directory.

```bash
$ cd /sys
$ ls
block  class  devices   fs          kernel  power
bus    dev    firmware  hypervisor  module
```
This is something that you need to be skilled at this point of learning administrator as Linux system.

By get the ```/sys/devices```, it show another way of showing all the devices that exist. Let check out the pci devices by diving into ```/sys/devices/pci0000:00```. If you like scan particular pci address .

```bash
$ cd /dev
$ ls
block  char
$ cd ../devices
$ ls
LNXSYSTM:00  pci0000:00  pnp0      system      virtual
breakpoint   platform    software  tracepoint
$ cd pci0000:00
$  ls
0000:00:00.0  0000:00:01.2  0000:00:03.0  0000:00:06.0   pci_bus
0000:00:01.0  0000:00:01.3  0000:00:04.0  QEMU0002:00    power
0000:00:01.1  0000:00:02.0  0000:00:05.0  firmware_node  uevent
$ cd 0000\:00\:00.0/
$ ls
```

This gives you the entire device configuration as it been created by ```udev``` and be used by the kernel can be found here, what is pretty nice.

#### Course Summary

  * lspci
  * lsusb
  * /sys
  * /proc
  * /dev


#### 10.6 Tools and Utilities to List Various Hardware Information

#### 10.7 Tools and Utilities to Manipulate USB Devices
```bash
$  ps aux | grep dbus
message+   467  0.0  0.4  42124  3108 ?        Ss   Sep16   0:00 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
cem      16325  0.0  0.1  11132  1028 pts/0    S+   23:52   0:00 grep dbus
$ dmesg
{output results goes here}
```

 display message or driver message - ```dmesg```  is a command on most Unix-like operating systems that prints the message buffer of the kernel. The output of this command typically contains the messages produced by the device drivers.

 With ```dmesg```, we can see if something is happening hardware-wise; often you will see messages logged here. For example, any devices that might have been added

 ```bash
$ tail -f /var/log/messages
 ```

 On most Linux system, by default will this file available. This will give you interesting information on hardware events. If you have a incorrect time server you may get strange time entries in the file as well.

##### Command Summary
  * lsusb
  * usb-devices

#### 10.8 Conceptual Understanding of sysfs, udev, dbus

When managing devices on Linux system, we should have a conceptual understanding ```udev``` and ```sysfs``` (sys filesystem).  

How does this work ?

There is the ```kernel``` and it is responsible for loading devices. Now as an administrator, we need an interface to work with there devices and we an opportunity to determine if the device are created in a particular way.

That is exactly what ```udev``` is doing. ```udev``` is a helper for the ```kernel``` that makes sure  that devices are loaded. To assist the kernel, there are rules. This rules decides how this devices are created.

In order to write the correct information to the right location. There the ```/sys``` file system that contains a ton of information about how devices have been initialize.

```
         (kernel)

          (udev) -------- (rules)
             |
             |
             |
             v
          /sys - file system
```
#### Summary

In this lesson, we learned a little bit about how Linux is managing hardware. The kernel is the central part of the operating system to address hardware and to make that the hardware is available for the kernel. ```udev``` plays an important role, plays a role in loading modules and creating device files and making sure everything is in order the way it should be.

For an administrator perspective, there are the ```ls``` utilities like ```lsblk```, ```lsusb```, ...

These are very nice utilities to show more information about hardware that is attached to your Linux system.

## Lesson 14: Managing Shared Libraries

### Learning objectives

Congratulations, you've made it to the last lesson.

This is a short lesson that explains working with libraries.

In this lesson I'll explain how binaries are used in libraries and what you can do as an administrator if you experience problems while working with libraries.

#### Summary

And this brings us to the end of this short lesson about library management.

You have seen how many programs use libraries, how we have dynamic libraries as well as shared libraries, and you have seen what you can do as an administrator if something goes wrong with regard to the libraries.

And that's all for this lesson, and that brings us to the end of the course.

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
