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

#### 3.1 Adding, Modifying, and Removing Users

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

#### 3.2 Adding and Modifying Groups


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

To locate or define the available repos, ```cd /etc/yum.repos.d/``` and then ```ls``` You will see a list of files that end will ```.repo```; each entry may contain mirror list that is considered import if that is used if it can connect to the baseurl.

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
