
## Page 15

# 5. Powering up: shortcuts and options

## 5.1. Command line shortcuts

### 5.1.1. Up arrow

It is not too soon to introduce two shell shortcuts that will save you a lot of typing. Try to get into the habit of using these, because they will not only save you time, but will also reduce the number of typographical errors you have to correct.

The first shortcut is the ↑ key. In most shells, the ↑ moves back through your previous command history. For example, if you type in a long command and hit Enter, only to realize that you were in the wrong directory for the command to do what you wish, you can easily move to the correct directory, press ↑ one or more times until you see the correct command, and then hit Enter again to execute the command. Try pressing the ↑ key now to step back through and see all the commands that you have done so far. Pressing the ↓ key will get you back to more recent commands and even show future commands that you haven't typed yet.

Previous commands can also be edited before you re-execute them. If you enter a command but it has a typo somewhere in it, press ↑ to show it again, then use the ← and → keys to move to the place where the error occurred, fix it and hit Enter. The cursor doesn't have to be back at the end of line.

When typing or editing a command, you can use Ctrl+A to go directly to the start of the line, Ctrl+E to go to the end, Ctrl+←/→ or \+←/→ to go to the previous/next word, Ctrl+W to delete the word left of the cursor, Ctrl+U to delete everything left of the cursor and Ctrl+K to delete everything right of the cursor. Try these shortcuts with one of your previous commands. If you are in the middle of a command and wish to start over, typing Ctrl+C will clear the line. This key sequence is a universal way to interrupt a program or process.

### 5.1.2. Tab

Another big time-saver is the tab key. This is in effect the auto-completion button for the command line. For example, go to the parent pcfb directory and start typing:

```
$ cd sand
```

Then, press tab. The command line should fill in the remainder of the word sandbox and append a trailing slash. Now try this command:

```
$ cd s[tab]
```

You should get a beep or a blank stare from your terminal. This is because there is more than one folder starting with s in the pcfb directory. The shell can't tell if you are referring to the sandbox, or the scripts folder. To see what the choices are, press tab again. The terminal will return a list of the matches to what you have typed so far. If nothing shows up, check where you are and check for incorrect other characters at the beginning, to make sure you haven't entered the start of a path that doesn't exist.

Completion of directory and filenames is especially convenient when the name has a space in it. If you try to type a command with a space in it, such as cd My Project, the shell

&lt;page_number&gt;15&lt;/page_number&gt;

---


## Page 16

thinks that there are two different pieces of information (arguments) being sent to the cd command. Since you probably don't have a directory called My, it returns an error.

When you use tab auto-completion in his context, the shell types the command with extra backslashes inserted before the spaces. Remember from the previous tutorial on searching and replacing with regular expressions that a backslash (\) modifies the interpretation of the character that follows. In this case, it causes the shell to interpret the space as part of the filename rather than as the separation between two filenames. You don't need auto-completion to take advantage of \. You can also type it in yourself as part of the path.

Spaces can also be accommodated in file or directory names by using either single or double quotes to enclose the full path, including spaces. However, you cannot do so if you are trying to use the tilde shortcut or wildcards (discussed later) as part of the path, since they won't be expanded.

It is generally best to just AvoidUsingSpacesAltogether when naming data files and scripts. This will make things easier later on. Other punctuation marks in names (?, ;, /) have special meanings at the command line, and should therefore be avoided as well. Underscores are acceptable to use.

## 5.2. Wildcards in path descriptions

So far you have not done much that you could not have accomplished just as easily (or maybe more easily) with a graphical user interface. It is **wildcards** that makes the command line more powerful than a GUI for processing many files in one operation.

For example, to list all the files and folders that begin with s in the pcfb directory, as well as the contents of those directories, you could type:
```bash
$ ls ../s*
```

To list just files ending in .txt, you could type:
```bash
$ ls ../examples/*.txt
```

You can use several wildcards in the path. So to list all files and directories that start with a c within all directories that you have installed from the book, you can type:
```bash
$ ls ../*/c*
```

<table>
  <thead>
    <tr>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>../examples/chart.html</td>
      <td>../examples/ctd.txt</td>
    </tr>
    <tr>
      <td>../examples/chart.php</td>
      <td>../examples/ctd237e6.asc</td>
    </tr>
    <tr>
      <td>../examples/chart0.php</td>
      <td>../examples/curlexamples.txt</td>
    </tr>
    <tr>
      <td>../examples/chartform.php</td>
      <td>../scripts/compositioncalc1.py</td>
    </tr>
    <tr>
      <td>../examples/ctd.rtf</td>
      <td>../scripts/compositioncalc2.py</td>
    </tr>
  </tbody>
</table>

<table>
  <thead>
    <tr>
      <th colspan="3">../examples/ctd:</th>
    </tr>
    <tr>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Marrus_ctdTib515.txt</td>
      <td>Marrus_ctdVen1777.txt</td>
      <td>o_ctdTib626.txt</td>
    </tr>
    <tr>
      <td>Marrus_ctdTib531.txt</td>
      <td>Marrus_ctdVen2243.txt</td>
      <td>o_ctdTib834.txt</td>
    </tr>
    <tr>
      <td>Marrus_ctdTib547.txt</td>
      <td>midwater.sql</td>
      <td>o_ctdTib965.txt</td>
    </tr>
    <tr>
      <td>Marrus_ctdTib596.txt</td>
      <td>midwater2.sql</td>
      <td>o_ctdTib985.txt</td>
    </tr>
    <tr>
      <td>Marrus_ctdVen1575.txt</td>
      <td>o_ctdTib598.txt</td>
      <td>o_ctdTib989.txt</td>
    </tr>
  </tbody>
</table>

&lt;page_number&gt;16&lt;/page_number&gt;

---


## Page 17

Notice that the asterisk doesn't include text beyond the path divider (/). Therefore, `ls ../*c*` is not equivalent to the command above. In fact, it will show the content of the scripts directory.

When using wildcards, if `ls` finds a file that matches, it lists the filename; if it finds a directory that matches, it lists the directory along with its contents.

Another wildcard is the question mark. Try to figure out its meaning:
```bash
$ touch fat fit feet
$ ls f*t
$ ls f?t
$ ls f??t
```

### 5.3. Modifying command behaviour with arguments

All of the commands we've discussed so far, such as `ls`, `cd`, and `pwd`, are actually little programs that are run by the shell. The programs each read in bits of information and do something as a result. Pieces of information that are passed to a program at the command line are called **arguments**. Each argument is generally separated from the program name and any other arguments by a space, but beyond that there aren't any global rules for how programs receive and interpret arguments. You've already used arguments, such as when you told `cd` which directory to change to, or when you told the `mkdir` program what directory to create. Some programs interpret arguments in a particular order, while others allow arguments to be in any sequence.

Beside a path name, the `ls` command has many optional arguments; in format, these consist of a hyphen followed by a letter. Two of the most commonly used arguments or options are `-a` and `-l`. Consider `-a` first. Some files and folders on the system, those whose names begin with a period, are normally hidden from view. To tell the `ls` command to show all files, including those that are hidden, type `ls -a` (meaning list all). Try this to show all the content of your home directory, and you will notice some of the hidden files that show up, for example the `.Trash` directory.

You can also tell `ls` to return a more detailed list of directory contents with the `-l` (lowercase L) argument. This prints a list that includes, in columns from left to right, the file or directory permissions; the number of items in the folder, including hidden items; the owner; the group; the file size; the modification date; and the file or directory name. We won't talk about permissions until later, but much of this information will eventually prove useful or necessary as you progress:
```bash
$ pwd # Should still be in the sandbox folder...
$ ls -l
total 0
drwxr-xr-x 6 User staff 204 14 aug 11:45 Temp2/
-rw-r--r-- 1 User staff 0 14 aug 10:59 original.txt
```

Note that everything that is written after a number sign (`#`) is not interpreted by the shell.

&lt;page_number&gt;17&lt;/page_number&gt;

---


## Page 18

If you would like to both see a detailed view and all the hidden files, at the same time, use both arguments in the same command:
```bash
$ ls -l -a ~/
```
This shows a detailed view that includes all the hidden files in your home folder. With many programs, you can combine arguments using one dash followed by the arguments together with no spaces; thus `ls -la ~/` is equivalent to the command above. The order of the arguments for `ls` isn't critical either, so `ls -al ~/` is also equivalent. See Appendix 3 of *Practical Computing for Biologists* for a more complete list of options.

&lt;page_number&gt;18&lt;/page_number&gt;

---

