# Extras

## Copying Local Data to Windows Computer

To copy the local data from the computer I recomend doing so by removing the NVMe SSD from the computer.
This can be done by unscrewing the 4 philips screws on the bottom of the Beelink computer, then unscrewing the 
one philips screw holding down the M.2 NVMe SSD. Which can be then pulled straight out.

You will need an M.2 NVMe to USB converter to connect the SSD to your computer, an External NVMe enclosure will work too 
which can be bought at retailers like Best Buy or Walmart easily. Here is one example from amazon that is designed for quick
removal [FIDECO M.2 NVMe SSD Enclosure](https://a.co/d/5HVnMpZ) 

Now, your computer is not going to be able to read the drive by default since the drive is formated to a Linux only 
file system (likely EXT4 or BTRFS). What we can do is install something called WSL, or (Windows Subsystem for Linux)
which allows you to run Linux on your windows computer through just a terminal without having a separate volume you need to 
boot into or install. It works like a virtual machine but integrates itself within windows making it a lot easier to use.

Follow this link [Ubuntu - Microsoft Store](https://apps.microsoft.com/detail/9PDXGNCFSCZV?hl=en-us&gl=US&ocid=pdpshare) 
or, search for Ubuntu on the Microsoft Store app. Then click install, which will install WSL and Ubuntu onto your system.

When it is finished installing, open the start menu and search for **Ubuntu** which will open a terminal window where 
Ubuntu will run it's first time setup.

After a few minutes it should ask you to set up a username and a password. You can set this up as your own name and a 
password you would set up for your computer if you would like as this is not related to the wsprdaemon system.

Now, you should be sent to the BASH command line. 

From here, you can close the window (we will get back to ubuntu later). And plug in the NVMe from your Beelink into your
NVMe enclosure, then plug that into your computer. (I recommend using a high speed USB 3.0+/Super Speed Port which are usually
blue or have an "SS" icon silk-screened around it) 

Now, search for powershell in the windows start menu (don't open it yet) then, on the right side of the menu click open as 
administrator and click yes to the prompt. 

Now, in PowerShell type in the following command.

```powershell
GET-CimInstance -query "SELECT * from Win32_DiskDrive"
```

Which will list all of the drives connected to your system, including ones not formated for windows. In my case it looked like 
this,
```powershell
DeviceID           Caption                             Partitions Size          Model
--------           -------                             ---------- ----          -----
\\.\PHYSICALDRIVE2 Generic MassStorageClass USB Device 0                        Generic MassStorageClass USB Device
\\.\PHYSICALDRIVE3 ROG ESD-S1C SCSI Disk Device        2          500105249280  ROG ESD-S1C SCSI Disk Device
\\.\PHYSICALDRIVE0 MTFDKBA2T0QFM-1BD1AABGB             5          2048407280640 MTFDKBA2T0QFM-1BD1AABGB
\\.\PHYSICALDRIVE1 Generic MassStorageClass USB Device 0                        Generic MassStorageClass USB Device
```

Find the Physical drive with the highest number which should be the most recent drive plugged into your computer.

Now, type in this command replacing `\\.\PHYSICALDRIVE3` with the highest number from your list.

```PowerShell
wsl --mount \\.\PHYSICALDRIVE3 --bare
```
Which if all goes well should output the following,
```PowerShell
The operation completed successfully.
```

If you receive an error saying Administrator access is required, make sure to open powershell as an administrator.

Now, open Ubuntu again by searching for the program in the start menu.

Then type in the following to create a directory to mount the drive.
```bash
mkdir /mnt/beelink
```

Then type in the following command to list the drives detected by Ubuntu,
```Bash
lsblk
```

Which for me outputted this,
```Bash
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0 388.4M  1 disk
sdb      8:16   0     4G  0 disk [SWAP]
sdc      8:32   0 465.8G  0 disk
├─sdc1   8:33   0     1G  0 part
└─sdc2   8:34   0 464.7G  0 part
sdd      8:48   0     1T  0 disk /mnt/wslg/distro
```

Find the "NAME" with multiple sub partitions, which in my case is `sdc` with sub-partition `sdc1` and `sdc2`

Take note of the sub-partiton that has the largest size, which will be the main partition, in my case it is `sdc2` with 464.7GB

To double check you can run the following command replacing `sdc2` with the sub-partition you want to check.

```Bash
sudo blkid /dev/sdc2
```
Which outputted for me,
```
/dev/sdc2: UUID="0416fa66-0a6a-4bbc-949a-c399c7b1a26a" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="046bb50b-b343-4868-b6f9-ce8df5c87acc"
```

The part that says `TYPE="xxxx"` should show `TYPE="ext4"` which will mean that this should be the correct 
partition (it may also say `TYPE="btrfs"` depending on your specific beelink configuration)

Then once you think you have the correct sub-partition run this command to mount the drive, again replacing `sdc2` with 
your sub-partition.
```Bash
sudo mount /dev/sdc2 /mnt/sdr
```

Now, you can open a file explorer window and navigate to the tab on the left called `Linux` with an icon
of a penguin (the Linux mascot). Then select Ubuntu.

**You can also type this into the windows Run dialog by pressing** <shortcut>Windows + R</shortcut> **and typing in the following
and pressing enter**
```
\\wsl.localhost\Ubuntu
```

Now in file explorer you can navigate to `mnt` which will have the `beelink` drive mounted within.

Now, go into the `beelink` directory, navigate to `home` then `wsprdaemon` and `wsprdaemon` again.

(Full directory Path is `\\wsl.localhost\Ubuntu\mnt\beelink\home\wsprdaemon\wsprdaemon`)

Now you should be in the wsprdaemon main program directory, all archive files are stored in the `wav-archive.d` folder.
You can now copy this normally to your local computer to get the local data (this may have hundreds of GB).

When you are finished open another administor Powershell window and type in the following, Replacing `\\.\PHYSICALDRIVE3`
with the number you used before. This will unmount the drive safely from Ubuntu.

```powershell
wsl --unmount \\.\PHYSICALDRIVE3
```

Finally, Go to your taskbar and click the up arrow symbol at the bottom right near the Wi-FI icon to bring up the hidden 
system tray applications

![image_20.png](image_20.png)

Then click the icon that looks like a flash drive,

![image_21.png](image_21.png)

And click the name of the NVMe adapter you are using, this will now safely eject the drive from your computer allowing you to 
unplug the USB cable.

Now reinstall the SSD into the beelink by reversing the uninstallation instructions from before.

