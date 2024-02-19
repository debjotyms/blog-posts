# Top 20+1 Linux Commands for Beginners

Tags: Ubuntu

Welcome to our guide on the top 20+1  Linux commands! Whether you're new to Linux or have been using it for a while, these commands are super handy. We'll show you how to use them step by step. So, let's get started!

### 1. `sudo`

Here `sudo` means **superuser do.** Whenever we try to do something sensitive, for example, creating or deleting a new user account, installing new software, or maybe modifying system configurations, we need to use `sudo` at the very beginning of our command. After that, it will ask for the user's password to get permission to do the task. This is kind of similar to the `Run as Administrator` on Windows.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled.png)

### 2. `sudo apt-get install vlc`

We use this command to install something. Here I am installing the VLC media player. Notice that I have used `sudo` at the beginning. Because to install something on Ubuntu, we have to run commands with Administrative Privileges. 

**Without `sudo`:**

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%201.png)

**With `sudo`:**

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%202.png)

### 3. `dpkg --list`

In Windows, if we want to see all the installed programs at once, we usually go to the **Control Panel > Programs**. In Ubuntu, we can do the same thing using the command `dpkg-list`. After running the command, we will get a long list of all installed packages of our system.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%203.png)

### 4. `sudo apt-get remove vlc`

Now If we want to remove an application (VLC for this example), we can use this command `udo apt-get remove <package name>`. Here in `<package name>` we have to mention the specific package that we want to remove. To know the correct package name, we can use the command `dpkg --list` to get a list of all the installed packages. Using this command will remove the `vlc` package but all its configuration files will still be there in the PC. 

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%204.png)

### 5. `sudo apt-get purge vlc`

If we want to remove a software completely from our PC along with its configuration files, we have to use `purge` instead of `remove`. That’s it! Super easy.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%205.png)

### 6. `date`

The `date` command is simple but very powerful. It is basically used to display or set the system date and time. We can display the date time according to our desired format. We just just have to mention it properly.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%206.png)

### 7. `df`

This command displays a table with details for each file system. It shows the device or file system name, total size, used space, available space for new files, the percentage of space used, and the mount point or directory where the file system is accessed. This helps users quickly understand how much space is remaining on their storage.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%207.png)

### 8. `uname -a`

The `uname -a` command provides detailed system information. It displays information about the **system kernel**, **network node hostname**, **kernel release**, **kernel version**, **machine hardware architecture**, and the **operating system**.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%208.png)

### 9. `top`

The `top` command in Ubuntu is similar to the Windows Task Manager. It provides a real-time overview of system resource usage and a list of running processes.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%209.png)

### 10. `uptime`

The `uptime` command is useful for quickly checking how long a system has been running and its current load status.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2010.png)

### 11. `ls`

The screenshot below shows the folders that I have inside my `Home` directory. We can to the same thing use the command line using the `ls` command.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2011.png)

The `ls` command shows a list of the files and directories in a directory.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2012.png)

The `ls` command has various options, allowing you to customize the output based on your requirements. For example, if we run the `ls -l` command, it displays information such as file permissions, owner, group, size, and modification time. In `ls -l`, `l` means long format.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2013.png)

### 12. `cd`

In normal user interface, to go inside a folder, we double click on the folder. In `CLI` we use this `cd` command to do the same. For example, if we want to go the directory `Desktop`,  we have to use the command `cd Desktop`. 

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2014.png)

Here `cd` means **Change Directory**. `cd ..` will take you the the previous directory.

### 13. `pwd`

`pwd` means **Print Working Directory**. This literally prints the current working directory, which is the directory our shell is currently in.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2015.png)

### 14. `cp`

The `cp` command is another powerful command that helps to copy a file and paste it to another directory. The screenshot below shows how we can copy a file **file.txt** from folder **A** to folder **B.**

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2016.png)

### 15. `mv`

`mv` command is used to move a file from one directory to another. Here is an example:

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2017.png)

In the example above, I move the `file.txt` file from folder `B` to folder `C`.

### 16. `rm`

It is a simple command that is used to remove a file from a directory.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2018.png)

### 17. `mkdir`

This command is used to create a directory. Below, I have create another folder `D` using the command `mkdir D`. Here `mkdir` means **Make Directory**.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2019.png)

### 18. `rmdir`

`rmdir` is used to remove a directory. Here I have removed the directory `D`.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2020.png)

### 19. `cat`

The `cat <file name>` command shows the content inside the file. We have to replace the `<file name>` with our desired file name. In this case, it’s `file.txt`.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2021.png)

### 20. `touch`

This command is used to create a new file. Suppose, we want to create a new file `file2.txt` inside the folder A. To do that, we have to run the following command:

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2022.png)

### Bonus. `cmatrix`

This is my personal favorite. To use this command, first, we have to install `cmatrix`. To do that, we have to run the command `sudo apt-get install cmatrix`.

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2023.png)

After the installation, if we run the command `cmatrix`, some magic will happen :)

![Untitled](Top%2020+1%20Linux%20Commands%20for%20Beginners%20df1e24714b20416598ca1b0ed641f2f3/Untitled%2024.png)