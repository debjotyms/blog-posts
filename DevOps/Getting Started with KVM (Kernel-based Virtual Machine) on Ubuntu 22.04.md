# Kernel Based Virtualization

Tags: Ubuntu

# Introduction

Are you interested in creating virtual machines on your computer? If so, Kernel Based Virtualization (KVM) might be just what you need. In this guide, we'll walk you through the process of setting up KVM on your Ubuntu 22.04 system. With KVM, you can run multiple operating systems simultaneously on your computer without needing separate physical hardware. We'll cover everything from installing KVM to creating virtual machines using both graphical and command-line interfaces. Additionally, we'll show you how to set up shared folders between your host and guest operating systems, connect your guest OS with a phone, clone virtual machines, add hard disks, and even migrate virtual machines between different systems. By the end of this guide, you'll have the knowledge and tools to harness the power of virtualization with KVM. Let's get started!

# **0. Prerequisites**

Before beginning the installation process, make sure that you fulfill the prerequisites:

- Pre-Installed Ubuntu 22.04
- 2 vCPUs & 4 GB RAM
- Stable Internet Connectivity

You can use other Linux distributions that support KVM. It’s totally up to you.

# 1. Install KVM and Enable Virtual Daemon

### 1.1: Update Your Ubuntu

Run `sudo apt update` before installing KVM. This command is like checking for updates on your computer. It makes sure your computer knows about the newest versions of software available to install. This helps keep your system secure by ensuring you get the latest security fixes and makes sure that when you install new software, everything it needs is there and up to date. It's an important step before installing or updating anything on your system.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled.png)

### 1.2: Check if Virtualization is Enabled

To verify whether your CPU supports KVM virtualization, you can run the following command:

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%201.png)

If the output is greater than 0, then congratulations! You can use KVM. If Virtualization is not enabled, be sure to enable the virtualization feature in your system’s BIOS settings.

### 1.3: Check for KVM Virtualization

In addition, you can verify if KVM virtualization is enabled by running the following command:

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%202.png)

If not, then install specific package using the returned command after running `kvm-ok`. After that, rerun the `kvm-ok` and if everything is okay, you will get this output. 

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%203.png)

### 1.4: Install KVM on Ubuntu 22.04

Now the real part. Let’s Install KVM. To do that, run the command and everything will be installed automatically.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%204.png)

### 1.5: Enable & Start Virtual Deamon

In this step, we will run 3 commands. First of all, using the `sudo systemctl enable --now libvirtd` command, we are enabling our `libvirtd` daemon for the libvirt virtualization toolkit, which provides a way to manage virtual machines on Linux. This command also ensures that this service will run automatically during system boot. 

The second command  `sudo systemctl start libvirtd` will start the previously enabled `libvirtd` daemon. Lastly, using the `sudo systemctl status libvirtd` we can verify whether our expected serviced (`libvirtd` in this case) is running as expected or not.  

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%205.png)

After enabling and running everything perfectly, now we need to add the currently logged-in user to the `kvm` and `libvirt` groups so that they can create and manage virtual machines. The `$USER` environment variable points to the name of the currently logged-in user.  To apply this change, you need to log out and log back again.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%206.png)

Keep that in mind, every time you create a new use in your host machine, you have to add the user to the `kvm` and `libvirt` groups using these two commands. 

# 2. Create a VM using VMM (GUI)

Till now we have done so many things. We have installed KVM, enabled the `libvirt` daemon, and also installed some other tools. VMM (Virtual Machine Manager) was one of them. In this part, I will show you how can you create a Virtual Machine using this VMM. If you guys are familiar with Oracle Virtual Box or Windows Hyper V, this VMM is almost similar to them.

**Step 1:** Open Virtual Machine Manager and Click on the “**Create a Virtual Machine**” button.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%207.png)

**Step 2:** Create a new VM using your own configuration. First of all, you have to choose your installation media. Then allocate necessary Memory, CPU and Disk Space. After giving all the information along with your VM name, click `Finish` and you are done.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%208.png)

If you selected an Ubuntu ISO, you would see this installation menu after booting up your newly created virtual machine. I am not going to show you the whole process of installing Ubuntu, as it is not the goal of this blog. You will find many other tutorials all over the internet. Search for tutorials according to the operating system you are going to install on your virtual machine.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%209.png)

# 3. Create a VM Using `virt-install` (CLI)

Creating a KVM-based virtual machine using the `virt-install` command-line interface (CLI) involves specifying various options to configure the VM. Below is an example command with explanations for each option:

```jsx
virt-install \
--name=my_vm \                       # Name of the virtual machine
--memory=2048 \                      # Amount of RAM in MB
--vcpus=2 \                          # Number of virtual CPUs
--cpu host \                         # Use host CPU model
--disk size=20 \                     # Disk size in GB
--cdrom /path/to/os.iso \            # Path to installation ISO
--os-variant=centos8 \               # OS variant (e.g., centos8, ubuntu20.04)
--network bridge=virbr0 \            # Networking configuration
--graphics vnc \                     # Graphics type (vnc, spice, none)
--console pty,target_type=virtio \   # Console configuration
--noautoconsole \                    # Do not automatically connect to console after creation
--wait=-1 \                          # Wait indefinitely for the installation to complete
--check all \                        # Check all options for errors before starting the VM
--extra-args="console=ttyS0"         # Extra kernel arguments for the installation
```

You may need to adjust the values for your specific use case. Once you have customized the options according to your requirements, execute the command. It will start the virtual machine creation process and launch the installation using the provided ISO file.

Remember to replace `/path/to/os.iso` with the actual path to your operating system installation ISO file.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2010.png)

After running this command, the VM will be created, and the installation process of the operating system will begin. Now again, install your desired guest OS by your own. I am not going to show you the whole process.

# 4. Make a Shared Folder Between Host OS and Guest OS (Using CLI)

To create a shared folder between the host (Ubuntu 22.04) and guest OS (Ubuntu 23.10) when using KVM, you can utilize the Virtio filesystem (`virtiofs`), or you can use a shared folder via Samba.

Here's how you can set up a shared folder using Samba:

### **4.1:** Install Samba on Host OS:

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2011.png)

### **4.2:** Create a directory for the shared folder

In this case, I am creating a folder named `public` on my `/data/` of Host OS using the `mkdir` command. After that, I created a new file named `file2` inside that public folder. Next, set proper permissions on the public directory:

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2012.png)

After all the commands, we have to restart `Samba` service to apply the change.

### 4.3: Configure Samba:

Edit the Samba configuration file `/etc/samba/smb.conf`. You can use any text editor you prefer, such as Nano or Vim. Add the following lines at the end of the file:

```
[Public]
comment = public share
path = /data/public/
browseable = yes
writable = yes
guest ok = yes
```

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2013.png)

Don’t forget to replace path = `/home/debjoty/Desktop/shared-folder` with your shared folder. Also, if you're unable to save changes to the Samba configuration file (**`/etc/samba/smb.conf`**) due to permission issues, you need to use a text editor with administrative privileges. Here's how you can do it using **`sudo`**:

```
sudo nano /etc/samba/smb.conf
```

This command will open the `smb.conf` file in the Nano text editor with elevated privileges. Once you've made the necessary changes (adding the [shared] section with its configurations), you can save the file by pressing Ctrl + O, then press Enter to confirm, and finally exit the editor by pressing Ctrl + X.

### 4.5: Restart Samba and Others

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2014.png)

### 4.6: Install Samba Client on Guest OS:

In order to access the Samba share, you will need to install the Samba client on the Linux system. You can install it using the following command:

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2015.png)

After Installing the Samba Client, run `sudo smbclient //samba-ip-address/public` . Here replace `samba-ip-address` with your Host OS IP Address.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2016.png)

Now using the command `ls`, you can see all the files from the public folder. Try adding more files and you will see the changes here in the Guest OS as well.

# 5. Connect the guest OS with a phone

You can easily mount your phone by adding your device through the VMM. It's super easy! After successfully completing the process, your device will automatically unmount from the host OS and mount on the guest OS.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2017.png)

# 6. **Clone a VM using `virt-clone` (CLI)**

The following example shows how to clone a guest virtual machine called "ubuntu23.10" on the default connection, automatically generating a new name and disk clone path. Notice that first time I run the command; I got an error. Because, you have to shut down your VM before cloning.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2018.png)

# 7. Add hard disks on VM (GUI)

To add storage to a cloned virtual machine using Open Virtual Machine Manager, begin by opening the program and right-clicking on the cloned virtual machine, then selecting "Open." Once opened, click on the "Add Hardware" button, choose "Storage" from the list of hardware types, and click "Forward." Next, select "Disk" and proceed by clicking "Forward." opt to "Select or create custom storage" and click "Forward" again. Click on "Manage" and then "Create Volume" to set up the new storage volume. Enter the details for the first hard disk as required and click "Finish" to complete the process, ensuring the added storage is successfully integrated with the virtual machine.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2019.png)

# 8. Add hard disks on VM (CLI)

### 8.1: Create `qcow2` Disc File

Before running the `virt-install` command, you need to ensure that the disk files you want to attach to the virtual machine are created and available at the specified paths. You can create empty disk files using tools like `qemu-img`. Here's an example command to create a qcow2 disk file:

```
sudo qemu-img create -f qcow2 /path/to/extra_disk1.qcow2 20G
```

I have created 2 different discs of 2GB size.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2020.png)

### 8.2: Attach this with VM

Now attach the newly created Disk using `virtsh attach-sidk`. Don’t forget to give the file path according to your `qcow2` directory.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2021.png)

# 9.  Migrate VM with Each Other

**Step 1:** Shutdown the machine you want to migrate and identify it’s `qcow2` file location. Here, I will share `ubuntu-debjoty.qcow2` with my friend.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2022.png)

**Step 2:** Get you friends `qcow2` file through pen drive, Google Drive or any other medium. It’s a time-consuming process as we have to copy a large size file. Download it locally to your computer.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2023.png)

**Step 3:** Run the migrated VM and you are good to go.

![Untitled](Kernel%20Based%20Virtualization%20d4d86688280d4369b685745a3dc7a118/Untitled%2024.png)