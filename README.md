# Groundwork Lab

This lab assignment is to be completed individually.

**Assigned: Wednesday, August 25, 2021 at 3:00 PM**\
**Due: Wednesday, September 1, 2021 at 3:00 PM**

## Objectives

To learn how to...

- Log in to and open a terminal on JupyterLab
- Use Git to `clone` repositories and `add`, `commit`, and `push` changes
- Set up SSH key-based authentication on GitHub
- Use basic terminal commands
- Format documents using the Markdown markup language

## Part 1: JupyterLab

In Computational Expression, we will use software, such as Git and Python, that may not come pre-installed on your laptop. Or, if they do come pre-installed, the versions of the software may not match the versions that I used while writing the exercises or lab assignments. Because the behavior of a program may change from version to version, this may cause you to get different output than is written in the exercise or lab assignment. Not only might this be confusing for you, but this would also complicate grading for me since sometimes I may not be able to quickly discern whether the difference in outputs is due to differences in versions or differences in code.

You *could* choose to install these software on your laptop, making sure that their versions match the versions I use. In fact, if you already have a lot of experience in installing and troubleshooting command-line software and would like to be able to complete coursework directly on your laptop, you are welcome to do so as long as you communicate this to me.

However, others who do not yet have this experience should use JupyterLab to complete coursework. JupyterLab is a computer you can access through your browser that already has all the software you will need for this course installed.

### Step 1: Log In

Assuming that you have already submitted your GitHub username to me and I have created an account for you on JupyterLab, navigate to [jupyter.cs.allegheny.edu](https://jupyter.cs.allegheny.edu) (you may want to bookmark this!), then click the **Sign in with GitHub** button. After JupyterLab has finished starting up, you should see a sidebar on the left that contains a table with the columns **Name** and **Last Modified** and, to the right of this sidebar, a tab named **Launcher**. If you see these things, you know that you have successfully logged in to JupyterLab 🎉.

This sidebar and tab, as well as everything else you see when you navigate to [jupyter.cs.allegheny.edu](https://jupyter.cs.allegheny.edu), are all part of the JupyterLab **graphical user interface** (GUI). GUIs are named as such because they use *graphics*, such as buttons or text boxes, to enable *users* to *interact* or *interface* with a computer.
Windows and macOS are examples of GUIs that enable to you interact with your laptop. In the same way, the GUI that you see at [jupyter.cs.allegheny.edu](https://jupyter.cs.allegheny.edu) enables you to interact with the JupyterLab computer.

### Step 2: Open a Terminal

A terminal is a program that you can use to type and execute commands on a computer.

There are two ways to open a terminal on JupyterLab:

1. Click **File**, then hover over **New**, then click **Terminal**.
2. If you have a **Launcher** tab open, under the **Other** category, click **Terminal**.
    - If you do not have a **Launcher** tab open, you can open one by either clicking the blue **+** button in the sidebar or by clicking **File**, then **New Launcher**.

In the terminal tab that you have just opened, you should see a line that looks similar to

```bash
mariakimheinert@jupyter-cs-allegheny-edu:~$
```

, where instead of `mariakimheinert` you see your own GitHub username, followed by a blinking rectangle. This line is known as a **command prompt** because it is *prompting* you for a command to run.

Why are terminals useful? Sometimes, certain actions can be faster to perform by typing and executing a command rather than by using a GUI.

For example, there are two ways you can create a new file on JupyterLab. The first is to use the JupyterLab GUI:

1. In the sidebar on the left, right click, then click **New File**. A new file should appear in the sidebar with the name `untitled.txt`. Let's write something in the file. Double click the file, which will open it in a tab that contains an editor. Type `Hello, World!` and hit **CTRL + S** or **CMD + S** to save your changes. Since `untitled.txt` is not a very descriptive name, right click the file, click **Rename**, type `hello_world`, then hit the **Enter** key. Because we created this file for demonstration purposes and no longer need it, you can delete it by right clicking it in the sidebar and clicking **Delete**.

Compare this to creating a new file in a terminal on JupyterLab.

2. In the terminal tab that you previously opened, type the command `echo "Hello, World!" > hello_world.txt` and hit the **Enter** key to execute the command. (If it does not immediately appear in your sidebar, click the **Refresh File List** button (🔃) at the top of the sidebar.) You can verify that this file is identical to the `hello_world.txt` file you created using the GUI by double clicking the file, which will open it in a tab. To delete the file, back in the terminal, run the command `rm hello_world.txt`.

As you just experienced, it took many more steps to create, descriptively name, add content to, and delete a file by using the GUI than by using the terminal. Using the terminal is almost like magic, right? You typed a "spell" and, just like that, things appeared or disappeared! Throughout this course, you will learn all sorts of different "spells" that do even wilder things than creating and deleting files. Though, creating and deleting files is pretty cool, too.

By the way, do not worry if you do not understand how the commands `echo "Hello, World!" > hello_world.txt` or `rm hello_world.txt` worked--they were used only to demonstrate how using the terminal could be faster than using a GUI. As we progress through the course, not only will you be able to understand these commands, but you will be able to write your own!

## Part 2: Git, GitHub, and SSH Keys

In other courses, you may have submitted your work to your professors through email or on Google Drive. In computer science courses at Allegheny College, you will submit your work on a website called [GitHub](https://github.com).

Before we talk about GitHub, let's discuss the ways in which the submission process for computer science coursework will differ from the submission process for coursework in other departments.

- In other departments, you submit mostly files such as Word or Google documents, Excel or Google spreadsheets, PowerPoint or Google slides, or PDF documents. In computer science, not only will you submit mostly *code* files, but for every assignment, whether it be reading comprehension exercises, a lab assignment, or your final project, you will submit what is called a **Git repository**. You can think of a Git repository as a folder, or **directory** (the computer science way of saying "folder"), that stores additional information about why, when, and by whom changes to files in the repository were made.
- You may think that it is crazy that we ask you in computer science to track every change, when it was made, and by whom it was made, even if you are the only one working on an assignment. And indeed, it *would* be crazy if we expected you to do all of this manually. But, very fortunately for us, there exists a program called [Git](https://git-scm.com), which is a **version control system** that will track all of this for you with just a few simple terminal commands. Magic 🪄! So, while in other departments, you only had to save your changes using **CTRL + S** or **CMD + S**, in computer science, you will also have to track your changes using Git.
- In other departments, you have probably been told that it is important to back up your work, either to a hosting service like Google Drive, an external hard drive, or even a USB stick. Well, believe it or not, it is also important to back up your work in computer science! However, in computer science, you will back up your work on GitHub.\
What is GitHub, exactly? GitHub is a Git repository hosting service. You can think of it like Google Drive for Git repositories. While working on an assignment in a Git repository on JupyterLab, you will back up, or **push**, your work to the master copy of the repository on GitHub.\
You may have been wondering why you need to track changes using Git. After all, if your program works in the end, does it matter what it looked like while you were writing it? The short answer to this question is yes! And as we progress through the course, it will become more and more evident why you want to track changes to your program. But, *another* reason to track changes using Git is because you will use Git to push your work to GitHub and Git will only push the changes that you have tracked, or have **committed** to. You should only track changes that you are certain are improvements to the files in the Git repository.

Now, if you have read all of this and are still confused by the terms repository, Git, and GitHub, please do not worry! It is much easier to learn about these technologies by using them, rather than by only reading about them. And you will use these technologies *plenty* throughout this course. In fact, let's start now!

### Step 3: Clone This Git Repository

For each assignment in this course, I will create a Git repository for you that contains everything you need to complete the assignment--except for the solution, of course!

In order to access your Git repository for an assignment, click on the link that I send out for that assignment on Discord.

In fact, if you are reading this now, you have already done exactly that! At the top of this page, you should see the name of your Git repository. It will look something like `groundwork-lab-mariakimheinert`, where instead of `mariakimheinert`, you see your own GitHub username.

In a previous paragraph, I wrote

> While working on an assignment in a Git repository on JupyterLab, you will back up, or **push**, your work to the master copy of the repository on GitHub.

But, if you look on JupyterLab, you will notice in the sidebar that the `groundwork-lab-<YOUR-GITHUB-USERNAME>` Git repository is not there!

This is because the Git repository that you see on this page, which is the master copy, is the only copy of this Git repository so far. In order to have a copy of this Git respository to work in on JupyterLab, you must copy, or **clone**, this repository to JupyterLab.

But how will GitHub know that JupyterLab is allowed to access the Git repositories linked to your GitHub account? Actually, it will not! At least, not unless we give GitHub some way to recognize the connection between JupyterLab and your GitHub account. To do this, you can use an SSH key.

An SSH key is a pair of keys shared between two computers to allow one computer to recognize the other. This recognition is also referred to as authentication. Thus, this process is known as SSH key-based authentication.

In order for GitHub to recognize, or authenticate, JupyterLab, you must first generate an SSH key on JupyterLab. To do this, in a terminal on JupyterLab, run the command `ssh-keygen` and, to accept the default settings for the SSH key, continue to hit the **Enter** key for every prompt that appears until the SSH key has been generated. You should see something like this once you have successfully generated a SSH key:

```text
The key's randomart image is:
+---[RSA 3072]----+
|    +.o o..      |
|   o = .D=.      |
|    . * =o..     |
|     . O *o.     |
|    . ++B+= .    |
|     +.S+.++     |
|      *.o o      |
|     + o .oo     |
|      o  .o.     |
+----[SHA256]-----+
```

Let's take a look at the SSH key you just generated. Run the command `cd ~/.ssh; ls`. In the output, you should see `id_rsa` and `id_rsa.pub`, which are the pair of keys that make up your SSH key! The `.pub` extension indicates that the `id_rsa.pub` is the public key, while `id_rsa` is the private key. **You will never share your private key with GitHub or anyone else.** Instead, you will give GitHub your public key.

To do this, run `cat id_rsa.pub` and copy the output that appears all the way from `ssh-rsa` to `@jupyter-cs-allegheny-edu`. Now, go to GitHub, click on the down arrow next to your profile photo in the top right corner, then click **Settings**. In the sidebar on the left, click **SSH and GPG keys**, then the green **New SSH key** button in the top right corner. Give your SSH key a title (I recommend "Allegheny College JupyterLab") and paste your key into the provided text box. Then, click **Add SSH key**.

Now that GitHub has one part of your SSH key, when you try to access repositories that are linked to your GitHub account, it will check if the public key that you added corresponds to the private key stored on the computer from which you are requesting access (in this case, JupyterLab). If GitHub finds that these keys correspond, which it will since the `id_rsa` private key corresponds to the `id_rsa.pub` public key that you added to your GitHub account, it will authenticate your computer and allow you to access your GitHub repositories from that computer.

Let's put this to the test. At the top of this page, click the green **Code** button, make sure the **SSH** option is underlined, then click the clipboard icon (📋). This will copy the address of this Git repository to your clipboard.

Then, in a terminal on JupyterLab, run the command `cd ~; git clone <ADDRESS-OF-GIT-REPOSITORY>`. After the command has completed, run `ls`.
If all went well, you should now see a copy of the `groundwork-lab-<YOUR-GITHUB-USERNAME>` Git repository. You should also see `groundwork-lab-<YOUR-GITHUB-USERNAME>` in the sidebar on the left, which refers to the same Git repository that was shown in the output of the `ls` command. This Git repository on JupyterLab is where you will work on this lab assignment moving forward--it is your **working copy**. Double click `groundwork-lab-<YOUR-GITHUB-USERNAME>` in the sidebar and then double click on `README.md` to open this document on JupyterLab.

Actually, for every assignment here on out, you will follow these same steps to clone a working copy of your Git repository for that assignment on JupyterLab. To summarize:

1. Access your Git repository for the assignment by clicking on the link for the assignment that I send out on Discord.
2. Copy its address, which you can see by clicking the green **Code** button at the top of the master copy of the Git repository, making sure to use the **SSH** option.
3. In a terminal on JupyterLab, run the command `cd ~; git clone <ADDRESS-OF-GIT-REPOSITORY>`.

Notice that you do not need to set up a new SSH key for every assignment. As long as you do not delete either the `id_rsa` private key on JupyterLab or the public key that you added to your GitHub account, you will be able to continue using SSH key-based authentication between JupyterLab and GitHub indefinitely.

## Part 3: Basic Terminal Commands

As you discovered before, using the terminal to interact with a computer can often be faster than using a GUI. Not only is using a terminal normally more efficient, but there are numerous software that do not have a GUI and can only be run as a command in a terminal. For this reason, all computer scientists must know how to use a terminal.

Every time you use a terminal, you will likely want to perform at least one of the following six actions:

1. See all the files and directories in your current, or **working** directory
2. Create a file
3. Create a directory
4. Delete a file or directory
5. Navigate into or out of a directory
6. Move a file or directory from one location to another

You need to know the basic terminal commands that are used to perform these actions.

### Step 4: Help Phil and Lil Plan Their Wedding

Phil and Lil just got engaged! 💍 Somewhat technically challenged, they need help to set up a directory to store all of their wedding planning files. Knowing that this would be a great opportunity to learn the basic terminal commands you need to know, I volunteered you for the job! You are very welcome. ☺️

First, open a terminal. Let's look at the command prompt again:

```bash
mariakimheinert@jupyter-cs-allegheny-edu:~$
```

Notice the `~` near the end of the command prompt? Everything between the `:` and `$` is the **path** to your working directory. The `~` represents your **home** directory. Your home directory is a directory on JupyterLab made for you and only you. This means that no one except for you (and me, occasionally) can access your home directory and its contents. Since there is nothing after the `~`, you know that you are in (i.e. your working directory is) your home directory.

To see the contents of your home directory, run `ls` to **list** all files and directories.

Now, navigate into `groundwork-lab-<YOUR-GITHUB-USERNAME>` by running `cd groundwork-lab-<YOUR-GITHUB-USERNAME>`. The `cd` command stands for **change directory** and takes as an **argument** the directory to navigate into.

Use `ls` to list the files in `groundwork-lab-<YOUR-GITHUB-USERNAME>`, which should now be your working directory. In addition to `README.md`, you should see the following files:

- `engagement-photo-0.jpeg`
- `engagement-photo-1.jpeg`
- `engagement-photo-2.jpeg`
- `venue.pdf`

These are the wedding planning files that Phil and Lil have so far.

Let's give them a home. Create a directory named `wedding-planning` by running `mkdir wedding-planning`. The `mkdir` command stands for **make directory**; it takes as an argument the name of the directory to create.

Run `ls` again to confirm that you have created the `wedding-planning` directory. Then, navigate into the `wedding-planning` directory using the command `cd wedding-planning`.

As you can see, Phil and Lil already have a file from a vendor, `venue.pdf`, that they need to store. In `wedding-planning`, create a directory named `vendors` by running `mkdir vendors`. Phil and Lil would like to store all of their vendor contracts in one directory, so in `vendors`, create a directory named `contracts` with the command `mkdir vendors/contracts`. Notice that we did not navigate into the `vendors` directory before creating the `contracts` directory, but instead specified that `contracts` should be created in `vendors` by including `vendors` in the argument for `mkdir`. Navigating into the `vendors` directory and running `mkdir contracts` would have also created `contracts` in the right location--`mkdir vendors/contracts` is just a shorter way of doing the same thing.

Now that we have a `contracts` directory, let's move the `venue.pdf` file into it. Recall that `venue.pdf` is located in `groundwork-lab-<YOUR-GITHUB-USERNAME>`, which is now one directory above your working directory (`wedding-planning`). To move back up one directory, run `cd ..`. If you run `ls`, you should see `venue.pdf`.

To move `venue.pdf` into `wedding-planning/vendors/contracts`, run `mv venue.pdf wedding-planning/vendors/contracts`. The command `mv` stands for `move` and takes two arguments--the file or directory to move and the location to move it to. To confirm that the file was moved, run `cd wedding-planning/vendors/contracts` to navigate into the `contracts` directory and run `ls`.

Phil and Lil would like a file to keep track of all of their vendors. Since you are in the `contracts` directory, run `cd ..` to move back up to the `vendors` directory. Now, run `touch list.txt` to create a file named `list.txt`. The `touch` command takes one argument--the name of the file to create. Confirm that `list.txt` exists by running `ls`.

What's that, Phil and Lil? Oh, you are having second thoughts about showing `engagement-photo-1.jpeg` to everyone (including *your grandparents*) at your wedding? No worries, we can just delete it!

Move back up into `groundwork-lab-<YOUR-GITHUB-USERNAME>` by running `cd ../..`. To delete Phil and Lil's scandalous shot, run `rm engagement-photo-1.jpeg`. The `rm` command, which stands for **remove**, takes one argument--the file or directory to delete. Note that if you are deleting a directory, you must include the `-r` (or, **recursive**) option. For instance, if you wanted to practice all of these commands again, you could run `rm -r wedding-planning`--but make sure that you *really* want to do this as there is no going back!

If you have not deleted it, your `wedding-planning` directory should now look like:

```text
wedding-planning
└── vendors
    ├── contracts
    │   └── venue.pdf
    └── list.txt
```

But, there is more wedding planning to be done! Using the commands you just learned, which are summarized below, create files and folders and move Phil and Lil's engagement photos so that the `wedding-planning` directory looks like this:

```text
wedding-planning
├── guests
│   ├── list.txt
│   └── seating-arrangement.txt
├── slideshow
│   ├── engagement-photo-0.jpeg
│   └── engagement-photo-2.jpeg
└── vendors
    ├── contracts
    │   └── venue.pdf
    └── list.txt
```

| Command                                        | Behavior                                             |
|------------------------------------------------|------------------------------------------------------|
| `ls`                                           | Lists all files and directories in working directory |
| `cd <PATH-TO-DIRECTORY>`                       | Navigates into directory                             |
| `mkdir <NAME-OF-DIRECTORY>`                    | Creates  directory                                   |
| `mv <NAME-OF-FILE-OR-DIRECTORY> <DESTINATION>` | Moves file or directory to destination               |
| `touch <NAME-OF-FILE>`                         | Creates  file                                        |
| `rm [-r] <NAME-OF-FILE-OR-DIRECTORY>`          | Deletes file or directory                            |

## Part 4: Markdown

You may have noticed that this `README.md` document contains

### headers

#### of

##### different

###### sizes,

**bolded** and *italicized* text,

| a     |
|-------|
| table |

, and `even`

```text
code blocks!
```

In Microsoft Word or Google Docs, you would format this document by highlighting the text that you want to format and adjusting its size, weight, background color, or font. However, in computer science courses, we use [Markdown](https://www.markdownguide.org/) to format our written documents. This is what the `.md` in `README.md` stands for.

> [Markdown is a lightweight markup language that you can use to add formatting elements to plaintext text documents.](https://www.markdownguide.org/getting-started/)

You know that Markdown files are plaintext text documents because when you open them, all you see is plaintext.

If you have this file opened on JupyterLab, right click anywhere in the file and click **Show Markdown Editor**. This will open a tab that shows what this file really contains without the Markdown rendering functionality that the JupyterLab GUI provides. You can see that, in addition to the text that you have been seeing, it also contains many pound signs (`#`) and backticks (`` ` ``) and asterisks (`*`) that you have not been seeing.

And that is the beauty of Markdown! When you open a file with a program that knows how to interpret the Markdown syntax, such as the JupyterLab GUI, those symbols are not shown and instead format the document.

### Step 5: Write a Markdown Document

In the sidebar, in `groundwork-lab-<YOUR-GITHUB-USERNAME>`, create a file named `about-me.md`, right click on the file, hover over **Open With**, then click **Editor**.

You can see the JupyterLab GUI interpret your Markdown in real time as your write it by right clicking in the editor and clicking **Show Markdown Preview**.

Using a [Markdown cheat sheet](https://www.markdownguide.org/cheat-sheet/), please write a short introduction about yourself so that I can get to know you better.

This `about-me.md` file should include:

1. A level 1 heading that says **About Me** (`#`)
2. A sentence that includes the **name** you go by in bold, your *year* in italics, and ***where you are from*** in both bold and italics.
3. Two level 2 headings (`##`)--**Academic Goals**, **Favorite Things**, and **A Ranking of Marvel Chrises**
4. Under the **Academic Goals** heading, a sentence or two that state your major (or, intended major, which may be "undecided") and what you are hoping to get out of this course
5. Under the **Favorite Things** heading, an unordered list (`-`) of three of your favorite foods or hobbies
6. Under the **A Ranking of Marvel Chrises**, an ordered list (`1.`, `2.`, `3.`) of your ranking of Chris Pratt, Chris Hemsworth, and Chris Evans based on whatever you want

## Part 5: Submitting Your Work

### Step 6: Track Your Changes

By this point, you have made *many* changes to your `groundwork-lab-<YOUR-GITHUB-USERNAME>` Git repository! As discussed previously, not only do you have to save your changes using **CTRL + S** or **CMD + S**, but you also need to track your changes using Git.

But first, recall that part of the information that Git tracks is who made the changes. In order for Git to add an author to your changes, you must set your Git username and email on JupyterLab.

To do this, run:

```bash
git config --global user.email "<YOUR-GITHUB-EMAIL>"
git config --global user.name "<YOUR-GITHUB-USERNAME>"
```

Now, Git will know who is tracking these changes.

There are two stages to tracking your changes:

1. Add all of the changes you want to track
2. Commit to those changes and give them a description

Since you want to add all of the changes that you made to the `groundwork-lab-<YOUR-GITHUB-USERNAME>` Git repository, in a terminal, navigate to `groundwork-lab-<YOUR-GITHUB-USERNAME>` and run `git add .`. This will add everything in the working directory, specified by the `.`, to be committed. This step is also referred to as "staging" your files.

To commit these changes, run `git commit -m "<A-ONE-LINE-DESCRIPTION-OF-THE-CHANGES>"`. For example, you might run `git commit -m "Add required deliverables"`.

### Step 7: Push Your Changes to the Master Copy

When you create a commit containing your changes by using the command `git commit`, those changes still exist only on JupyterLab. To back up and submit your work on GitHub, you must push your changes by running `git push`. You can verify that you have successfully pushed your work by looking at your Git repository on GitHub.

### A Very Important Note About Backing Up Your Work

Although in this lab assignment, you only tracked and pushed your changes once, in all other assignments, you should track and push your changes as frequently as possible to avoid losing work if JupyterLab ever goes down. I will only ever grade your last push by the due date for an assignment, so please do not hesitate to push even when your assignment is incomplete!

## Conclusion and Summary of Required Deliverables

Congratulations--you just completed your first lab assignment! This is a tremendous accomplishment. The first lab assignment is one of the most difficult lab assignments for many students because it asks you to enter such unfamiliar territory. But, by golly, you have done it.

For your peace of mind, here is a summary of the required deliverables for this lab assignment:

1. A `wedding-planning` directory that contains all files and folders specified in the instructions
2. An `about-me.md` Markdown document that contains all of the Markdown elements specified in the instructions

Make sure to double-check that you have all of these things!
