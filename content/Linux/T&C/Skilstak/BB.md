---
title: "Beginner Boost"
date: 2023-05-29T18:31:10-04:00
draft: false
---

{{< panel title="Update Log" style="success" >}}

* 2023 06 05 - Initial Commit

{{< /panel >}}


{{< panel title="Extracted Content" style="danger" >}}

This is material extracted from Skilstak.io Interspersed with my own notes as the course progresses

{{< /panel >}}

# 2023 Boost overview

Here's what we currently plan to cover over approximately 32 weeks in 2023 with an estimated completion date sometime in December based on two hours per week 

* Become an autodidact: learn to manage your own learning. (1h) [x]
* Take efficient, searchable notes with Markdown on GitHub. (1h) [x]
* Grok benefit and origin of terminal command-line interface. (1h) [x]
* Install and use bash shell on Windows and Mac (besides Linux). (1h) [x]
* Know why Ubuntu, RedHat, and Alpine are most relevant Linux distros. (20m) [x]
* Run Linux container(s) on Windows or Mac with podman. (1h) [x]
* Use search-centric system navigation on Windows, Mac, or Linux. (20m) [x]
* Get help for any Linux command without the Internet. (20m) [x]
* Use tab-completion to speed command line input. (20m) [x]
* Navigate Linux file system and understand general organization. (2h) [x]
* Capture, append, and connect command input, output, and errors. (1h) [ ]
* Run commands on multiple files using wildcard globbing. (1h) [ ]
* Search and filter text input and files with regular expressions. (2h) [ ]
* Edit text files in-place from the command line. (1h) [ ]
* Edit text files visually using terminal editor apps. (2h) [ ]
* Manage running application processes. (1h) [ ]
* Manage terminal windows with screen/tmux. (1h) [x]
* Leverage command history to save time. (20m) [x]
* Do effective research from command line with lynx or w3m. (1h) [ ]
* Understand and manipulate Linux file ownership and permissions. (1h) [ ]
* Find specific files anywhere and determine what they are. (1h) [ ]
* Understand how Internet networking generally works. (2h) [x]
* Use secure shell to safely interact with remote systems. (1h) [x]
* Save source to GitHub with git and gh. (1h) [x]
* Organize commands and start your own "dot files" GitHub repo. (1h) [x]
* Commit working Linux container as image to GitHub registry. (1h) [x]
* Write safe shell scripts in bash and ash with shellcheck. (1h) [ ]
* Grok and apply everything in the bash manual page (man bash). (4h) [ ]
* Doing math safely and reliably with bc and dc. (2h) [ ]
* Understand ASCII, terminal encoding, and escape sequences. (1h) [ ]
* Follow UNIX philosophies and use UNIX filters over plugins. (1h) [ ]
* Work with structured data in JSON, YAML, and delimited formats. (2h) [x]
* Do things as administrator (root) but only when necessary. (1h) [x]
* Install, and update software packages with apt. (1h) [x]
* Start your own custom Linux container image from scratch. (1h) [x]
* Customize bash profile and environment. (1h) [x]
* Customize ed/ex/vi/vim configuration. (1h) [x]
* Customize TMUX configuration. (1h) [x]
* Customize lynx configuration. (1h) [ ]
* Try coding in Python, C, and Go from CLI. (8h) [x]
* Create and maintain a consumable, sustainable resume. (2h) [ ]
* Complete GitHub profile page and grok job discovery from GitHub. (1h) [ ]
* Learn just enough Web development to create a personal page/blog. (2h) [x]
* Network and foster a professional learning network/community. (1h) [x]
* Know when and how to certify and get a good starting Linux job. (1h) [x]
* Set healthy work boundaries and self-care habits. (1h) [ ]
* Pay it forward! (1h) [ ]
* How to install Linux on hardware. [x]
* How to use Linux graphic user interfaces, desktops, and window managers. [x]

# Notes:

## Starting a project with GO 'The correct way'

### Repo Directory

* README.md
* License.md

### mod file

go mod init + 'path to project directory'

place to list dependancies

example mod file:

module github.com/trevorsmale/projectname

go 1.14

### Creating the program

file example 'main.go':

package main

func main() {
    println("Hello World")
}

### run main.go

go run main.go

### build to executable

go build main.go




# 2023 Boost - Week 1 [x]

📺 <https://youtu.be/cE-kkVwz0Xg> [x]

This week we start taking notes in basic Markdown on GitHub and connect with others doing the Boost. Then we go over the core applications that must be installed next week: bash shell, a good terminal, and Podman desktop.

1. Create a GitHub account [x]
    1. Pick a good, short, memorable name suitable for work [x]
    2. Find and follow some other friends from Boost [x]
    3. Create a private repo to contain notes from Boost with README.md [x]
2. Learn basic Markdown [x]
    1. Focus on one best way for consistency [x]
    2. Practice using your new README.md in repo of notes [x]
    3. Started taking notes from GitHub GUI [x]
3. Install bash
    1. Install git-bash on Windows [x]
    2. Install brew and then brew install bash on mac [x]
4. Install a better terminal application [x]
    1. Install Windows Terminal Preview on Windows [x]
    2. Install iTerm2 on Mac [x]
    3. Customize themes and colors to your preferences [x]
    4. Perhaps install and explore VSCode a bit to see as well [x]
5. Install Podman Desktop (with WSL2 extension if prompted) [x]
    1. Start exploring `podman` command from terminal [x]

# 2023 Boost - Week 2 [x]

📺 <https://youtu.be/0gNR6qj87a0> [x]

This week we learn about terminal and command line interfaces, containers and virtual machines and start using Podman Desktop and podman command for the first time.

1. Use command search to open a bash terminal (in full screen if prefer) [x]
2. What's a **command line**? **Shell**? [x]
    1. What's a **prompt**? [x]
        1. Why simple prompts are best? [x]
    2. What's a **command**? [x]
    3. What is a REPL? [x]
    4. What's an **argument**? [x]
    5. What is a **switch**, **flag**, and/or  **option**? [x]
    6. Difference between "terminal" and "command line" [x]
3. What's a **file system**? **Directory**? [x]
    1. Rooted node tree **data structure** [x]
    2. "Everything is a file in UNIX/Linux" (inode specifically) [x]
4. Learn bash shell navigation? [x]
    1. `exit` - exit the current shell [x]
    2. `pwd` - print working directory (show where you are) [x]
    3. `clear` - clear the screen [x]
    4. `ls` - list files and directories [x]
        1. Current directory [x]
        2. Parent directories [x]
        3. Sub-directories [x]
        4. Globing [x]
    5. `cd` - change directory [x]
    6. `which` - see which command will be run (if available) [x]
    7. How can I find help? `-h`, `man`, `info`, `help`, `apropos`, `whatis` [x]
5. What's a container? [x]
    1. ... compared to a *virtual machine*? [x]
6. Create hub.docker.io and/or quay.io account (if needed) [x]
7. Start Podman Desktop GUI [x]
    1. Pull an image [x]
    2. Start a container [x]
    3. Open a terminal to the container [x]
    4. Understand equivalents from a command line [x]
8. Run a new temporary container with `podman` command [x]
    1. `ubuntu` [x]
    2. `busybox` [x]
    3. `alpine` [x]
    4. `archlinux` [x]
    5. `kalilinux/kali-rolling` [x]
    6. `redhat/ubi8-minimal` [x]
    7. `gentoo/stage3` [x]

# 2023 Boost - Week 3 [x]

📺 <https://youtu.be/mUmQk1o6FFs> [x]

(PLEASE SKIP TO WEEK 4.) This week we setup an Ubuntu Linux container image using podman command and apt package manager, learn how to save (commit) an image copy so we have backups during our setup, and how to navigate the command line.

1.  Why Ubuntu? [x]
2.  Pull an Ubuntu Linux image into podman images [x]
3.  Create (run) a named container from the Ubuntu local image [x]
4.  Exit the container [x]
5.  Understand difference between running and exited containers [x]
6.  Use –rm for temporary containers [x]
7.  Use podman ps -a to show all containers (running and exited) [x]
8.  Use podman rm to remove unwanted containers [x]
9.  Use bash tab completion to save on typing [x]
10. Use up and down arrows (for now) to get previous commands [x]
11. Restart and attach to named container [x]
12. Use Advanced Package Manager (APT) [x]
13. Use `apt update` command to refresh list of packages [x]
14. Clear the screen with clear command (not control-L) [x]
15. Install documentation helpers [x]
16. Use man to get help about commands [x]
17. Use help to get help about bash builtins [x]
18. Look for runnable stuff [x]
    1.  Use which command [x]
    2.  Use type builtin [x]
    3.  Use command -v command [x]
    4.  Use file command to see what type of thing it is [x]
19. Everything is a file (inode) even directories [x]
    1.  Use ls command [x]
    2.  Use pwd command [x]
    3.  Use cd to change directories [x]
    4.  Use chmod to change permissions [x]
    5.  Use chown to change owner (and group) [x]
20. Add new user with adduser (or useradd) [x]
21. Delete user with deluser (or userdel) [x]
22. Add new group with addgroup (or groupadd) [x]
23. Delete group with delgroup (or groupdel) [x]
24. Commit (save) container as image [x]
25. Push saved image to GitHub Container Registry [x]
    1.  Create Personal Access Token on GitHub [x]
    2.  Use podman push to push local image to remote ghcr.io [x]
    3.  View saved GitHub packages (containers) [x]

# 2023 Boost - Week 4 [x]

📺 <https://youtu.be/SPoqW1CMEhY> [x]

Let's do this again. Weeks 2 and 3 were a little harder than most beginners might be able to handle. Most Linux users will be using a Linux that has been installed already. The Boost is primarily intended for *them* (not admins and hackers, who are also users). So we've prepared a quick-start with an existing Linux container image. Here's how to get it and another take at how to get going without having to setup anything.

1. What concepts do all *users* need to understand? [x]
2. What does it mean to be a Linux "user" (vs "admin" or "hacker")? [x]
3. Create a local Linux container for the Boost [x]

    ```sh
    podman run -it --hostname skilstak --name boost -v shared://shared ghcr.io/rwxrob/ws-skilstak
    ```

4. What is the difference between a terminal and a command line? [x]
5. What do the parts of the prompt mean? [x]
6. How do I clear the screen? [x]
    * Do not depend on Control-L [x]
    * `clear` (or `c`) [x]
7. How do I see where I am? [x]
    * `pwd` [x]
8. How do I see everything in this directory? [x]
    * `ls -al` [x]
9. How do get help information about a command? [x]
    * `CMD -h` or `CMD --help` [x]
    * `man CMD` [x]
    * `help CMD` [x]
    * `apropos KEYWORD` (if you want) [x]
10. What is a directory and what is a file? [x]
11. What are special directories? [x]
    * current: `.` [x]
    * parent: `..` [x]
    * previous: `-` [x]
    * home: `~` [x]
12. How do I change directories? [x]
    * `cd DIR` [x]
    * `cd -` [x]
    * `cd ..` [x]
    * `cd` [x]
12. How do I see what's in a file? [x]
    * `cat FILE [FILE]` [x]
    * `tac FILE [FILE]` [x]
    * `more FILE` [x]
    * `less FILE` [x]
    * `head FILE` [x]
    * `tail FILE` [x]
13. What is a file descriptor and how do I use them? [x]
    * Understand origins of TTY (teletype machines) [x]
    * standard input (`/dev/stdin`, 0) [x]
    * standard output (`/dev/stdout`, 1) [x]
    * standard error (`/dev/stderr`, 2) [x]
14. What is a pipe? [x]
    * `ls -al | more` [x]
15. How do write output of a command to a file? [x]
    * `ls -al > /tmp/foo` [x]
16. How do I append command output to end of a file? [x]
    * `echo some >> /tmp/foo` [x]
    * `echo thing >> /tmp/foo` [x]
17. How do I zero out an existing or new file? [x]
    * `> /tmp/foo` [x]
18. How do I create a new file (or update time changed)? [x]
    * `touch /tmp/foo` [x]
19. How do I remove a file? [x]
    * `rm FILE` [x]
20. How do I find files with a keyword in the name? [x]
    * `find . -name '*vim*' 2> /dev/null` [x]
21. How do I send stderr to stdout as well? [x]
    * `find / -name '*md*' 1> /tmp/foo 2> /dev/stdout` [x]
    * `find / -name '*md*' > /tmp/foo 2> /dev/stdout` [x]
    * `find / -name '*md*' > /tmp/foo 2>&1` [x]
    * `find / -name '*md*' &> /tmp/foo` [x]

# 2023 Boost - Week 5 [x]

📺 <https://youtu.be/ZcEIJFbHRn4> [x]

This week we do "destructive" file system stuff related and take a lot of time to review the most common dangers. Watch this is you want to *keep* your job once you get it.

1. How do I create a new directory? [x]
   
    ```sh
    mkdir NAME
    ```

2. How do I "hide" a file or directory? [x]

    Give it a dot (`.`) as the first character in name.

3. How do I move or rename a file or directory? [x]

    `mv OLD NEW`

    !!! danger
        Be very careful when moving and renaming since you can easily clobber an existing file or directory. Don't bother with activating `noclobber` because it will get in your way more than help you, just become aware/paranoid about the danger.

4. How do I move multiple files into a single directory? [x]

    ```sh
    mv SOURCE... DIR
    ```

    SOURCE can be a file, directory (or path to) or a glob.

    !!! danger
        When moving muliple SOURCEs make *sure* that DIR is a directory and not a file.

    !!! note
        Note that `mv` sometimes will not work because the source and destination are on different file systems.

5. How do I list properties of a directory (instead of contents)? [x]

    ```sh
    ls -lda DIR
    ```

6. How do I safely avoid typing long or complicated names? [x]

    Tap tab (once or twice) for tab completion.

7. How do I remove a file? [x]

    ```sh
    rm FILE
    ```

    !!! tip
        When working with destructive commands that operate on many files try `ls` first to make sure it only affects the files you want.

8. How do I create a temporary container (sandbox) just to try dangerous (stupid) things? [x]

    ```sh
    podman run -it --rm ghcr.io/rwxrob/ws-skilstak
    ```

9. How do I remove a directory? [x]

    ```sh
    rmdir DIR
    ```

    !!! note
        Prefer `rmdir` over alternatives to force yourself to be sure of each individual thing that is being deleted within that directory (since `rmdir` will not remove directories containing).

10. How do I remove a directory and everything under it recursively? [x]

    ```sh
    rm -rf DIR
    ```

    !!! danger
        Even though this command does not work on significant system directories (like `/`) it is very recursively destructive and should almost never be used. Use `rmdir` instead.

11. How do I recover a broken or deleted configuration file? [x]

    ```sh
    cp /etc/skel/FILE ~
    ```

12. How do I start a new shell and replace the currently running one? [x]

    ```sh
    exec bash -l
    ```

13. How do I copy a file? [x]

    ```sh
    cp FILE NEWNAME
    ```

14. How do I recusively copy a directory and subdirectories? [x]

    ```sh
    cp -r SOURCE.. DIR
    ```

    !!! note
        This creates new files with new creation dates/times and ownership if copying from another user. Use other `cp` argument options when preserving them is important.
