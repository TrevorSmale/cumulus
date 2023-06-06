---
title: "Beginner Boost"
date: 2023-05-29T18:31:10-04:00
draft: false
---

{{< panel title="Update Log" style="success" >}}

* 2023 06 05 - Initial Commit

{{< /panel >}}


{{< panel title="Extracted Content" style="danger" >}}

This is material extracted from [Skilstak.io](Skilstak Page) Interspersed with my own notes as the course progresses

{{< /panel >}}

# 2023 Boost overview

Here's what we currently plan to cover over approximately 32 weeks in 2023 with an estimated completion date sometime in December based on two hours per week 

* Become an autodidact: learn to manage your own learning. (1h)
* Take efficient, searchable notes with Markdown on GitHub. (1h)
* Grok benefit and origin of terminal command-line interface. (1h)
* Install and use bash shell on Windows and Mac (besides Linux). (1h)
* Know why Ubuntu, RedHat, and Alpine are most relevant Linux distros. (20m)
* Run Linux container(s) on Windows or Mac with podman. (1h)
* Use search-centric system navigation on Windows, Mac, or Linux. (20m)
* Get help for any Linux command without the Internet. (20m)
* Use tab-completion to speed command line input. (20m)
* Navigate Linux file system and understand general organization. (2h)
* Capture, append, and connect command input, output, and errors. (1h)
* Run commands on multiple files using wildcard globbing. (1h)
* Search and filter text input and files with regular expressions. (2h)
* Edit text files in-place from the command line. (1h)
* Edit text files visually using terminal editor apps. (2h)
* Manage running application processes. (1h)
* Manage terminal windows with screen/tmux. (1h)
* Leverage command history to save time. (20m)
* Do effective research from command line with lynx or w3m. (1h)
* Understand and manipulate Linux file ownership and permissions. (1h)
* Find specific files anywhere and determine what they are. (1h)
* Understand how Internet networking generally works. (2h)
* Use secure shell to safely interact with remote systems. (1h)
* Save source to GitHub with git and gh. (1h)
* Organize commands and start your own "dot files" GitHub repo. (1h)
* Commit working Linux container as image to GitHub registry. (1h)
* Write safe shell scripts in bash and ash with shellcheck. (1h)
* Grok and apply everything in the bash manual page (man bash). (4h)
* Doing math safely and reliably with bc and dc. (2h)
* Understand ASCII, terminal encoding, and escape sequences. (1h)
* Follow UNIX philosophies and use UNIX filters over plugins. (1h)
* Work with structured data in JSON, YAML, and delimited formats. (2h)
* Do things as administrator (root) but only when necessary. (1h)
* Install, and update software packages with apt. (1h)
* Start your own custom Linux container image from scratch. (1h)
* Customize bash profile and environment. (1h)
* Customize ed/ex/vi/vim configuration. (1h)
* Customize TMUX configuration. (1h)
* Customize lynx configuration. (1h)
* Try coding in Python, C, and Go from CLI. (8h)
* Create and maintain a consumable, sustainable resume. (2h)
* Complete GitHub profile page and grok job discovery from GitHub. (1h)
* Learn just enough Web development to create a personal page/blog. (2h)
* Network and foster a professional learning network/community. (1h)
* Know when and how to certify and get a good starting Linux job. (1h)
* Set healthy work boundaries and self-care habits. (1h)
* Pay it forward! (1h)

* How to install Linux on hardware.
* How to use Linux graphic user interfaces, desktops, and window managers.

# 2023 Boost - Week 1

📺 <https://youtu.be/cE-kkVwz0Xg>

This week we start taking notes in basic Markdown on GitHub and connect with others doing the Boost. Then we go over the core applications that must be installed next week: bash shell, a good terminal, and Podman desktop.

1. Create a GitHub account
    1. Pick a good, short, memorable name suitable for work
    2. Find and follow some other friends from Boost
    3. Create a private repo to contain notes from Boost with README.md
2. Learn basic Markdown
    1. Focus on one best way for consistency
    2. Practice using your new README.md in repo of notes
    3. Started taking notes from GitHub GUI
3. Install bash
    1. Install git-bash on Windows
    2. Install brew and then brew install bash on mac
4. Install a better terminal application
    1. Install Windows Terminal Preview on Windows
    2. Install iTerm2 on Mac
    3. Customize themes and colors to your preferences
    4. Perhaps install and explore VSCode a bit to see as well
5. Install Podman Desktop (with WSL2 extension if prompted)
    1. Start exploring `podman` command from terminal

# 2023 Boost - Week 2

📺 <https://youtu.be/0gNR6qj87a0>

This week we learn about terminal and command line interfaces, containers and virtual machines and start using Podman Desktop and podman command for the first time.

1. Use command search to open a bash terminal (in full screen if prefer)
2. What's a **command line**? **Shell**?
    1. What's a **prompt**?
        1. Why simple prompts are best?
    2. What's a **command**?
    3. What is a REPL?
    4. What's an **argument**?
    5. What is a **switch**, **flag**, and/or  **option**?
    6. Difference between "terminal" and "command line"
3. What's a **file system**? **Directory**?
    1. Rooted node tree **data structure**
    2. "Everything is a file in UNIX/Linux" (inode specifically)
4. Learn bash shell navigation?
    1. `exit` - exit the current shell
    2. `pwd` - print working directory (show where you are)
    3. `clear` - clear the screen
    4. `ls` - list files and directories
        1. Current directory
        2. Parent directories
        3. Sub-directories
        4. Globing
    5. `cd` - change directory
    6. `which` - see which command will be run (if available)
    7. How can I find help? `-h`, `man`, `info`, `help`, `apropos`, `whatis`
5. What's a container?
    1. ... compared to a *virtual machine*?
6. Create hub.docker.io and/or quay.io account (if needed)
7. Start Podman Desktop GUI
    1. Pull an image
    2. Start a container
    3. Open a terminal to the container
    4. Understand equivalents from a command line
8. Run a new temporary container with `podman` command
    1. `ubuntu`
    2. `busybox`
    3. `alpine`
    4. `archlinux`
    5. `kalilinux/kali-rolling`
    6. `redhat/ubi8-minimal`
    7. `gentoo/stage3`

# 2023 Boost - Week 3

📺 <https://youtu.be/mUmQk1o6FFs>

(PLEASE SKIP TO WEEK 4.) This week we setup an Ubuntu Linux container image using podman command and apt package manager, learn how to save (commit) an image copy so we have backups during our setup, and how to navigate the command line.

1.  Why Ubuntu?
2.  Pull an Ubuntu Linux image into podman images
3.  Create (run) a named container from the Ubuntu local image
4.  Exit the container
5.  Understand difference between running and exited containers
6.  Use –rm for temporary containers
7.  Use podman ps -a to show all containers (running and exited)
8.  Use podman rm to remove unwanted containers
9.  Use bash tab completion to save on typing
10. Use up and down arrows (for now) to get previous commands
11. Restart and attach to named container
12. Use Advanced Package Manager (APT)
13. Use `apt update` command to refresh list of packages
14. Clear the screen with clear command (not control-L)
15. Install documentation helpers
16. Use man to get help about commands
17. Use help to get help about bash builtins
18. Look for runnable stuff
    1.  Use which command
    2.  Use type builtin
    3.  Use command -v command
    4.  Use file command to see what type of thing it is
19. Everything is a file (inode) even directories
    1.  Use ls command
    2.  Use pwd command
    3.  Use cd to change directories
    4.  Use chmod to change permissions
    5.  Use chown to change owner (and group)
20. Add new user with adduser (or useradd)
21. Delete user with deluser (or userdel)
22. Add new group with addgroup (or groupadd)
23. Delete group with delgroup (or groupdel)
24. Commit (save) container as image
25. Push saved image to GitHub Container Registry
    1.  Create Personal Access Token on GitHub
    2.  Use podman push to push local image to remote ghcr.io
    3.  View saved GitHub packages (containers)

# 2023 Boost - Week 4

📺 <https://youtu.be/SPoqW1CMEhY>

Let's do this again. Weeks 2 and 3 were a little harder than most beginners might be able to handle. Most Linux users will be using a Linux that has been installed already. The Boost is primarily intended for *them* (not admins and hackers, who are also users). So we've prepared a quick-start with an existing Linux container image. Here's how to get it and another take at how to get going without having to setup anything.

1. What concepts do all *users* need to understand?
1. What does it mean to be a Linux "user" (vs "admin" or "hacker")?
1. Create a local Linux container for the Boost

    ```sh
    podman run -it --hostname skilstak --name boost -v shared://shared ghcr.io/rwxrob/ws-skilstak
    ```

1. What is the difference between a terminal and a command line?
1. What do the parts of the prompt mean?
1. How do I clear the screen?
    * Do not depend on Control-L
    * `clear` (or `c`)
1. How do I see where I am?
    * `pwd`
1. How do I see everything in this directory?
    * `ls -al`
1. How do get help information about a command?
    * `CMD -h` or `CMD --help`
    * `man CMD`
    * `help CMD`
    * `apropos KEYWORD` (if you want)
1. What is a directory and what is a file?
1. What are special directories?
    * current: `.`
    * parent: `..`
    * previous: `-`
    * home: `~`
1. How do I change directories?
    * `cd DIR`
    * `cd -`
    * `cd ..`
    * `cd`
1. How do I see what's in a file?
    * `cat FILE [FILE]`
    * `tac FILE [FILE]`
    * `more FILE`
    * `less FILE`
    * `head FILE`
    * `tail FILE`
1. What is a file descriptor and how do I use them?
    * Understand origins of TTY (teletype machines)
    * standard input (`/dev/stdin`, 0)
    * standard output (`/dev/stdout`, 1)
    * standard error (`/dev/stderr`, 2)
1. What is a pipe?
    * `ls -al | more`
1. How do write output of a command to a file?
    * `ls -al > /tmp/foo`
1. How do I append command output to end of a file?
    * `echo some >> /tmp/foo`
    * `echo thing >> /tmp/foo`
1. How do I zero out an existing or new file?
    * `> /tmp/foo`
1. How do I create a new file (or update time changed)?
    * `touch /tmp/foo`
1. How do I remove a file?
    * `rm FILE`
1. How do I find files with a keyword in the name?
    * `find . -name '*vim*' 2> /dev/null`
1. How do I send stderr to stdout as well?
    * `find / -name '*md*' 1> /tmp/foo 2> /dev/stdout`
    * `find / -name '*md*' > /tmp/foo 2> /dev/stdout`
    * `find / -name '*md*' > /tmp/foo 2>&1`
    * `find / -name '*md*' &> /tmp/foo`

# 2023 Boost - Week 5

📺 <https://youtu.be/ZcEIJFbHRn4>

This week we do "destructive" file system stuff related and take a lot of time to review the most common dangers. Watch this is you want to *keep* your job once you get it.

1. How do I create a new directory?
   
    ```sh
    mkdir NAME
    ```

1. How do I "hide" a file or directory?

    Give it a dot (`.`) as the first character in name.

1. How do I move or rename a file or directory?

    `mv OLD NEW`

    !!! danger
        Be very careful when moving and renaming since you can easily clobber an existing file or directory. Don't bother with activating `noclobber` because it will get in your way more than help you, just become aware/paranoid about the danger.

1. How do I move multiple files into a single directory?

    ```sh
    mv SOURCE... DIR
    ```

    SOURCE can be a file, directory (or path to) or a glob.

    !!! danger
        When moving muliple SOURCEs make *sure* that DIR is a directory and not a file.

    !!! note
        Note that `mv` sometimes will not work because the source and destination are on different file systems.

1. How do I list properties of a directory (instead of contents)?

    ```sh
    ls -lda DIR
    ```

1. How do I safely avoid typing long or complicated names?

    Tap tab (once or twice) for tab completion.

1. How do I remove a file?

    ```sh
    rm FILE
    ```

    !!! tip
        When working with destructive commands that operate on many files try `ls` first to make sure it only affects the files you want.

1. How do I create a temporary container (sandbox) just to try dangerous (stupid) things?

    ```sh
    podman run -it --rm ghcr.io/rwxrob/ws-skilstak
    ```

1. How do I remove a directory?

    ```sh
    rmdir DIR
    ```

    !!! note
        Prefer `rmdir` over alternatives to force yourself to be sure of each individual thing that is being deleted within that directory (since `rmdir` will not remove directories containing).

1. How do I remove a directory and everything under it recursively?

    ```sh
    rm -rf DIR
    ```

    !!! danger
        Even though this command does not work on significant system directories (like `/`) it is very recursively destructive and should almost never be used. Use `rmdir` instead.

1. How do I recover a broken or deleted configuration file?

    ```sh
    cp /etc/skel/FILE ~
    ```

1. How do I start a new shell and replace the currently running one?

    ```sh
    exec bash -l
    ```

1. How do I copy a file?

    ```sh
    cp FILE NEWNAME
    ```

1. How do I recusively copy a directory and subdirectories?

    ```sh
    cp -r SOURCE.. DIR
    ```

    !!! note
        This creates new files with new creation dates/times and ownership if copying from another user. Use other `cp` argument options when preserving them is important.
