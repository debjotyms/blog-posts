# Top 20+1 Linux Commands for Beginners

Tags: Ubuntu

Welcome to our guide on the top 20+1  Linux commands! Whether you're new to Linux or have been using it for a while, these commands are super handy. We'll show you how to use them step by step. So, let's get started!

### 1. `sudo`

Here `sudo` means **superuser do.** Whenever we try to do something sensitive, for example, creating or deleting a new user account, installing new software, or maybe modifying system configurations, we need to use `sudo` at the very beginning of our command. After that, it will ask for the user's password to get permission to do the task. This is kind of similar to the `Run as Administrator` on Windows.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/sudo.png?raw=true)

### 2. `sudo apt-get install vlc`

We use this command to install something. Here I am installing the VLC media player. Notice that I have used `sudo` at the beginning. Because to install something on Ubuntu, we have to run commands with Administrative Privileges. 

**Without `sudo`:**

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/sudo_apt_get_install%20_vlc_with_sudo.png?raw=true)

**With `sudo`:**

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/sudo_apt_get_install%20_vlc_without_sudo.png?raw=true)

### 3. `dpkg --list`

In Windows, if we want to see all the installed programs at once, we usually go to the **Control Panel > Programs**. In Ubuntu, we can do the same thing using the command `dpkg-list`. After running the command, we will get a long list of all installed packages of our system.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/dpkg_list.png?raw=true)

### 4. `sudo apt-get remove vlc`

Now If we want to remove an application (VLC for this example), we can use this command `udo apt-get remove <package name>`. Here in `<package name>` we have to mention the specific package that we want to remove. To know the correct package name, we can use the command `dpkg --list` to get a list of all the installed packages. Using this command will remove the `vlc` package but all its configuration files will still be there in the PC. 

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/sudo_apt_get_remove_vlc.png?raw=true)

### 5. `sudo apt-get purge vlc`

If we want to remove a software completely from our PC along with its configuration files, we have to use `purge` instead of `remove`. That’s it! Super easy.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/sudo_apt_get_purge_vlc.png?raw=true)

### 6. `date`

The `date` command is simple but very powerful. It is basically used to display or set the system date and time. We can display the date time according to our desired format. We just just have to mention it properly.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/date.png?raw=true)

### 7. `df`

This command displays a table with details for each file system. It shows the device or file system name, total size, used space, available space for new files, the percentage of space used, and the mount point or directory where the file system is accessed. This helps users quickly understand how much space is remaining on their storage.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/df.png?raw=true)

### 8. `uname -a`

The `uname -a` command provides detailed system information. It displays information about the **system kernel**, **network node hostname**, **kernel release**, **kernel version**, **machine hardware architecture**, and the **operating system**.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/uname_a.png?raw=true)

### 9. `top`

The `top` command in Ubuntu is similar to the Windows Task Manager. It provides a real-time overview of system resource usage and a list of running processes.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/top.png?raw=true)

### 10. `uptime`

The `uptime` command is useful for quickly checking how long a system has been running and its current load status.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/uptime.png?raw=true)

### 11. `ls`

The screenshot below shows the folders that I have inside my `Home` directory. We can to the same thing use the command line using the `ls` command.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/ls_desktop.png?raw=true)

The `ls` command shows a list of the files and directories in a directory.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/ls_cli.png?raw=true)

The `ls` command has various options, allowing you to customize the output based on your requirements. For example, if we run the `ls -l` command, it displays information such as file permissions, owner, group, size, and modification time. In `ls -l`, `l` means long format.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/ls_cli_l.png?raw=true)

### 12. `cd`

In normal user interface, to go inside a folder, we double click on the folder. In `CLI` we use this `cd` command to do the same. For example, if we want to go the directory `Desktop`,  we have to use the command `cd Desktop`. 

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/cd.png?raw=true)

Here `cd` means **Change Directory**. `cd ..` will take you the the previous directory.

### 13. `pwd`

`pwd` means **Print Working Directory**. This literally prints the current working directory, which is the directory our shell is currently in.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/pwd.png?raw=true)

### 14. `cp`

The `cp` command is another powerful command that helps to copy a file and paste it to another directory. The screenshot below shows how we can copy a file **file.txt** from folder **A** to folder **B.**

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/cp.png?raw=true)

### 15. `mv`

`mv` command is used to move a file from one directory to another. Here is an example:

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/mv.png?raw=true)

In the example above, I move the `file.txt` file from folder `B` to folder `C`.

### 16. `rm`

It is a simple command that is used to remove a file from a directory.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/rm.png?raw=true)

### 17. `mkdir`

This command is used to create a directory. Below, I have create another folder `D` using the command `mkdir D`. Here `mkdir` means **Make Directory**.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/mkdir.png?raw=true)

### 18. `rmdir`

`rmdir` is used to remove a directory. Here I have removed the directory `D`.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/rmdir.png?raw=true)

### 19. `cat`

The `cat <file name>` command shows the content inside the file. We have to replace the `<file name>` with our desired file name. In this case, it’s `file.txt`.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/cat.png?raw=true)

### 20. `touch`

This command is used to create a new file. Suppose, we want to create a new file `file2.txt` inside the folder A. To do that, we have to run the following command:

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/touch.png?raw=true)

### Bonus. `cmatrix`

This is my personal favorite. To use this command, first, we have to install `cmatrix`. To do that, we have to run the command `sudo apt-get install cmatrix`.

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/cmatrix_install.png?raw=true)

After the installation, if we run the command `cmatrix`, some magic will happen :)

![Untitled](https://github.com/debjotyms/blog-posts/blob/main/DevOps/resources/Top%2020+1%20Linux%20Commands%20for%20Beginners/cmatrix_run.png?raw=true)