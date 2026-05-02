# 2. Starting the shell and getting oriented

## 2.1. Starting your terminal session
On Windows, launch the `Ubuntu app`, which will open the `Ubuntu` terminal. On Linux/Mac, open the `Terminal` app.

A new session will start, and the opened window displays a greeting on the first line and a prompt and cursor on the second line (Figure 1). A prompt is a sign on a computer screen that shows that the computer is ready for you to type something. The prompt will probably contain the name of your machine, the name of the current directory ('~', you will learn more on that later) and your username. The command line, as the prompt and cursor are known, is displayed within the terminal window by a program called a **shell**. Shells are customizable and powerful – and at times they can seem frustratingly simple-minded. You can issue short commands or write simple scripts that do amazing things, but you can also wipe out a chunk of your hard disk with a few ill-chosen punctuation marks. The shell assumes that you mean what you say, and rarely gives you the chance to opt out of a command you issue or to undo the results.

There are many different shell programs, but the most widely used is `bash`, which will also be used in the course.

It’s time to try your first command. To check that you are set up to use the bash shell, at the prompt in the open terminal window type the following:

```bash
echo $SHELL
```

The terminal will respond by printing out the name of the active shell, which should be `/bin/bash`. If the active shell is not `bash` but for example `zsh`, which is the default shell on the latest macOS versions, try the following command to make bash the default shell:

```bash
chsh -s /bin/bash
```

![](./images/mbls207_tutorial2_1.png "Figure 1. A portion of the Terminal window in MacOS and Ubuntu (via Windows subsystem for Linux), showing the greeting, prompt and cursor.")
**Figure 1. A portion of the `Terminal` window in MacOS and Ubuntu (via Windows subsystem for Linux), showing the greeting, prompt and cursor.**

## 2.2. Ending your terminal session

To end your session, type `exit`. You can just close the window, but this is a bit like unplugging your computer without turning it off first: if there are any programs still running in the terminal window, they will come unceremoniously to a halt. Closing the window is also not an option when you log in to a different computer from within your terminal.

[Go to module 3](03-Navigating_computer_from_shell.md)
