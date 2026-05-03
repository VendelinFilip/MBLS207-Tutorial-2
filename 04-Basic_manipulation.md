# 4. Basic manipulation of folders and files

## 4.1. Adding and removing directories with mkdir and rmdir

So far, we’ve discussed moving around the filesystem, but you have been a fly on the wall and have not actually done anything to affect the filesystem in your travels. One basic modification you can make to your filesystem is to add a directory – a task accomplished with the command `mkdir` (`m`a`k`e `dir`ectory).

The following sequence of commands will make a folder called `test` in the `sandbox` folder you installed along with the `examples` folder. While you do these operations, it is illustrative to have a graphical browser window open in `Finder` or `File Explorer` with the contents of the `pcfb/sandbox` folder showing. Go to the same directory in the terminal. You should have placed the `pcfb` folder in your home directory (note that it therefore will be in `/mnt/c/Users/lucy/pcfb/sandbox` or `/cygdrive/c/Users/lucy/pcfb/sandbox` for Windows users). The ls commands give a before and after view of the changes resulting from `mkdir`:

```bash
host:sandbox lucy$ ls

host:sandbox lucy$ mkdir test

host:sandbox lucy$ ls

test

host:sandbox lucy$ cd test

host:test lucy$ ls

host:test lucy$ cd ..

host:sandbox lucy$ ls

test
```

After the `mkdir` command is issued, you find a new directory has been created called test. If you look at your sandbox folder using the `Finder / File Explorer` (remember that GUI you used to use?) you should also see it there, represented by a new folder of the same name. In the last few commands, you simply moved into the new directory, looked around (there was nothing there to see since you hadn’t put any files in it), and moved back out. Next you get rid of the empty directory with the command `rmdir` (`r`e`m`ove `dir`ectory):

```bash
host:sandbox lucy$ rmdir test

host:sandbox lucy$ ls
```

**Warning**

You can see that test is now gone. By default, `rmdir` is conservative in that it only removes empty directories. The equivalent to `rmdir` for deleting files is `rm`. Use caution with `rmdir` and even more so with `rm`. These commands are not like putting something in the `Trash`, where you can pull it out later. Files deleted this way are gone and cannot be recovered. We will explore `rm` later after we have built in a check to prevent accidents.

## 4.2. Creating and copying files: `touch` and `cp`

The following sections will deal with commands that help us to work with files, i.e., copy files to/from places, move files, rename files, remove files, and most importantly, look at files. First, we need to have some files to play with. The command `touch` will let us create a new, empty file. The `touch` command does other things too, but for now we just want a file to work with. If you still have the GUI open, you will see a new file appear.

```bash
host:sandbox lucy$ touch original.txt

host:sandbox lucy$ ls

original.txt
```

The command to copy a file is `cp` (copy). It is followed by the file’s present name and location (known as the source) and the location where you would like the copy to end up (known as the destination). In the following example, the source is the file we’ve just created and the destination is an identical file but with a different name:

```bash
host:sandbox lucy$ cp original.txt duplicate.txt

host:sandbox lucy$ ls

duplicate.txt original.txt
```

You can use `cp` to copy a file within the same directory, giving the new file a new name, as we just did. You can also copy a file to another directory, either giving it a new name or retaining the old name. If you only specify a path to a directory for the destination, without an actual filename, then the file will be copied to that directory with its original name.

Remember that the command option consisting of two periods (`..`) refers to the directory that contains the current working directory. Similarly, a single period (`.`) represents the current working directory itself, which is useful if you want to copy a file from elsewhere to the working directory. Let’s copy a file from the examples folder to the sandbox folder.

```bash
$ cp ../examples/reflist.txt .

$ ls

duplicate.txt original.txt reflist.txt
```

When moving or copying a file, by default the shell will not warn you if a file or folder of the same name exists in the destination directory. If a file of the same name does exist, it will get “clobbered” – that is, deleted and replaced without warning or notification. You may not realize this until much later when you go looking for the original file. Later, you will see how to modify this behaviour.

### 4.3. Moving files: `mv`

The command for moving files is `mv` (move). You move files in the exact same way that you copy them, except that the original file disappears in the process. In the following example, you move the reflist.txt file to a new directory:

```bash
$ mkdir Temp

$ mv reflist.txt Temp

$ ls

Temp

$ ls Temp

duplicate.txt original.txt

$ reflist.txt
```

The command `mv` is also used for renaming files, since renaming a file is equivalent to moving it to a new file with a different name in the same directory.

```bash
$ mv duplicate.txt duplicate_renamed.txt

$ ls

Temp

duplicate_renamed.txt original.txt

$ mv duplicate_renamed.txt Temp/duplicate.txt

$ mv Temp Temp2

$ mkdir Temp3

$ mv Temp3 Temp2

$ ls

Temp2 original.txt

$ ls Temp2

Temp3 duplicate.txt reflist.txt
```

You will see that with one command you can also both rename and move a file and that you can use `mv` also on folders. Note the difference in outcome between the `mv Temp Temp2` and `mv Temp3 Temp2` commands. Later, you will see how to quickly move or copy multiple files at once.

[Go to module 5](05-Powering_up.md)
