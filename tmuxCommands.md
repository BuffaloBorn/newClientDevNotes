
To start off we are in regular shell prompt:
```bash
$ tmux
```

New we are in the tmux server and we can issue the following commands:

```
ctrl -b = is the prefix that you would use to alert tmux that you will like to execute a command
ctrl -b <command>
```
so ```ctrl-b c``` - will create a new window and we will call this window: windowl
At the bottom, we should see the following

```
[OJ O:bash- l:bash*
s2-user@i p-10-126-140' 16:03 13-oct-17
```

where we have ```o:bash``` for window1 and ```1:bash``` for window 2; the reason why it named bash is because that the current shell.
- can change the name of the :bash whatever we like by ```ctrl -b```	and name-window)bash
then type ```window1``` in replace of ```bash``` above

```
[OJ O:bash- l:windowl*
s2-user@i p-10-126-140' 16:07 13-oct-17
```
If we want to switch the current window, to the previous ```ctrl -b p	or next ```ctrl -b n	window.

```[O] O:bash* l:windowl­
s2-user@i p-10-126-140'' 16:10 13-oct-17
```
##### Note: how there a star is moved to the current window's name

If we want to list the current set of windows created: ```ctrl -b w ``` - this give us a scrollable and selectable list of open windows.

Now we going to check out panes in tmux. we can split windows that we are in vertically or horizontally

For vertically we use: ```ctrl -b %```;this make sense because the key does looks like	something being split in half.

To split by vertically we first issue: ```ctrl -b :``` and this allows us to give named commands to ```tmux``` then we type ```split-window```
by default there isn't a key binding for vertical window split.
we can still the previous commands in panes that may multiple windows with init.
If you exit the last windows it will exit out of tmux one of the powerful features of	tmx	is sessions .

we can create a new session by issuing: ```tmx new -s backupsession``` it just like firing up its a named session
Let create another session called ```session00``` we can detach from a named session by issuing: ```ctrl -b d```­

```bash
$ tmux new -s sessionOO
[attached]
```
If we desire to re-attach to the same named session we can issue:	```tmux attach -t session00```

tmx	but we can al so fi re up an application in a session like	vim will be still running in that session.

```bash
tmux attach -t sessionOO
```

and detach the session. And that application


This allows some users to create some very interesting dashboards for networking monitor.
scrolling and buffering in tmux is very powerful for running http dump and pipe it into a file and allow it to running and not lose it in older terminal tools.
We can detach from a named session by issuing: ```ctrl -b & ```
