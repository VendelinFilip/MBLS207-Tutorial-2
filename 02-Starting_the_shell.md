

## Page 3

2. Starting the shell and getting oriented

2.1. Starting your terminal session
On Windows, launch the Ubuntu app, which will open the Ubuntu terminal. On Linux/Mac, open the Terminal app.

A new session will start, and the opened window displays a greeting on the first line and a prompt and cursor on the second line (Figure 1). A prompt is a sign on a computer screen that shows that the computer is ready for you to type something. The prompt will probably contain the name of your machine, the name of the current directory ('~', you will learn more on that later) and your username. The command line, as the prompt and cursor are known, is displayed within the terminal window by a program called a shell. Shells are customizable and powerful – and at times they can seem frustratingly simple-minded. You can issue short commands or write simple scripts that do amazing things, but you can also wipe out a chunk of your hard disk with a few ill-chosen punctuation marks. The shell assumes that you mean what you say, and rarely gives you the chance to opt out of a command you issue or to undo the results.

There are many different shell programs, but the most widely used is bash, which will also be used in the course.

It’s time to try your first command. To check that you are set up to use the bash shell, at the prompt in the open terminal window type the following:
echo $SHELL

The terminal will respond by printing out the name of the active shell, which should be /bin/bash. If the active shell is not bash but for example zsh, which is the default shell on the latest macOS versions, try the following command to make bash the default shell:
chsh -s /bin/bash

&lt;img&gt;A screenshot of a terminal window showing two instances. The top instance is a macOS terminal with the title "Julian — bash — 80x5". The text inside shows "Last login: Thu Nov 22 07:53:35 on console" and "MacBook-Air-van-Julian-2:~ Julian$". The bottom instance is a Windows Subsystem for Linux terminal with the title "juliane@DESKTOP-VCAQEO2: ~". The text inside shows "To run a command as administrator (user "root"), use "sudo <command>". See "man sudo_root" for details." and "juliane@DESKTOP-VCAQEO2: $".&lt;/img&gt;

Figure 1. A portion of the Terminal window in MacOS and Ubuntu (via Windows subsystem for Linux), showing the greeting, prompt and cursor.

&lt;page_number&gt;3&lt;/page_number&gt;

---


## Page 4

2.2. Ending your terminal session
To end your session, type exit. You can just close the window, but this is a bit like unplugging your computer without turning it off first: if there are any programs still running in the terminal window, they will come unceremoniously to a halt. Closing the window is also not an option when you log in to a different computer from within your terminal.

&lt;page_number&gt;4&lt;/page_number&gt;

---

