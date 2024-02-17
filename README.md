# Born2beRoot

*The main goal for this project is to create a virtual machine using “VMware fusion”.*

## Okay, but what even is a virtual machine??

**In short - a virtual machine (VM) is a machine inside your machine.**

Virtualization is like having multiple computers running on a single computer. It allows you to run different operating systems and programs as if they were on their own separate computers, even though they are all running on the same physical machine.

Yeah I know, that definitely did not clarify anything… 

So we will start from the very basic. What even is a computer server and what are operating systems?

## The computer server and its components

A physical server has a number of hardware elements; such as a CPU (central processing unit), some RAM for temporary storage, a hard disk for long-term memory storage, a network card and much more.

**An operating system is installed on top of this** and can contain several different applications. 

The Virtual Machine will use the hardware of the machine it is running on (CPU, memory etc.), but everything inside will be different. 

You could for example install **Windows on a Mac, or Linux on a Windows**.

In order to achieve this you’d need a **hypervisor.**

The **VIRTUAL BOX** is the hypervisor we will be using for this project.

### The Hypervisor

Hypervisor =  a piece of software that enables a user to create and run one or more virtual machines simultaneously. 

It is known as the virtual machine monitor, or the VMM.

It controls and allocated the resources of the host machine to what VM needs (memory, CPU++), while also making sure that the VM’s does not interfere withh each other.

Virtual Box is a type 2 hypervisor, which means that it runs on top of a host OS. 

![With the help of the hypervisor Virtual Box - we can install several different operating on the same machine/hardware. ](Born2beRoot%20d6c460c44bce415198a743142af4ff81/Screen_Shot_2024-02-06_at_9.04.44_AM.png)

With the help of the hypervisor Virtual Box - we can install several different operating on the same machine/hardware. 

### The Operating System - OS

All machines runs on an **operating system -** a set of programs that allows us to run and control the machine. 

It is the interface between the user, the programs and the computer components.

For example - Apple machines run on macOS, while other machines may run on Windows or Linux.

The virtual machine also has to run on an operating system, which in this case will be Debian. 

### Debian

Debian was one of the very first Linux distributions and has been available since 1993. It offers a higher degree of control and customization of its configuration. 

## But what’s the point?

Virtual machines can be very helpful for several reasons. They are more **convenient and cheaper** than buying multiple computers to try different operating systems. Maintaining virtual machines is also **easier and less time-consuming** than maintaining physical machines.

It can be helpful if you for example are **developing an app and want to test it** on different operating systems.

When a physical server crashes, it can be difficult to recover the data it contained. However, **virtual machines simplify data backup.** While your virtual machine is running, you can create a backup called a snapshot. If something goes wrong, you can restore the virtual machine to its previous state using the snapshot.

Virtualization also **enhances data security by isolating services on different servers.** Each virtual machine is separate from the others, including the main host system. This **reduces the risk of malware spreading** if one virtual machine gets infected. If a virtual machine crashes, it does not affect the host or other virtual machines.

# File System in Linux

In Linux we have a file system that works something like this:

![Untitled](Born2beRoot%20d6c460c44bce415198a743142af4ff81/Untitled.png)

The main focus in this task is:

1. **/etc/** which is host specific configuration. 
A "configuration file" is a local file used to control the operation of a program; it must be static and cannot be an executable binary.
One example here is the ssh config files where we have the settings for opening and closing the ports. 
The etc folder can in a way be seen as a settings folder for the OS. 

2. **/boot** which is the static file of boot loader.

3. **/var/log/sudo** which will contain our sudo log file **(sudo_config)**. This is located under var because it is a log file and is expected to change continuously (variable). Cache files are also stored here. We don’t know the actual size of the file.

4. **/usr/local/bin** which is apart of shareable and read-only data and shows us the local software. Which in our case will keep the [monitoring.sh](http://monitoring.sh) file with our script. 

## Sudo configuration

There is two ways to configure the sudo specifications:

1. **`/etc/sudoers.d/` directory in a sudo_config file**:
    - **Organized Management**: Placing individual configuration files in the **`/etc/sudoers.d/`** directory allows for better organization of sudo configurations. Each file can contain specific rules or settings, making it easier to manage and understand the configurations.
    - **Granular Control**: You can create separate files for different users, groups, or applications, allowing for more granular control over sudo permissions.
    - **Safety**: Files in **`/etc/sudoers.d/`** are included as part of the **`sudoers`** policy and are subject to syntax checks performed by **`sudo`**. This helps prevent syntax errors that could potentially lock users out of administrative access.
2. **`sudo visudo`**:
    - **Direct Modification**: **`sudo visudo`** directly edits the main **`sudoers`** file (**`/etc/sudoers`**). While this provides immediate access to all configurations, it can become unwieldy for larger setups or when managing complex permissions.
    - **Syntax Checking**: **`visudo`** checks the syntax of the **`sudoers`** file before saving changes, helping prevent mistakes that could lead to system-wide sudo failures.
    - **Risk of Conflicts**: Editing the main **`sudoers`** file can lead to conflicts if multiple administrators are simultaneously modifying the file. This could potentially disrupt system administration tasks.

All in all it is better practice to use a separate sudo_config file, although in this project it is not strictly necessary. 

## LVM & Disk Partitioning

**Disk**: Imagine your computer's hard drive as a big piece of paper. It's blank and ready for you to use. But it's just one big piece, and you can't really organize things on it very well.

**Partitioning**: Now, imagine you fold that piece of paper into smaller sections, kind of like folding it into thirds or quarters. Each section is like a separate area on your hard drive. You can put different things in each section, like your games in one section, your school work in another, and your pictures in yet another. Partitioning helps keep things organized.

**LVM (Logical Volume Manager)**: Think of LVM like magic sticky notes you can stick on your folded paper. These sticky notes can change size and move around. So, if you need more space for your games, you can make that section bigger by moving the sticky note. If you don't need as much space for your school work, you can make that section smaller. LVM lets you be flexible and adjust things as you need without needing to fold and unfold the paper again.

<aside>
📓 **Short and sweet:**
A VM is a machine inside the host machine. It behaves exactly the same way as any other machine; with an OS and some applications.

**The advantages are many:**
- Inexpensive
- Saves physical space
- Less maintenance 
- Data backup simplified
- Increased security
- Good for testing applications and software developing

</aside>

**Some helpful articles and guides:**

[https://medium.com/@makhlouf.yasmine1/are-you-born-to-be-root-5005f303108a](https://medium.com/@makhlouf.yasmine1/are-you-born-to-be-root-5005f303108a)

[https://baigal.medium.com/born2beroot-e6e26dfb50ac](https://baigal.medium.com/born2beroot-e6e26dfb50ac)

[https://42-cursus.gitbook.io/guide/rank-01/born2beroot/install-your-virtual-machine](https://42-cursus.gitbook.io/guide/rank-01/born2beroot/install-your-virtual-machine)

[https://github.com/gemartin99/Born2beroot-Tutorial/blob/main/README_EN.md#1--download-the-virtual-machine-iso-](https://github.com/gemartin99/Born2beroot-Tutorial/blob/main/README_EN.md#1--download-the-virtual-machine-iso-)
