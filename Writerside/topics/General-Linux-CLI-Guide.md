# General Linux-CLI Guide

<show-structure/>

## Definitions and Background

**Linux** generally refers to any operating system that uses the [Linux/GNU Kernel](https://www.gnu.org/gnu/linux-and-gnu.en.html) (**Kernel** being the most basic part
of an operating system that manages processes and system resources)

**Ubuntu** is a specific **Distrobution (Distro)** of Linux based on a different distro called **Debian**.

The main difference between many Distro's is the default software installed on said system, generally the most important one
is it's default **Package Manager** which allows users to download virtually any software or program without needing to actually
go onto the internet through a browser and download an installer.

For example, to download firefox using the **apt** file manager (Ubuntu/Debian Package Manager), you would enter the 
following command.
```Bash
sudo apt install firefox
```

Now if your computer doesn't have a Graphical User Interface (GUI) installed, firefox is not very useful but if you did 
then you would have installed the complete program with one line of text.

> Fun fact, if you use Windows as your main Operating System, newer Windows versions have added a default package manager
> called **Winget** which can allow you to do the same thing using Windows. This allows you to bypass going through a browser
> and GUI installer that may be tedious.
> 
> For example to install firefox on Windows using Winget, open a powershell or command prompt window and enter the following command.
> `winget install mozilla.firefox`, this will prompt you to press `y` to accept terms and conditions the first time the command is 
> run. After this, you will probably get a prompt asking to run as an Administrator. Then you are done. After a few seconds
> firefox will be installed and can be searched for in the search bar like any other application. 
> 
> The format for the operation is `winget install company.product` to be more specific, or entering `winget install product` like `winget install firefox` 
> will work too but I recomend being specific since its less likely to install the wrong thing. If you don't know what the identifier
> is for an app you can use `winget search product` which will list out product ID's with similar names. Like Adobe Acrobat, which has a 
> long ID `winget install adobe.acrobat.reader.64-bit`, which you can find by using `winget search acrobat`
> 
{style=note}

## Navigating the Command Line Interface (CLI)

When you login to a linux server (or open a terminal window if you have a GUI)
you will be greeted with something called a **prompt**, this is where you will type in your commands.

The prompt tells you (usually) main 3 things, first is your username, second is your computer hostname, third is your current directory.

For example, in the context of wsprdaemon this would be your general prompt.

```Bash
wsprdaemon@hostname:~$
```
The `:` and `$` separate the different sections. Text will be entered after the `$`

### File System Structure

#### /Home
`~` is shorthand for your current user's home directory (Equivilent to C:\Users\MyUsername\ on Windows)
**Also directory is a synonym with folder in the context of computers**

The actual directory **path** for `~` in our case would be `/home/wsprdaemon` 

> Note that unlike Windows which uses backslashes
> to denote different directories, Linux and MacOS (Unix like systems) use forward slashes, this is why websites also use forward slashes
> for URL's since you are accessing a servers directory structure by changing the URL
{style=warning}

So `wsprdaemon@hostname:~$` is equivalent to `wsprdaemon@hostname:/home/wsprdaemon$

#### Root "/"
You may be confused at the lack of a drive letter if you are used to Windows where the main OS drive is labled as 
`C:\`. This is because Linux (and MacOS) do not use drive letters, instead it will **mount** additional drives to directories/folders
which will act identically as if they were any other directory. The operating system itself is mounted to the "root" directory
denoted by a forward slash `/`. All other drives, and directories connected to the computer are accesed by changing to a sub-directory of the root directory.
This is why all file paths will begin with `/` Eg. `/home/wsprdaemon` The home folder *generally* is located on the same drive/partition as the root directory, however, 
this is not always the case as separating them can help prevent corruption. 

> A *Partition* refer to sectioning a hard drive into **partitions** which will each act as a seperate hard drive, 
>and may have different file systems formated to them creating a **volume**. Eg. The Windows OS *Partition* is formated to
>a **NTFS**  *Volume* labeled as `C:\`, while there is a seperate partition on the drive that is used to allow the computer's
>BIOS to boot into Windows called the **EFI** volume which is formated to **FAT32**, however, this volume does not get mounted (assigned a drive letter)
>in Windows systems by default, which is why you normally cannot see it. 
>
>Linux also needs an EFI volume to boot, however, this usually is mounted by default to the location `/boot`

#### /mnt
If you connect an external drive or flash drive to linux it will usually be mounted in the `/mnt` directory **Note it can actually 
be mounted anywhere you want but external drives are conventionally placed here so it is understood to be an external drive and not 
a normal directory**

In MacOS, drives get mounted to the `/Volumes` directory for the same reason. 

> Fun Fact, the reason that the OS drive in Windows is assigned the letter **C** is because before modern Windows systems
> during the 90's when Windows was still based on MSDOS Command Line Based OS. The **A** and **B** drives were reserved for 
> floppy disks (Which is generally what MSDOS ran off of), leaving Hard Disk Mass Storage devices to start at the letter **C**
> Since at the time Hard Disks were usually add-ons, rather than required.
> 
> You can still mount drives to the **A** and **B** letters if you format a drive using the Disk Management tool, however,
> file explorer may feel weird as the extra drives will show up before the **C** drive in the computer view.
{style=note}

#### /bin

`/bin` is where system-wide **Binary Executables** (.exe equivalent files) are stored, basically any program you install will have its executable
program file stored here.  **System-Wide** meaning all users can access the program. (Kind of like installing a program in 
windows for all users which requires Admin permission, and will install the program into the `C:\Program Files (x86)` folder for 32-bit applications
and `C:\Program Files` for 64-bit applications)

Some programs that are installed by a user without administrative permissions will instead 
store their executable file in `/usr/bin/` (Which is kind of like installing a program in windows for only one user vs system-wide which 
will install the program into the user's appdata folder)

**Most files you may see that do not contain a file extension, are generally a program executable file on Linux. Although, executables
could have any file extension but it is convention to leave out any extension to denote an executable.**

#### /dev

Like the `/mnt` directory that allows drives to be mounted as if they are a directory/folder. `/dev` refers to a hardware device
which could be anything (including our rx888 radio reciever used for wsprdaemon). You will usually see `/dev` instead being used
in the context of unmounted disks/partitions as to mount a partiton you need the device name. For example `/dev/nvme0` refers to the 
entire disk, while `/dev/nvme0n1p1` just refers to the first partition on the disk. 

**NVMe is a SSD protocol usually used with the M.2 connector which is also what many people call these types of drives** 
You may also see `\dev\sda` representing older SATA or SCSI interfaces used in mechanical 2.5" and 3.5" HDDs or some older 2.5" SSDs.

#### /etc

`/etc` is where most System-Wide program configuration files are stored to configure and modify programs operation.

There is also a user equivilent `/usr/etc` for non-system-wide program installations.

#### /usr

Despite its name, do not confuse `/usr` to the `C:\Users` directory in Windows, as this is where non-system-wide programs 
are installed for specific users (closer to the appdata directory in Windows).

#### /tmp

As it's name suggests, this is a directory for temp files or cache files which can be deleted when not in use anymore.

#### /run

`/run` stores information regarding currently running programs.

#### /var

`/var` stores other data files, including logs and cache files.



There are other top level directories but these are the main ones you may see referenced regularly.


### Commonly Used Commands


#### Print Working Directory [pwd]

You can double check which directory you are in by entering the following command `pwd` which stands for "print working directory"
```Bash
wsprdaemon@hostname:~$ pwd
```
Which will output 
```Bash
/home/wsprdaemon
```

#### Make Directory [mkdir]

As its name suggests, use this command to create a directory. If you do not specify a full path 
to the directory from the **root** directory, it will assume you are operating in the same directory you are working in.

```Bash
wsprdaemon@hostname:~$ mkdir test
```
will, create the directory `/home/wsprdaemon/test` or usually denoted `~/test`

#### List [ls]

This command will print all directories and files in your current working directory.

Utilizing the previous example,
```Bash
wsprdaemon@hostname:~$ ls
```

will print out 

```Bash
test
```

Adding a path after typing in ls will list the contents of the specific directory.

Eg. 
```Bash
wsprdaemon@hostname:~$ ls /
```
Will print out something like this,
```Bash
bin                cdrom  home               lib64       mnt   root  sbin.usr-is-merged  sys  var
bin.usr-is-merged  dev    lib                lost+found  opt   run   srv                 tmp
boot               etc    lib.usr-is-merged  media       proc  sbin  swap.img            usr
```

Directories, files, and executables will all usually be colored differently in the command line to denote the difference.

Adding in the `-a` flag will also include hidden files **hidden files generally will begin with a period, Eg. `~/.config` which is a
common hidden directory in the user's home folder that usually contains specific configuration files for customization. This
directory will not show up unless you add the `-a` flag `ls ~/ -a` for example.


>Important note. You may come across a item named `name.d`, this usually refers to a configuration file that has an
> associated directory which you could add a file to which will be equivalent to adding that text to the overall configuration file.
> Eg. There is a configuration file at the location `/etc/sudoers` which configures the administrator permissions for a system, 
> however having to modify a file this important is risky as you don't want to accidentally delete something you were not supposed to.
> So, instead you can add a file to the `/etc/sudoers.d/` directory, which will effectively append any text file located in itself 
> to the `/etc/sudoers` file. (It does not actually modify the file but the system considers the directory contents as a part of the file)
> 
> A `.d` directory may also just mean that a directory is related to something else with the same name, but it does not nessisarily 
> need to be a configuration file. Eg. `wsprdaemon/wav-archive.d` directory which stores the PSWS archived wav audio files.
> 
{style=note}

#### Change Directory [cd]

To change you directory you can enter the command `cd` to "change directory".

so,
```Bash
wsprdaemon@hostname:~$ cd test
```
will move you into the `~/test` directory.
so this is what the terminal would look like.

```Bash
wsprdaemon@hostname:~$ cd test
wsprdaemon@hostname:~/test$ pwd
/home/wsprdaemon/test/
```

> Important Note, to move up a directory you can use the shorthand `..` (or `../`) for example, `cd ..` would move you from the 
> `/home/wsprdaemon/test/` directory, back to the `/home/wsprdaemon/` directory. Running the same command again would 
> move you to the `/home` directory. 
> 
> Other commands also work using the same convention, if you were in the `/home/wsprdaemon` directory. Running `ls ..`
> would list the contents of the `/home` directory.
> 


#### Remove [rm]

This command will delete a file or directory. 

To do so, run `rm` then then name of the file you would like to delete.

```Bash
rm test.txt
```

To delete a non-empty directory use the `-r` flag to recursively delete 

If directory `~/test` contains `~/test/test1.txt`
```Bash
rm -r ~/test
```
Will delete both the directory `~/test` and the file `~/test/test1.txt`

**You may also need to add the `-f` flag if a file is in use or is write protected (excluding permission blocked items)**

If you do not own the file however, you need to use `sudo` (pronounced sue doh) to run the action as the root user (equivilent to the administrator user on windows), 
an account with access to **sudo** is called a **Super User**. So, **sudo** stands for Super User Do.

Eg.

```Bash
sudo rm -rf ~/ImportantTest
```

Will erase the directory `~/ImportantTest` without any care for what is inside ()

> Important, be ***Very*** careful when using `sudo rm -rf` as it can and will delete anything.
> You may come across someone online who says to run `sudo rm -rf  --no-preserve-root /`. Never run this command, as this
> will delete your entire computer. It is essentailly the equivilent to someone telling you to delete `C:\Windows\System32` 
> on Windows, as it will destroy your operating system. (Although the linux one is arguably worse as it will delete your 
> data on top of the OS files, since System32 only contains OS files and no user data)
{style=warning}

#### touch
`touch` is used to create an empty file.

So,
```Bash
touch test.txt
```
will create an empty text file named test.txt in your current directory.


#### echo, >> and |

Echo is equivilent to the print command in python, so `echo "test"` will print out text.

This may seem redundant but it is used in scripts to display information to the user when you run it, or you can use it in 
combination with other things like the stream operator [>>] to insert text into a file.

Eg.
```Bash
touch test.txt
echo "Hello World!" >> test.txt
```
Will create a file named `test.txt` with the text `Hello World!` inside it.

The stream operator is useful if you have a command that outputs too much text which causes some of the output to get cut off 
as you can use it with any command and the output will be passed into the file.

Eg. 
```Bash
ls ~/ >> test.txt
```

will insert the output of the command `ls ~/` into the text file `test.txt`

The pipe operator `|` is similar, however, it instead allows you to use the output of one command as the input of another.

Eg.
```Bash
ls ~/ | less
```
Will open the output of `ls ~/` in the program **less** which is a program used to view text or text documents without 
editing them, and includes scrolling support. 


#### cat

Running `cat` and appending the command with a text file name will print the contents of the file into the terminal.

Eg. 

```Bash
cat test.txt
```
will print out the content of `test.txt` straight into the console.



