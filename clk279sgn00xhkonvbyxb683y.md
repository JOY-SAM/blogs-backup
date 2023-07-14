---
title: "Scripts  For Git"
seoTitle: "Shell scripts for Git"
seoDescription: "Shell scripts for making your developer experience better."
datePublished: Fri Jul 14 2023 06:30:39 GMT+0000 (Coordinated Universal Time)
cuid: clk279sgn00xhkonvbyxb683y
slug: scripts-for-git
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689297573598/16312688-6b4a-40c2-895e-3ffa403733f4.jpeg
tags: github, git, full-stack, developer-experience, shell-script

---

Always tired of writing the same commands again and again for pushing your code to Git.

```bash
git add . 
git commit -m "commit_message"
git push
```

This reduces your developer experience. So let's make a shell script to follow the methodology of **Do not repeat yourself (DRY)**. Even though you're not familiar with shell scripts, don't worry copy paste it still works.

## Solution:

### Create a Scripts folder

```bash

mkdir ~/Scripts/
cd ~/Scripts/
```

### Create the Shell Script file

```bash
echo 'commit_message=$1
git add . &&
git commit -m "${commit_message}" &&
git push' >> Git.sh
```

### Make an Alias

To make it more comfortable and to be accessed all over the OS

**Mac Users**

```bash
echo "alias Git='zsh ~/Scripts/Git.sh'" >> ~/.zprofile
```

**Linux Users**

```bash
echo "alias Git='bash ~/Scripts/Git.sh'" >> ~/.bash_profile
```

Now close all terminals and open them again to get the effect

```bash
Git "Now this is my custom commit message!!"
```

## Life is good, but it can be better.