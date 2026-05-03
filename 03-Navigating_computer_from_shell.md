# 3. Navigating your computer from the shell

## 3.1. Listing files with `ls` and figuring out where you are with `pwd`

As mentioned above, the prompt shows you the directory that is currently your perspective of the **filesystem** from the command line (Figure 2). This is also called the **working directory**. Each time you open a new terminal window, you are logging onto the Unix system of your computer anew. You will be located in what is called your home directory (~). You are now viewing the filesystem from this directory. To specify a different location, we must provide the **path** of that location. A path can be absolute or relative. The **absolute path** is a complete and unambiguous description of where something is in relation to the **root directory** (/), the very base of the filesystem. In contrast, a **relative path** describes where a folder or file is in relation to our working directory.

The first command you will learn, and one you’ll use frequently, is `ls` (short for **l**i**s**t). It prints out a list of files and directories contained within the working directory, or a specified directory.

![](../images/mbls207_tutorial2_2.png "Figure 2. A portion of the Unix filesystem structure in tree format. Folders (also called directories) are in green, files (also called documents) are in maroon, and Unix programs (also called commands) are in grey. The root directory is on the far left.")
**Figure 2. A portion of the Unix filesystem structure in tree format.** Folders (also called directories) are in green, files (also called documents) are in maroon, and Unix programs (also called commands) are in grey. The root directory is on the far left.

<details>
<summary><strong>MacOS and Linux</strong></summary>

For comparison, open Finder (Mac) or the Linux equivalent and navigate to your home folder (Mac: `Go` → `Home` or `Shift+⌘+H` keyboard shortcut), so you can see its content. Now do the same by typing the command ls in your terminal window and compare the output with what you see in the familiar `Finder`. You should see the same folders and files in both. If you have set your computer to a different language than English, you will see the translated names in the GUI, but not in the terminal.

In the following examples, in place of `lucy` you’ll see your own username, and you will also see a different host name at the beginning of the line. This is your network identity, created when you first set up an account on your computer.

To see the contents of the `Desktop` folder while sitting in your home directory, type:

```bash
host:~ lucy$ ls Desktop
```

or with the default Linux prompt:

```bash
lucy@host:~$ ls Desktop
```

From now on the Linux prompt will only be shown too if the command is different. Without anything before `Desktop`, `ls` expects that `Desktop` is a directory within the working directory. This is a relative path to `Desktop`, because it is in relation to where you are now. Upon executing the command, you should see a list of whatever files are stored on your `Desktop` at the moment.

To see the absolute path of the working directory, use the command `pwd` (`p`rint `w`orking `d`irectory):

```bash
host:~ lucy$ pwd

/Users/lucy
```

</details>

<details>
<summary><strong>Windows</strong></summary>

<details>
<summary><strong>Windows 10</strong></summary>

If you are using WSL or Cygwin, the root directory in the terminal is in a somewhat odd place compared with the filesystem. The root directory corresponds to a Windows directory deeply hidden somewhere in `C:\Users\<username>\AppData\...` for WSL and `C:\cygwin` for Cygwin. Conversely, the Windows root directory `C:\` is available from the shell environment as `/mnt/c` (WSL) or `/cygdrive/c` (Cygwin).

</details>

<details>
<summary><strong>Windows 11</strong></summary>
  
In the newest Windows version, the root directory of the terminal is shown in the filesystem (File Explorer) as a separate folder (Linux).

</details>

In the following examples, in place of `lucy` you’ll see your own username, and you will also see a different host name at the beginning of the line. This is your network identity, created when you first set up an account on your computer. 

Type the command `ls` in your terminal window and you will see that there is not much to see in the Ubuntu or Cygwin home directory yet. We will copy the example files to here later on.

```bash
lucy@host:~$ ls
```

With the Cygwin prompt it will look like this:

```bash
lucy@host ~

$ ls
```

From now on the Cygwin prompt will only be shown if the command is different.

To see the absolute path of the working directory, use the command `pwd` (`p`rint `w`orking `d`irectory):

```bash
lucy@host:~$ pwd

/home/lucy
```

Since you haven’t moved anywhere since starting the shell, you are seeing the absolute path of your home directory. To see the contents of another directory than the working directory you provide the path to that directory behind the ls command. For comparison, open File Explorer and navigate to your `Documents` folder, so you can see its content. Now do the same by typing the following command in your terminal window and compare the output with what you see in the familiar `File Explorer`. You should see the same folders and files in both. Note that instead of `lucy` you should fill in your **Windows** username. This can be seen in `File Explorer` by checking the content of the directory `C:\Users`.

```bash
lucy@host:~$ ls /mnt/c/Users/lucy/Documents
```

or with Cygwin:

```bash
lucy@host ~

$ ls /cygdrive/c/Users/lucy/Documents
```

</details>

## 3.2. How to move around with `cd`

<details>
<summary><strong>MacOS and Linux</strong></summary>
  
To move to another directory, use the command `cd` (change directory). Move inside your Desktop directory by typing

```bash
host:~ lucy$ cd Desktop

host:Desktop lucy$
```

Notice that the prompt changes from `host:~ lucy$` to `host:Desktop lucy$`, showing the name of the new working directory. On a Linux system the path component of the prompt will be expanded, showing the complete path.

You will need to keep in mind that capitalization generally counts in all types of Unix. Getting the capitalization of a command wrong can be as bad as misspelling it. This capitalization behaviour is hard to predict, though, so you should not rely on it to distinguish similarly named files.

To see the contents of the `Desktop` directory, but this time from within the directory, you can now type `ls` by itself:

```bash
host:Desktop lucy$ ls
```

From here, if you type `ls Desktop`, you will generate an error, because there is no `Desktop` folder within your `Desktop` folder (unless you have created one).

```bash
host:Desktop lucy$ ls Desktop

ls: Desktop: No such file or directory
```

The same error happens when you try this, but for a different reason:

```bash
host:Desktop lucy$ ls /Desktop

ls: /Desktop: No such file or directory
```

To move back towards the root in the directory structure (see Figure 2), more specifically to the parent directory of the working directory, use the command:

```bash
host:Desktop lucy$ cd ..
```

Make sure to include a space between the `cd` and the two dots. This command won’t return any feedback after the prompt. However, since the prompt by default shows a shortened version of your current working directory, it will again change your new location.

The two dots in the command indicate the folder that contains the current folder. This is just another type of relative path. This will always move you from the current working directory to the directory which contains it – unless, of course, you are in the root directory, which is absolute and contained by nothing.

The `..` symbol can be used in conjunction with other directory names. This allows you to move with a single command from one directory to another that is sister to it in the hierarchy. For example, if you want to go from your `Desktop` directory to your `Documents` folder, this is equivalent to backing out one level and then moving one level into a different but parallel directory relative to where you started (see Figure 2). First, go back to the `Desktop` folder and then go in one command to the `Documents` folder:

```bash
host:~ lucy$ cd Desktop

host:Desktop lucy$ pwd

/Users/lucy/Desktop

host:Desktop lucy$ cd ../Documents

host:Documents lucy$ pwd

/Users/lucy/Documents
```

From `Documents` you can type `cd ..` to go back to the home directory again. Note that you can use `..` more than once in a command. For example, `cd ../..` will send you back two directories in one step.

```bash
host:Documents lucy$ cd ..

host:~ lucy$ pwd

/Users/lucy

host:~ lucy$ cd ../..

host:/ lucy$ pwd
/
```

</details>

<details>
<summary><strong>Windows</strong></summary>
  
To move to another directory, use the command `cd` (change directory). Move inside your Windows home directory by typing:

```bash
lucy@host:~$ cd /mnt/c/Users/lucy

lucy@host:/mnt/c/Users/lucy$
```

or

```bash
lucy@host ~

$ cd /cygdrive/c/Users/lucy

lucy@host /cygdrive/c/Users/lucy
$
```

Notice that the prompt changes from `lucy@host:~$` to `lucy@host:/mnt/c/Users/lucy$`, showing the name of the new working directory.

You will need to keep in mind that capitalization generally counts in all types of Unix. Getting the capitalization of a command wrong can be as bad as misspelling it. This capitalization behaviour is hard to predict, though, so you should not rely on it to distinguish similarly named files.

To see the contents of the `Desktop` folder while sitting in your home directory, type:

```bash
lucy@host:/mnt/c/Users/lucy$ ls Desktop
```

Without anything before `Desktop`, `ls` expects that `Desktop` is a directory within the working directory. This is a relative path to `Desktop`, because it is in relation to where you are now. Upon executing the command, you should see a list of whatever files are stored on your `Desktop` at the moment.

Because `Desktop` is a folder within your Windows home directory, and the absolute path to your Windows home directory is `/mnt/c/Users/lucy`, you could also list its contents with:

```bash
lucy@host:/mnt/c/Users/lucy$ ls /mnt/c/Users/lucy/Desktop
```

This command has the exact same results as the previous `ls Desktop` because it is showing the contents of the same folder, just specified in two different ways.

Move inside your `Desktop` directory by typing

```bash
lucy@host:/mnt/c/Users/lucy$ cd Desktop
```

To see the contents of the `Desktop` directory, but this time from within the directory, you can now type `ls` by itself:

```bash
lucy@host:/mnt/c/Users/lucy/Desktop$ ls
```

From here, if you type `ls Desktop`, you will generate an error, because there is no `Desktop` folder within your Desktop folder (unless you have created one).

```bash
lucy@host:/mnt/c/Users/lucy/Desktop$ ls Desktop

ls: Desktop: No such file or directory
```

The same error happens when you try this, but for a different reason:

```bash
lucy@host:/mnt/c/Users/lucy/Desktop$ ls /Desktop

ls: /Desktop: No such file or directory
```

To move back towards the root in the directory structure (see Figure 2), more specifically to the parent directory of the working directory, use the command:

```bash
lucy@host:/mnt/c/Users/lucy/Desktop$ cd ..
```

Make sure to include a space between the `cd` and the two dots. This command won’t return any feedback after the prompt. However, since the prompt by default shows a shortened version of your current working directory, it will again change your new location. 

The two dots in the command indicate the folder that contains the current folder. This is just another type of relative path. This will always move you from the current working directory to the directory which contains it – unless, of course, you are in the root directory, which is absolute and contained by nothing.

The `..` symbol can be used in conjunction with other directory names. This allows you to move with a single command from one directory to another that is sister to it in the hierarchy. For example, if you want to go from your `Desktop` directory to your `Downloads` folder, this is equivalent to backing out one level and then moving one level into a different but parallel directory relative to where you started (see Figure 2).

First, go back to the `Desktop` folder and then go in one command to the `Downloads` folder:

```bash
lucy@host:/mnt/c/Users/lucy$ cd Desktop

lucy@host:/mnt/c/Users/lucy/Desktop$ cd ../Downloads

lucy@host:/mnt/c/Users/lucy/Downloads$
```

From `Downloads` you can type `cd ..` to go back to the home directory again. Note that you can use `..` more than once in a command. For example, `cd ../..` will send you back two directories in one step.

```bash
lucy@host:/mnt/c/Users/lucy/Downloads$ cd ..

lucy@host:/mnt/c/Users/lucy$ cd ../..

lucy@host:/mnt/c$ cd ../..

lucy@host:/ $
```

</details>

## 3.3. Signifying the home directory with ~
A shortcut for referring to your home directory is the tilde symbol (~). This is also shown in the prompt, when you are in your home directory. So, for instance, no matter where you are on the system, you can type the following command to jump straight to the Documents folder in your home directory (this of course only works if you have a Documents directory there, so it won’t work for Windows users; be patient, we’ll add some files in your Ubuntu home directory later on):

```bash
host:/ lucy$ cd ~/Documents
```

This is equivalent to typing the absolute path, specified all the way from root:
```bash
host:Documents lucy$ cd /Users/lucy/Documents
```

See what happens when you try the following commands (use the pwd command after each one to confirm the results):

```bash
$ cd /

$ cd ~

$ cd /

$ cd
```

You should find that `cd` and `cd ~` do the same thing, i.e., they take you back to your home directory. Typing `cd` is a very quick way to get there.

[Go to module 4](04-Basic_manipulation.md)
