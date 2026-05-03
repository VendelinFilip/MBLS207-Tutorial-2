# 7. Handling text in the shell

<details>
<summary><strong>Windows</strong></summary>

To play around with the example folders and files, the easiest way is having these files in your Ubuntu/Cygwin home directory as well. We can copy them to this directory. Assuming you are already in the Ubuntu/Cygwin home directory and the pcfb folder is in your Windows home directory, the command is:

```bash
$ cp -iR /mnt/c/Users/lucy/pcfb .
```
</details>

### Editing text files at the command line with nano
It is sometimes convenient to create or modify a file right at the command line. Moreover, if you work on a remote machine, the only way to directly modify a file may be through a command-line editor.

Although less, which you learned about it in the previous chapter, is a convenient command-line viewer for text files, it does not allow you to edit the contents of a file. For that, you will need one of the many command-line text editors available. For starting out, we will use nano, a widely available, general-purpose command-line text editor. It displays the options in a menu-like array at the bottom of the screen.

If you call nano without any arguments it will create a new blank file. Open the terminal and move to the sandbox folder and start a blank document:
```bash
$ cd pcfb/sandbox
$ nano
```

Enter some text into the blank document:
Helpful shell commands

Along the bottom of the window, though, you will see a series of characters, each preceded by a caret (^), and each followed by a short description of a corresponding function (Figure 3). The caret corresponds to the Ctrl key. Hit Ctrl+O, save the file as shelltips.txt and exit nano with Ctrl+X. Listing the directory contents with ls will show the shelltips.txt file you just created, and less shelltips.txt will let you view the file's contents. Open it again with nano, this time specifying the filename:
```bash
$ ls
shelltips.txt
$ less shelltips.txt
$ nano shelltips.txt
```

and close nano again.

&lt;page_number&gt;22&lt;/page_number&gt;

---


## Page 23

&lt;img&gt;Terminal window showing GNU nano 2.0.1 with text "Helpful shell commands" and a list of commands at the bottom.&lt;/img&gt;
Figure 3. A view of the command-line text editor nano with the text you entered. Some of the available commands are displayed at the bottom of the window.

---

