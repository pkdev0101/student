---
layout: post
title: "🌐 Developer Environment Setup with KASM Workspace"
description: "A complete guide to setting up Ubuntu-based KASM Workspace for coding, version control, and package management."
author: "Pranay Kamath"
categories: ["DevOps", "Development"]
permalink: /blogs/kasm-workspace-setup
breadcrumb: true
toc: false
---
# 🌐 Developer Environment Setup with KASM Workspace
 
*A complete Ubuntu-based workflow for coding, version control, and package management*
 
This guide walks you through configuring your KASM Workspace from the ground up. You’ll learn how to navigate with Linux commands, manage packages, work with Git, and streamline your projects inside VSCode. By the end, you’ll have a reliable development environment that mirrors real-world workflows.
 
---
 
## Why Use KASM Workspace?
 
Traditional setups can be messy: different operating systems, inconsistent tools, and “it works on my machine” issues. KASM Workspace solves these challenges by:
 
* Running a **Linux-based environment** in your browser that feels like a local machine
* Giving you access to **developer essentials** like Python, Ruby, Git, and package managers
* Providing a **reproducible setup** for projects and team collaboration
* Allowing you to follow the full **software development lifecycle (SDLC)**: code → build → test → commit → deploy
 
---
 
## First-Time Setup
 
When you launch KASM Workspace for the first time, you’ll want to initialize your project and tools. Here’s a structured flow:
 
1. **Create a working directory**
 
   * Example: `mkdir opencs && cd opencs`
   * This keeps your workspace organized and avoids scattering files everywhere.
 
2. **Clone a repository**
 
   * Example: `git clone https://github.com/Open-Coding-Society/student.git`
   * Cloning gives you a local copy of a project hosted on GitHub.
 
3. **Run setup scripts**
 
   * Use `./scripts/activate.sh` to configure Git with your username and email.
   * Use `./scripts/venv.sh` to create and activate a Python virtual environment.
   * Virtual environments isolate dependencies, preventing conflicts between projects.
 
4. **Open VSCode**
 
   * Launch with `code .` inside your project folder.
   * This command opens the current directory directly in VSCode.
 
---
 
## Visualizing the Workflow
 
🖥️ **Terminal Navigation** → commands like `mkdir`, `cd`, and `ls` to move around
📂 **Project Initialization** → use Git to bring projects into your workspace
🛠️ **Tool Activation** → enable Python, Ruby, Git, and other required tools
🔄 **Development Cycle** → `write → test → commit → push → deploy`
 
---
 
## VSCode as Your Coding Dashboard
 
Visual Studio Code isn’t just a text editor—it’s where everything comes together. Here’s why it matters:
 
* **Editing Made Simple**: Syntax highlighting, IntelliSense, and auto-completion speed up coding.
* **Terminal Integration**: Run scripts, install packages, and use Git without leaving the editor.
* **Version Control Built-In**: Stage, commit, branch, and push changes directly from the interface.
* **Extensions Marketplace**: Tools like GitLens, Prettier, Python, and Markdown improve productivity.
* **Debugging Power**: Add breakpoints, inspect variables, and step through code visually.
* **Workspace Management**: Keep multiple projects or folders open and organized.
 
💡 Pro tip: Use `Ctrl + ~` to quickly open the integrated terminal. Always activate your Python virtual environment (`source venv/bin/activate`) before running code to avoid dependency issues.
 
---
 
## Essential Linux Shell Commands
 
| Command            | What It Does                                      |
| ------------------ | ------------------------------------------------- |
| ls                 | Lists files and directories in the current folder |
| pwd                | Shows your current directory path                 |
| mkdir <name>       | Creates a new folder                              |
| cd <name>          | Moves into a folder                               |
| touch <file>       | Creates a blank file                              |
| cat <file>         | Displays the contents of a file                   |
| echo "text" > file | Writes text into a file                           |
| cp <src> <dst>     | Copies files or directories                       |
| mv <src> <dst>     | Moves or renames files                            |
| rm <file>          | Deletes a file                                    |
| rm -r <folder>     | Deletes a folder and its contents                 |
| nano <file>        | Opens a file in a terminal text editor            |
| ps aux             | Shows running processes                           |
| top                | Displays system resource usage in real-time       |
 
---
 
## Git: Version Control for Your Projects
 
Version control is at the heart of collaboration. Git allows multiple people to work on the same project without stepping on each other’s toes.
 
| Command                 | Purpose                                               |
| ----------------------- | ----------------------------------------------------- |
| git clone <url>         | Copies a repo from GitHub or another remote           |
| git pull                | Fetches and merges updates from the remote repository |
| git status              | Shows changes in your working directory               |
| git add .               | Stages all changes for commit                         |
| git commit -m "message" | Records changes locally with a message                |
| git push                | Uploads your commits to the remote repository         |
| git branch              | Lists all branches                                    |
| git checkout <branch>   | Switches to another branch                            |
| git merge <branch>      | Merges a branch into the current one                  |
| git log --oneline       | Displays a compact history of commits                 |
 
🔗 Resources:
 
* [Git Official Documentation](https://git-scm.com/doc)
* [GitHub Guides](https://guides.github.com/)
 
---
 
## Managing Packages with apt
 
Ubuntu comes with the **apt package manager**, which makes installing and updating software straightforward.
 
| Command                | Purpose                             |
| ---------------------- | ----------------------------------- |
| sudo apt update        | Refreshes the package list          |
| sudo apt upgrade       | Updates all installed packages      |
| sudo apt install <pkg> | Installs a new package              |
| sudo apt remove <pkg>  | Removes an installed package        |
| apt search <pkg>       | Looks for a package in repositories |
| apt list --installed   | Shows installed packages            |
| sudo apt autoremove    | Cleans up unused dependencies       |
 
📚 References:
 
* [Ubuntu Package Search](https://packages.ubuntu.com/)
* [APT User Guide](https://help.ubuntu.com/lts/serverguide/apt.html)
 
---
 
## Final Thoughts
 
By now, you should have:
 
* A running **KASM Workspace** with Ubuntu or Kali
* A **Git-enabled** project cloned and ready to go
* A Python **virtual environment** for isolated development
* **VSCode configured** as your main coding environment
