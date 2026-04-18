# **Introduction to Shell**  

### ***Linux Shell (Overview)***

The Linux shell is a key interface for interacting with the system, especially on servers where Linux is widely used due to its stability and efficiency. It is essential for controlling and managing the operating system effectively.

The shell, also known as the terminal or command line, provides a text-based interface between the user and the system kernel, allowing commands to be executed directly.

It can be thought of as a powerful text-based control system used to navigate directories, manage files, and retrieve system information, offering far more control than a traditional graphical interface.

![[terminal.png]]

### **Terminal Emulators**  

Terminal emulators are software tools that simulate a physical terminal inside a graphical interface, allowing users to interact with the system through a text-based command line. They provide access to the shell while running within a GUI environment.

They act as a bridge between the user and the system, making it possible to execute commands, run programs, and manage the system without needing a physical terminal.

Some tools also extend this functionality, such as terminal multiplexers, which allow multiple sessions, windows, or workspaces inside a single terminal for better workflow management.

Together, terminal emulators and multiplexers make working in the command line more flexible, efficient, and organized.

![[CLI.png]]

### **Shell**   

The most commonly used shell in Linux is the `Bourne-Again Shell` (`BASH`), and is part of the GNU project. Everything we do through the GUI we can do with the shell. The shell gives us many more possibilities to interact with programs and processes to get information faster. Besides, many processes can be easily automated with smaller or larger scripts that make manual work much easier.

Besides Bash, there also exist other shells like [Tcsh/Csh](https://en.wikipedia.org/wiki/Tcsh), [Ksh](https://en.wikipedia.org/wiki/KornShell), [Zsh](https://en.wikipedia.org/wiki/Z_shell), [Fish](https://en.wikipedia.org/wiki/Friendly_interactive_shell) shell and others.

### **Bash Prompt**  

The Bash prompt is the text shown in the terminal that indicates the system is ready to receive commands. It typically displays key information such as the current user, hostname, and working directory.

It appears at the start of a new line with a cursor positioned after it, waiting for input.

The prompt helps users understand their current context in the system before executing commands.

It can be customized to provide useful information to the user. The format can look something like this:

```shell
<username>@<hostname><current working directory>$
```

The home directory for a user is marked with a tilde <`~`> and is the default folder when we log in.

```shell
<username>@<hostname>[~]$
```

The dollar sign, in this case, stands for a user. As soon as we log in as `root`, the character changes to a `hash` <`#`> and looks like this:

```shell
root@htb[/htb]#
```

For example, when we upload and run a shell on the target system, we may not see the username, hostname, and current working directory. This may be due to the PS1 variable in the environment not being set correctly. In this case, we would see the following prompts:

#### *Unprivileged - User Shell Prompt*

```shell
$
```

#### *Privileged - Root Shell Prompt*

```shell
#
```

### ***PS1 Variable (Bash Prompt Customization)  

The PS1 variable in Linux controls how the command prompt appears in the terminal. It acts as a template that defines what information is displayed whenever the system is ready for a new command.

It can be customized to show details such as the username, hostname, current directory, time, and even command status, making the terminal more informative and easier to use.

Advanced customization is done through shell configuration files like `.bashrc`, using special escape sequences such as `\u` for username, `\h` for hostname, and `\w` for the current working directory.

This allows users to personalize their terminal environment and improve efficiency, especially when working on complex tasks or system analysis.

![[PS1_vs.png]]

Customizing the terminal prompt and environment can improve both usability and efficiency by making key system information easier to access at a glance. It helps users better understand their current context while working in the command line.

Beyond the prompt itself, the terminal can also be personalized with different colors, fonts, and visual settings to create a more readable and comfortable workspace.

While the default setup already provides essential context (such as user, system name, and directory), customization allows users to adapt the environment to their workflow and preferences. Tools like prompt generators and themes such as Powerline can further enhance and simplify this process.

### **System Information (Overview)**

Understanding system information is essential when working with Linux, especially across different environments. It includes details about the system, processes, network configuration, users, and directories.

The terminal provides various built-in tools to gather this information, with help options like `-h`, `--help`, and `man` available for guidance.

This knowledge is important not only for everyday system usage but also for security purposes, such as analyzing configurations, identifying vulnerabilities, and assessing potential risks

![[system_infos_cmds.png]]

