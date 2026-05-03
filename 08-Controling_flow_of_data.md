# 8. Controlling the flow of data

## 8.1. Redirecting output to a file with `>`

There are many times when it is useful to send the output of a program to a file rather than to the screen. Though this might at first sound like a nice but esoteric trick, it adds tremendous flexibility to the way that you can extract and combine data. It also creates the possibility of hooking software together in new ways. This is helpful when an analysis program normally sends its results to the screen, but you want to save the results instead. You could use the GUI's copy and paste functions to copy the results from the screen, but this can't be automated and gets cumbersome for big files or lots of files.

To redirect the output of a program to a file instead of the screen use `>`. You type your command as you normally would, then on the same line add a `>` followed by the name of the file you want to send the output to. Think of `>` as an arrow that is pointing to where the output should go.

If the file doesn't already exist, the redirect will create it. Be careful, however: if a file with the same name does exist, it will be erased and replaced with the program output. It is therefore very easy to accidentally destroy an important document.

To try out redirection, use `ls` to list those files in the examples folder which end in `.seq`:

```bash
$ ls -1 ../examples/*.seq
```

Now, try the same command, but redirect the output to a file called `files.txt` (remember that you can just press `↑` and type the new text from `>` onward):

```bash
$ ls -1 ../examples/*.seq > files.txt

$ ls

files.txt shelltips.txt

$ less files.txt
```

## 8.2. Displaying and joining files with cat

Another useful command is `cat`. It is very simple, taking a list of one or more file names separated by spaces and outputting the contents of these files to the screen. Instead of displaying the contents in a special viewer or editor, as `less` and `nano` do, `cat` dumps them right into the display without a break, in the same manner as the results of many other commands, such as `ls`. Though this may not seem very useful at first, there is a good chance `cat` will become one of your most frequently used commands.

To begin with, `cat` is a convenient tool to view the contents of a short file. For example, `cat files.txt` will output the contents of the `files.txt` file from the previous example. You don't want to view large files with `cat`, as it will take some time for the file contents to scroll by. If your file seems to be scrolling past for too long, press `Ctrl+C` to kill `cat` and get the command line back. This is a useful trick whenever a program stops responding in the terminal.

Take a look at the contents of another example file:

```bash
$ cat ../examples/FEC00001_1.seq
```

As you might expect, this will dump the contents of the file `FEC00001_1.seq` in the examples directory to the screen.

Now, use `cat` to view two files. Notice that there is a space between the paths to the two files:

```bash
$ cat ../examples/FEC00001_1.seq ../examples/FEC00002_1.seq
```

You can see that `cat` just dumps the contents of both files to the screen, one after the other, without any separation of any kind between them. Now, let's look at the contents of all ten of the files at once that end in `.seq`. You could write out the path to each of them, but it is much easier to use a wildcard as we did for `ls`:

```bash
$ cat ../examples/*.seq
```

At this point, it is a simple matter to use cat in combination with a redirect to create a new file that contains all the contents of all the other files, joined end to end:

```bash
$ cat ../examples/*.seq > chaetognath.fasta
```

Combining files with GUI tools can be a tedious and frequently recurring task. This one-line command just saved you from opening ten different files, copying and pasting the contents of each file into a new blank document, and then saving the file you generated. Best of all, this command would have worked just as well for two files or for a hundred. It is an expandable solution that you only need to learn once for projects of any size. The other thing to note is that the command didn't just join all the files in a directory; it looked for only particular files that ended with `.seq`. This specificity was important since there are many other files in the examples directory that we didn't want to combine into `chaetognath.fasta`, and it saved you the added task of sorting through these files.

Notice that all the `.seq` file names have the general format `FEC00001_1.seq`, and that the digit after the underscore is either a 1, 2, or 3. You might want to make a combined file from only the original files that have a 1 in this position. This could be done as follows:

```bash
$ cat ../examples/*1.seq > chaetognath_subset.fasta
```

If you wanted to now add the files with a 2 to `chaetognath_subset.fasta`, you could use a slightly modified redirect which appends to existing files.

```bash
$ cat ../examples/*2.seq >> chaetognath_subset.fasta
```

The `>>` behaves much as `>`, but it appends the redirected content to the end of a file if it already exists rather than replacing the file altogether. If the file doesn't already exist, it creates it just as `>` does, so in most cases you can default to using `>>` and avoid the risk of losing files by accident.

## 8.3. Redirecting output from one program to another with the pipe |

You have already used `>` and `>>` to redirect the output of a program to a file. Using the pipe redirect, it is also possible to redirect the output of one command directly to the input of another, without ever generating a file. The pipe character is the vertical bar ( `|` ) located above the backslash key on your keyboard.

To illustrate this, we will use the command `history`, which displays all your more recent commands line by line. This is a great way to remember what you did or to find a previous command so that you can reuse it. Try it out:

```bash
$ history
```

Sometimes, one would prefer not to fill the screen with a command’s output. One possibility could be to direct the output of a command to a file, just like we did before using `>`. For example, you can generate a text file containing the output of `history` using the following command:

```bash
$ history > history.txt
```

There is another possibility that does not require generating one additional file: the pipe. Here, you use the output of one command as the input for the next command. For example, here you could use the output of history as direct input to the program `less`.
```bash
$ history | less
```

The pipe is a very powerful feature of the shell. You will see more examples below.

[Go to module 9](09-Searches_regex.md)
