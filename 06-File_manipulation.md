
## Page 19

# 6. File manipulation II

## 6.1. Viewing file contents with less

There are several commands that display the contents of text files. This is useful when you have a huge file and want to take a quick peek inside, or just view a certain part of a file within the terminal without launching another program. The most commonly used file viewer is less. Typing `less` followed by the path of a file presents the contents of that file on the screen one page at a time. Let's view a protein structure file in less:

```bash
$ less ../examples/structure_1xmz.pdb
```

Table 1 shows the keyboard shortcuts you can use to navigate in less. Try these commands and look around in the file. When you have seen enough, type `q` to quit.

**Table 1. Keyboard commands when viewing a file with less**

<table>
  <thead>
    <tr>
      <th>Key</th>
      <th>Command</th>
      <th>Key</th>
      <th>Command</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>q</td>
      <td>Quit viewing</td>
      <td>↑ or ↓</td>
      <td>Move up or down a line</td>
    </tr>
    <tr>
      <td>[space]</td>
      <td>Next page</td>
      <td>/abc</td>
      <td>Search for text abc</td>
    </tr>
    <tr>
      <td>b</td>
      <td>Back a page</td>
      <td>n</td>
      <td>Find next occurrence of abc</td>
    </tr>
    <tr>
      <td>14g</td>
      <td>Go to line 14</td>
      <td>? + [Enter]</td>
      <td>Find previous occurrence of abc</td>
    </tr>
    <tr>
      <td>G</td>
      <td>Go to end</td>
      <td>h</td>
      <td>Show help for less</td>
    </tr>
  </tbody>
</table>

The program `less` does not load the entire file into memory before showing it to you; it loads only the part it is displaying. So if you have a 500 megabyte dataset and just want to see the very first part of it (perhaps to check that it contains what you think it does, or to figure out the column headers), you are much better off taking a look at it with `less` than you would be opening the entire file in a text editor (which could take some time and bog the entire system down). Later, you will see ways to search inside a file without having to open it.

## 6.2. Viewing help files at the command line with man

Most command-line programs have user manuals already installed on your computer. These explain what the programs do, which arguments they understand, and how these arguments should be entered. These manuals are viewed with the program `man`, which takes an argument consisting of the name of the program you want to see the manual for. So, for instance, `man ls` will display lots of practical information about the `ls` program and the optional arguments it understands.

The `man` program uses the `less` program described above to display the help files, so you navigate within it using the same keys. Try using `man` to investigate some of the options for programs you've already used.

```bash
$ man ls
$ man mv
$ man man
```

&lt;page_number&gt;19&lt;/page_number&gt;

---


## Page 20

6.3. Copying and moving multiple files
Using wildcards, you can quickly copy or move multiple files with names that match a certain pattern. In the following example, all of the files that end with .txt in the examples directory are copied to the sandbox folder:

```
$ ls
$ cp ../examples/*.txt .
$ ls
```

This should give you an intuition of some of the tasks that can be easier by working at the command line rather than in a GUI. Both the copy and move commands, used in conjunction with wildcards, are timesavers when dealing with large numbers of files. For instance, imagine how you gather all your data from a particular species by using the taxonomic name at the beginning and the data format at the end of a path (Nanomia*.dat) while ignoring any similarly named images or documents that might be in that folder.

Wildcards carry the risk of causing problems through unanticipated matches. You especially want to be careful before using wildcards to remove, copy, or move important files; this will help keep you from accidentally modifying files you didn't realize were there. It is often wise to test wildcards with a harmless ls. This will give you a list of files recognized by the command so you can check to see if it includes any that you didn't anticipate.

6.4. Removing files with rm
It is time to clean up the sandbox folder. To do this, we will use the rm command. As already mentioned, this is a very dangerous command. It is possible to delete everything in your home directory (all directories and subdirectories) with rm. Luckily, there is a way of making rm a little bit safer. We can use it with the -i argument, which will ask for confirmation before deleting anything. All the files and directories in the sandbox folder are either empty or copies, so all content can be safely removed. Even though, we are completely certain that everything can be removed, it is good practice to use rm -i.

```
$ pwd # Should be sandbox; if not, go to this directory
$ ls
$ rm -i *
remove Ch30bservations.txt? y
remove Latlon.txt? y
remove Marrus_claudianielis.txt? y
rm: Temp2: is a directory
remove ThalassocalyceData.txt? y
...
$ ls
Temp2
```

If you realize at this point that you were in the wrong directory, relax and hit Ctrl+C to stop the rm command. You can also type n, nothing, or anything that does not start with y or Y if you do not want to remove that particular file.

By default, rm does not remove directories. To remove Temp2, we can either remove all its contents and then remove the empty Temp2 folder, or remove it with the -R argument (recursively) which will be faster. We will do the latter.

&lt;page_number&gt;20&lt;/page_number&gt;

---


## Page 21

text
$ rm -iR Temp2
examine files in directory Temp2? y
remove Temp2/duplicate.txt? y
remove Temp2/reflist.txt? y
examine files in directory Temp2/Temp3? y
remove Temp2/Temp3? y
remove Temp2? Y
$ ls
```

You can, and actually should, use the -i argument when executing a mv or cp command. This will give you a warning when you are about to overwrite a file. For copying directories instead of files you use cp -R.

&lt;page_number&gt;21&lt;/page_number&gt;

---

