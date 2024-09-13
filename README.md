# linux-git-tips

Here are some tips on how to use git effectively when working on your assignments.

# TLDR

Issue the following commands to configure your git (replace the strings in 
the 3rd and 4th commands with your personal info).

```
git config --global credential.helper store
git config --global pull.rebase true
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

# Basic commands

## Download files

You can think of git as a way to upload/download files, with github being the server where all the files are
stored.

To "Download" a set of files, you would use `git clone` followed by the URL to the file location 
(we call this URL a "git reposotiry", or simply "repo"

```bash
$ git clone https://github.com/env3d-lessons/linux-introduction.git
```

The above command would effectively download all the files, along with the entire directory structure
into your local machine.  A new sub-directory named will be created under your working directory.

In the above case, a sub-directory called  `linux-intorudction` will be created.

## Upload files

If you have make some changes to the files in the subdirecotry, the files will not be uploaded to the
repo on github automatically.  You will need to perform the following commands.  Please note that
these commands need to be perform in the sub-directory of your cloned repo.

```bash
$ echo "Hello" > new_file.txt
$ git add -A
$ git commit -m 'created a new file'
$ git push
```

# Username and password

Everytime to interact with github (i.e. `git clone` or `git push`, the system may ask for your
github username and password.  It gets tiring if you have to provide it everytime.  Here's
a tip - execute the following command before `git clone` or `git push`:

```
$ git config --global credential.helper store
```

The above command will instruct the git command to store your username and password, so you don't 
have to keep providing it over and over.

# First time configration

If it's your very first time interacting with git, you may get an error message asking you to 
provide email and user name.  As follows:

```bash
$ git commit -a -m 'submit'
Author identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'env3d@ip-172-31-2-248.(none)')
```

This is simply git wanting to keep track of who is doing the commit,
and these information are simply labels.  Execute the following commands to configure your personal 
information:

```bash
$ git config --global user.email "you@example.com"
$ git config --global user.name "Your Name"
```

Make sure you replace the email and name with your email and name.  

# Addtional Errors

If you get and error during git push, you may need to issue a `git pull` first.  However
before you do a git pull, make sure you configure it using the following command

```
$ git config --global pull.rebase true
```

