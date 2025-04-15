# Install Wsprdaemon

<show-structure/>

## 0.5: BIOS Settings
Before setting up the system with an operating system it is recomended to configure the following BIOS/Firmware settings to 
allow better operation of the Beelink computer.

<procedure title="Entering the BIOS Setup Screen" id="BIOS-id">
    <step>Plug in the computer and connect and HDMI or Display Port between the computer
            and your monitor.</step>
    <step>Press the power button to turn on the PC, then quickly tap
            <control>Delete</control> on the keyboard.</step>
    <p>You should now be in the BIOS setup screen.</p>
</procedure>

<procedure title="Configuring the BIOS Setup" id="BIOS-config">
    <step>Using the arrow keys, open the <ui-path>Advanced</ui-path> tab.</step>
    <step>Move down to <ui-path>Smart Fan Function</ui-path>, and press <control>Enter</control> to 
        enter the sub menu.</step>
    <step>Select <ui-path>Smart CPU_Fan Mode</ui-path> using <control>Enter</control>, and move the cursor
        up to <ui-path>Full on Mode</ui-path>. Now press <control>Enter</control> to select it.</step>
    <step>Press <control>Escape</control> to exit the sub menus, until you reach the <ui-path>Advanced</ui-path> tab 
        again.</step>
    <step>Move down to <ui-path>AMD CBS</ui-path> and enter the sub menu.</step>
    <step>Move to and select <ui-path>FCH Common Options</ui-path> </step>
    <step>Now, move down to <ui-path>Ac Power Loss Options</ui-path> and press <control>Enter</control>.</step>
    <step>Finally, press <control>Enter</control> over <ui-path>Ac Loss Control</ui-path>, and move the
        cursor down to <ui-path>Always On</ui-path>. Then, hit <control>Enter</control> again to select it.</step>
    <step>Move back to the <ui-path>Advanced</ui-path> tab using <control>Enter</control>.</step>
    <step>Finally, move over to the <ui-path>Save & Exit</ui-path> tab, and move down 
        to <ui-path>Save Changes and Exit</ui-path>.</step>
    <step>Press <control>Enter</control> over <ui-path>Yes</ui-path>, to confirm changes.</step>
    <p>This will configure the computer to automatically turn back on in the event of a power outtage, 
        well as setting the internal fans to always full speed. (To prevent overheating issues)</p>




</procedure>

## 1: Install the Operating System

### Youtube Video Walkthrough Link
[Youtube Video Walkthrough Link](https://youtu.be/JZvuR3WRL-Q)
This is a link to a video walkthrough, however, I recommend to using primarily this document as I speed through
the setup pretty quick.


First before we can set up any software we need to install the OS, in this case Ubuntu.

Go to this download link and download the newest version of Ubuntu Server, for my installation I am using 24.04.1

The file will be a .iso file indicating it is a disk image.
[](https://ubuntu.com/download/server)

### 1.1: Flashing the Installation Media

Next download a program to flash the disk image to an external disk.

<tabs>
<tab title="Balena Etcher (Recomended)">
For MacOS I recomend using Balena Etcher although Balena works for Windows as well.

[Balena Etcher](https://www.balena.io/etcher)

Once you have installed Balena Etcher grab a USB flash drive, It should be at least 8 GB.

- First plug in the flash drive and open Balena Etcher
- Next select "Flash from file" which will open a file browser window
- Navigate to the location of the disk image (.iso) and select it
- Then, select "Select Target"
- Click the check mark of the flash drive you will be using.
- Finally Click "Flash!" and wait until the process finishes

</tab>
<tab title="Rufus (Windows Only)">
For Windows I recommend downloading Rufus but Balena Etcher also works

[Rufus](https://rufus.ie/en/)

Once the program is installed grab a USB flash drive, It should be at least 8 GB.

- First plug in the Flash drive into a free USB port on your personal computer
- Next open Rufus and press the "Select" Button towards the top right of the screen.
- Then, Select your flash drive from the dropdown at the top of the screen labeled "Device"
- Next make sure that towards the bottom, under "File System", that Fat32 is selected rather than NTFS
- Now select the "Start" button on the bottom right.
- Select "OK" to the prompt telling you the flash drive will be erased
- You may see a screen after this telling you there are two different ways the drive can be formated, select the default.
- Later if you see issues try the other option.

</tab>
</tabs>

> **If you are Using Windows**
>
> While the operation is running you will start to see errors from file explorer stating that you
> have plugged in multiple drives that need to be formated.
>
> Ignore these messages and close out of the windows, **Do Not Click Format** on any of the popups.
>
{style="warning"}

Once the operation has completed eject the drive and remove it from your system.

### 1.2: Starting the OS Installation

Plug the flash drive into the computer you will be using as the server, with it turned off.

Now plug in a Keyboard (You will not need a mouse)

Now turn on the computer and immediately and repeatedly press the <control>F7</control> Button quickly
if you are using the recommended Beelink mini PC.

If you are using something else you may need to look up what
that computer's hotkey is to enter its "Boot Menu".

Now that you are in the boot menu select the USB flash drive,
if the screen shows an option that says UEFI and one that doesn't,
select the one that says UEFI.

Now that the computer is starting up you should see menu that asks
if you would like to "Try or Install Ubuntu" and a few other options.

![Install-2.png](Install-2.png)

<p> Select the option labeled <ui-path>Try or Install Ubuntu Server</ui-path> with <control>Enter</control>.</p>

You should see a bunch of text flying up the screen, this is normal. After a little bit you should
see something like this.

![Install-1.png](Install-1.png)

**Using the arrow keys** move the green cursor to English then press <control>Space</control>

Next you will see a screen asking you to select your Keyboard layout, leave the default options
and select done with <control>Space</control>

<p>On the next screen you will see a few options, using the arrow keys move the cursor up to the section
labeled <ui-path>Ubuntu Server (minimized)</ui-path> and press <control>Space</control> to select it.</p>

![install-3.png](install-3.png)

Move the cursor down and select done using <control>Enter</control>.

### 1.3: Next you need to connect the system to Wi-Fi.

***Skip if using ethernet***

Next if you are doing this on the NJIT campus

On the screen you should see a section called "wlo1", and text underneath
that says disabled. Underneath this text is some text that will look like
this `12:34:a5:b6:7c` with different values. This is the MAC address
of the computer or its network "Hardware ID". Write down this number
and save it for later.

Navigate on your personal computer to this website,
make sure you are connected to the network NJITsecure, and
doing so **Without a VPN** turned on.
[](https://myiot.validate.njit.edu/)

Type in your UCID to login. Once logged in, select add.

Type in a name for the device something like "Server" will do
but it is up to you. On the next line under "Device ID"
type in the MAC address you wrote down earlier. Then click "Register
Device"

Now go back to the server

Move the cursor up to "wlo1" and press `Space` to select it. Move the cursor down
to "Edit Wifi" and press `Space`. Next Move the cursor down to "Choose a visible network"
and press `Space`.

Next move the cursor to NJIoT and select it. Now move down to
"Password:" and enter "mythings" as the Wi-Fi password.

Now wait a few seconds for it to connect. Then move the cursor down
to done and select it.

On the next screen you will be asked to enter a proxy address,
leave this blank and select done.

Next the screen will start to test the network, wait a minute or two
until the top of the screen reads "This mirror location passed tests."

Then select done.

You will likely get a message reading that there is an update
to the installer and asks if you would like to update.
Move the cursor up to "Update to the new installer" and select
it with `Space`.

You may need to wait a few minutes, then you will see a screen asking
for the storage configuration.

![Install-4.png](Install-4.png)

Move down and de-select the option labeled <ui-path>Set up this disk as an LVM group</ui-path> using 
<control>Space</control>. 

**Make sure there is no X in the brackets**

Leave the <ui-path>Use an entire disk</ui-path> option enabled, which will erase the whole
internal drive of the computer. Then, Select done.

You will see a summary of the storage configuration, select <ui-path>done</ui-path>.

Next you will see a warning confirming destructive action,
move the cursor to continue and select it with <control>Space</control>.

Next you will see a screen asking to set up the default account,
I recommend the following configuration. 

***The username should be "wsprdaemon"***

![image_7.png](image_7.png)

>Whatever you choose, make sure you write down the username
>and the password you create as this is very important.
>
{style="warning"}

Once you have made your choices, select done.

On the next page you will be asked about upgrading to ubuntu
pro, leave the default option of skip for now and continue.

Next you will see a menu for SSH configuration. move to
"Install OpenSSH server" and select it with <control>Space</control>`

![Install-6.png](Install-6.png)

>This next part is *optional* but **Highly** recommended
> as making sure your server is secure is important.
> If you do not want to include an SSH Key if you plan to not use
> SSH or if you are fine with remote login using only a password
> select `Done` to continue.
>
{style="note"}

### 1.4: Configuring SSH Keys

***Optional but recommended***

**SSH** Is a tool that allows you to login to a server remotely
while only needing to be connected to the same network.

This can be very useful as having a dedicated monitor for the
server can take up a lot of space. Copying commands into the
terminal can also be more difficult without SSH.

#### 1.4.1: Installing OpenSSH to your PC

***Optional but recommended***

<tabs>
<tab title="Windows">

**Open the Terminal application, or Windows Powershell.**, then enter the following command
```powershell
winget install Microsoft.OpenSSH.Beta
```

</tab>
<tab title="MacOS/Linux">

**OpenSSH should already be installed so this part can be skipped.**

</tab>
</tabs>

Now once you have OpenSSH installed enter the following command.

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
It Will then print the following

```
Enter file in which to save the key (C:\Users\<Your Username>/.ssh/id_ed25519):
```
or with the equivilent filepath on MacOS or Linux to the directory located at
`~/.ssh` (Note that a `.` prefix indicated the directory or file is hidden)

The terminal will output something along these lines.
```
Your identification has been saved in C:\Users\Jeremy/.ssh/test
Your public key has been saved in C:\Users\Jeremy/.ssh/test.pub
The key fingerprint is:
SHA256:bSXd+FlDb0c67iI/6qGnL40mWs0uMaPbaEENRVkXjVM jeremy@DESKTOP-POT9A12
The key's randomart image is:
+--[ED25519 256]--+
|     ooo. o=E  ..|
|    . .  .o..o.o.|
|     o    ..+ +.=|
|    . .  . o o =o|
|   .    S o   +  |
|    . +o .   .   |
|     o.+ooo . .  |
|    o+o.+.o+..   |
|   .+o.++*+...   |
+----[SHA256]-----+
```

Now type in the following line replacing the path with the path that was listed above
on this line `Your public key has been saved in C:\Users\Jeremy/.ssh/test.pub`

```Bash
cat C:\Users\Jeremy/.ssh/test.pub
```
Now copy or take note of the output for use later which will look something like this
```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIOSp7JlrnvRR8xdp1TygTogTGCkWj9zDEYS0D5VCa+He jeremy@DESKTOP-POT9A12
```

Now create a [GitHub Account](https://github.com/signup)

Once you have created your account go to settings and the tab labeled [SSH and GPG keys](https://github.com/settings/keys)

Now click the button that says `New SSH key`

Title it SDR server or something else that can identify the key.
Leave the *key type* as Authentication Key

Under the text box labeled **key**, enter the line you copied earlier that begins with **ssh-ed25519**

Then press `Add SSH key`

Now go back to the SDR server and select the `[ Import SSH Key ]` option.

![image.png](image.png)

Now enter the GitHub username you created (note this is not your email, it is a username you created without spaces)

If you go to your profile it will be under your name as subtext.

![image_4.png](image_4.png)

![image_2.png](image_2.png)

Then select `Done`

You should get a notification with something along the following. Select `Yes`

![image_3.png](image_3.png)

This has now preconfigured SSH for the installation.

### 1.5: Finalizing Installation

Then, move to done and select it.

You will next see a screen that may or may not list third party
drivers, select any if applicable and select continue.

The next screen will give you several extra software that can be installed
on the system, these should not be installed so you can select done.

The system will now start installing, this processes may take 5-10 minutes.

When it has finished a button will appear that says "Reboot Now"
select it.

You will see a screen that says "Please remove the installation media
then press enter", remove the flash drive then press enter.

The system will now restart.

## 2: Configuring the System

You will be asked to login to the system.

Enter the username you created earlier, then the password.

> Note that the password will not display any characters being
> typed
>
{style="note"}

You are now logged into the system.

Start by updating the preinstalled software and operating system.

Enter the following commands.

```bash
sudo apt update
sudo apt upgrade
```

You will be asked to enter the password to your account.

After each command runs you will see a lot of text run across the screen
showing what is happening. Wait until you see `wsprdaemon@sdrpc:~$`
which is the terminal prompt indicating you can enter a command again.

You also may see a question asking if you would like to continue,
enter `y` and press enter.

Wait a few minutes for the software to install.

Now run the following commands to disable a system component called snap. This a type of software management tool that 
we do not want running on our system since it will auto-update some programs which can cause issues with our automated scrips.

```Bash
sudo apt autoremove --purge snapd gnome-software-plugin-snap
sudo apt-mark hold snapd
```

### 2.1: Configuring Network for WPA2-Enterprise (University/Eduroam Wi-Fi)

You may have connected the system to ethernet or for NJIT used the
NJIoT Wi-Fi, but this network is not ideal for the server so we need to change it.
If you continue to use ethernet or are using a WPA Personal Wi-Fi (Only a Wi-Fi password to login no username)
you do not need to do this step but if you  plan to place the server somewhere without a LAN connection, and you did not setup the Wi-Fi
in the preinstallation environment and are at a University use this process.

Enter the following command.

```bash
sudo apt install network-manager
```

Once the package has installed enter the following.

```bash
sudo sytemctl disable systemd-networkd.service
sudo systemctl mask systemd-networkd.service
sudo systemctl stop systemd-networkd.service

sudo systemctl disable systemd-networkd.socket
sudo systemctl mask systemd-networkd.socket
sudo systemctl stop systemd-networkd.socket
```

Then enter the following

```bash
ip a
```

#### 2.1.1 Network-Manager Terminal UI [nmtui]
The following is the configuration to setup and activate a WPA-2 Enterprise connection, however, depending on your network
or personal prefrences it may be easier to use the **Terminal User Interface** version of network-manager. I will not explain this one 
as going over the interface is a bit harder to do using text but it may be easier to understand how to use this interface as it is 
very similar to the one used in the Operating System set up screen from Part 1.

Launch Network-Manager TUI
```Bash
sudo nmtui
```

Otherwise, I recommend following the next steps, which describe using the Network-Manager Command Line Interface.

#### 2.1.2 Network-Manager Command Line Interface [nmcli]

The output should contain a few lines including `lo`, `enp1s0`, `wlo1`, or similar.

Look for the item starting with `w` which may be `wlo0`, `wlo1`, `wlan0`, `wlan1`, or similar.
This is the Wi-Fi card device ID.

Then enter the following, replacing `wlo1` with the Wi-Fi card ID that was on your system,
and `NJITsecure` with the SSID of your Wi-Fi network. (SSID just being the name of the network when it shows up in settings
on your computer or phone)

```bash
sudo nmcli con add type wifi ifname wlo1 con-name NJITsecure ssid NJITsecure
sudo nmcli con edit NJITsecure
```

This will open a new shell to edit the network config.

Replace `USERNAME` and `PASSWORD` with the username and password you use to login to your network.
```Bash
nmcli> set ipv4.method auto
nmcli> set 802-1x.eap peap
nmcli> set 802-1x.phase2-auth mschapv2
nmcli> set 802-1x.identity USERNAME 
nmcli> set 802-1x.password PASSWORD
nmcli> set wifi-sec.key-mgmt wpa-eap
nmcli> save
nmcli> activate
```
Wait a few seconds, then you should get an output stating the connection was successful.

Press any button to go back to the command line.
Then, enter `quit` to exit the configuration shell.

You should now be connected to the Wi-Fi.

If you would also like to add Ethernet as a backup do the following.

**Read this document if you have never used vi/vim before.** [Neovim Guide](NeoVim.md)

```bash
 sudo touch /etc/NetworkManager/conf.d/10-globally-managed-devices.conf
 sudo nvim /etc/NetworkManager/NetworkManager.conf
 ```
Then, edit the text to change the line that says `managed=false` to `managed=true`.

Save and quit, then run...

```Bash
sudo reboot now
```
To restart the system.

After logging back in...

Now enter,

```Bash
nmcli d
```
This should list the different network devices on your system including one with the type **ethernet**

In my case this was `enp1s0`

Then enter,

```Bash
sudo nmcli d con enp1s0
```
replacing `enp1s0` with your ethernet device ID.

Now you should have both the Ethernet and Wi-Fi as connected wireless interfaces.

### 2.2: Setting up Tailscale VPN

***Not required but highly recomended as this allows you to remotely access your system, even on other networks***

Now we will install Tailscale which is a VPN software that allows you to
create your own private VPN network with your personal devices. This is recommended
as otherwise you can only access the server locally, and you can have issues if you have multiple Wi-Fi access points
like in a university since IP addresses and hostnames are not universal across the network.

Create an account for [Tailscale](https://login.tailscale.com/start)

Note that using a university email address may not work so using a personal or dedicated email for tailscale is recomended.

Enter the following Command.

```Bash
curl -fsSL https://tailscale.com/install.sh | sh
```

Once it has finished installing run,

```Bash
sudo tailscale up
```

This will then display a URL pointing you to login to your tailscale account.

Once you have logged in, download [Tailscale](https://tailscale.com/download) on your personal system and login.

Note that once tailscale is installed it will be located on the system tray in windows in the bottom right of the screen,
and for MacOS it will be in the menu bar at the top right of the screen.

This is the icon.
![image_5.png](image_5.png)

It may be hidden behind the arrow

![image_6.png](image_6.png)

### 2.3: Logging in to the Server with SSH

Now open the terminal on your personal computer and type in the following.
```Bash
ssh wsprdaemon@sdrpc
```

If your computer cannot resolve the sdrpc hostname, go to the [Tailscale Admin Console](https://login.tailscale.com/admin/machines)

Then find the machine named sdrpc and copy the IP address starting with `100.xxx.xxx.xxx`

Then re-enter the command as
```Bash
ssh wsprdaemon@100.xxx.xxx.xxx
```

You should get a message saying the fingerprint is not recognized type in `y` or `yes`
depending on what the output asked.

If you created the SSH key earlier and added it to the system via GitHub you should be automatically logged in,
otherwise you will need to enter the password of the wsprdaemon account.

If you used the SSH key and want to login to the server from a different computer copy the file located at
`~/.ssh/id_ed25519` on your personal computer (`~/` indicating your user home folder). As mentioned before the `.ssh`
directory is a hidden directory so you will need to enable hidden files in finder/file explorer. Run the following command
in terminal on your personal computer to copy the file to your desktop. (if using windows make sure you are in powershell)

```Bash
cp ~/.ssh/id_ed25519 ~/Desktop/id_ed25519
```

then copy this file to the `~/.ssh` directory on the other computer. If this directory doesnt exist make sure OpenSSH is
installed and if it is type the following in to create the directory. Make sure Tailscale is also installed and
configured on the other system.

```Bash
mkdir ~/.ssh
```

>**Now you can run the server headless, without a monitor by using the ssh connection from your own computer**
>
> Additionally, you can now copy and paste commands and text into the terminal from here on out.
>
> Note that if you are on windows using the <shortcut>Ctrl</shortcut> key has different operations in the terminal as it *literally*
> controls the terminal. ex. to kill a command running you press <shortcut>Ctrl</shortcut><shortcut>C</shortcut>
>
> This presents an issue as that is the command to copy on windows, instead in the terminal you must instead do
> <shortcut>Ctrl</shortcut><shortcut>Shift</shortcut><shortcut>C</shortcut> or <shortcut>Ctrl</shortcut><shortcut>Shift</shortcut><shortcut>V</shortcut> to paste. If you highlight text in the terminal and right click this will also
> copy the text, then pressing right click again will paste it.
>
> MacOS <shortcut>⌘ Cmd</shortcut><shortcut>C</shortcut> keybinds are still valid, and pressing <shortcut>Ctrl</shortcut><shortcut>C</shortcut> will kill running commands as well.
>
{style="note"}

> **You may see text at times display with notation** `^<key>` like `^C` **This is the shorthand notation to tell the user
> to press** <shortcut>Ctrl</shortcut><shortcut>\<Key\></shortcut> This is why the <shortcut>ctrl</shortcut> key on Mac keyboards have the `^` character.
>
{style="tip"}

![image_8.png](image_8.png)

### 2.4: Installing Wsprdaemon

Finally we can install [Wsprdaemon](https://github.com/rrobinett/wsprdaemon)

First lets install some prerequisite tools and utilities by running the following command. (Quite long so i recommend using SSH to allow pasting)

```Bash
sudo apt install btop nmap git tmux vim net-tools iputils-ping avahi-daemon libnss-mdns mdns-scan avahi-utils avahi-discover build-essential make cmake gcc libairspy-dev libairspyhf-dev libavahi-client-dev libbsd-dev libfftw3-dev libhackrf-dev libiniparser-dev libncurses5-dev libopus-dev librtlsdr-dev libusb-1.0-0-dev libusb-dev portaudio19-dev libasound2-dev uuid-dev rsync sox libsox-fmt-all opus-tools flac tcpdump libhdf5-dev libsamplerate-dev
```

Type `y` or select yes to any prompts that come up.

Then, we want to configure our system to run sudo commands without requiring a password (this is why the ssh key is recommended).

We need to install a text editor first, there are ones preinstalled but this is the one I recommend.

In the SDR connection terminal (via SSH), run the following.

```Bash
sudo apt install neovim
```



```Bash
sudo nvim /etc/sudoers.d/wsprsudo
```

This is a text editor called neovim, based on the vi and vim editors. It can be hard to use sometimes so don't be afraid
to look up a vim guide if you get stuck. Some helpful quick information is located in this guide...

[Neovim Guide](NeoVim.md)

By default, you are in *normal* mode which allows you to move around the cursor. Now press `i` to enter insert mode
allowing you to type. Enter the following,

```Bash
wsprdaemon ALL=(ALL) NOPASSWD: ALL
```

then, press `esc` to exit insert mode.

to save the file press `:` to enter the vim commandline, and type in `wq!`

`w` to save or "write", `q` to quit, and `!` to force the operation since the directory is protected.

>To quit without saving in nvim, make sure you are in normal mode by pressing `esc`
> then press `:` and enter `q!`
>
{style="warning"}

Now run:

```Bash
sudo apt install git
```

Which will install git, this allows us to download the source code for wsprdaemon to allow us to install it.

Then run,
```Bash
cd ~
git clone https://github.com/rrobinett/wsprdaemon.git
cd wsprdaemon
./wsprdaemon.sh -V
```


This will clone the installation files from the source repo onto the computer,
then run the main script inside which will create a template configuration file to be edited.

#### 2.4.1: Configuring Wsprdaemon

If you are not comfortable with using vim, I would recommend downloading the configuration template from the
[Wsprdaemon GitHub](https://github.com/rrobinett/wsprdaemon/blob/master/wd_template.conf)

Then, editing it in notepad, or textedit on MacOS. (Make sure you are editing it as plaintext)

I used the configuration listed below, however, since I created this documentation before the official documentation
I do not know what the official recommendations will be, so HamSCI will likely release a better config in the future.

If you know what you are doing I recommend going through the config template and creating the config yourself as there are,
many more features we are not going to use as they are not relevant for the HamSCI PSWS application.

(You can also copy this into notepad/textedit to use if you prefer as well)
```bash
#!/bin/bash
#### The previous line signals to the vim editor that it should use its 'bash' editing mode when editing this file

WD_CPU_CORES="8-15"
RADIOD_CPU_CORES="0-7"

KA9Q_RADIO_COMMIT="main"
KA9Q_RUNS_ONLY_REMOTELY="no" 
KA9Q_CONF_NAME="rx888-wsprdaemon"
KA9Q_WEB_COMMIT_CHECK="main"
KA9Q_WEB_TITLE="<Your Callsign>"

### Since these wav files are uncompressed audio they are quite large.  A 30 minute wav file which might contain a FST4W-1800 signal will be almost 50 MBytes.
### To avoid overflowing the ~/wsprdaemon/wav-archive.d file system, if that wave file will fill more than 75% of the file system, then some of the oldest wav files are deleted first
ARCHIVE_WAV_FILES="yes"

IGNAL_LEVEL_UPLOAD="yes"          ### Whether and how to upload extended spots to wsprdaemon.org.  WD always attempts to upload spots to wsprnet.org
SIGNAL_LEVEL_UPLOAD_MODE="noise"    ### SIGNAL_LEVEL_UPLOAD="no"         => (Default) Only upload spots directly to wsprnet.org
                                    ### SIGNAL_LEVEL_UPLOAD_MODE="noise" => In addition, upload extended spots and noise data to wsprdaemon.org
                                    ### SIGNAL_LEVEL_UPLOAD_MODE="proxy" => Don't directly upload spots to wsprdaemon.org.  Instead, after uploading extended spots and noise data to wsprdaemon.org have it regenerate and upload those spots to wsprnet.org
                                    ###                                     This mode minimizes the use of Internet bandwidth, but makes getting spots to wsprnet.org dependent upon the wsprdameon.org services.

# If SIGNAL_LEVEL_UPLOAD in NOT "no", then you must modify SIGNAL_LEVEL_UPLOAD_ID from "K2MFF" to your call sign.  SIGNAL_LEVEL_UPLOAD_ID cannot include '/
SIGNAL_LEVEL_UPLOAD_ID="<Your Callsign>"     ### The name put in upload log records, the title bar of the graph, and the name used to view spots and noise at that server.
SIGNAL_LEVEL_UPLOAD_GRAPHS="yes"   ### If this variable is defined as "yes" AND SIGNAL_LEVEL_UPLOAD_ID is defined, then FTP graphs of the last 24 hours to http://wsprdaemon.org/graphs/SIGNAL_LEVEL_UPLOAD_ID
SIGNAL_LEVEL_LOCAL_GRAPHS="yes"    ### If this variable is defined as "yes" AND SIGNAL_LEVEL_UPLOAD_ID is defined, then make graphs visible at http://localhost/

KA9Q_RUNS_ONLY_REMOTELY="no"         ### If "yes" then WD will not install and configure its own copy of KA9Q-radio and thus assumes the user has installed and configured it him/her self.

###### These two variables need to be defined in order to enable this WD GRAPE service:
GRAPE_PSWS_ID="<Your Station ID>_<Your Instrument ID>"          ### If this and GRAPE_PSWS_TOKEN are both defined, then each day soon after 00:00 UDT WD will upload the previous day's 24_hour_10sps-iq.wav file
                                                    ### GRAPE_PSWS_ID has the form <SITE_ID>_<INSTRUMENT_ID>,  where those values are obtained from a PSWS user account which assigns these values for
                                                    ### this site+receiver.  That PSWS site is at https://pswsnetwork.caps.ua.edu/home
                                                    ### SITE_ID has the form 'S000nnn' while INSTRUMENT has the form 'NNN'
GRAPE_PSWS_TOKEN="<TokenFromPSWSsite>"          ### This value is the "token" created for that user account by the PSWS server.  It is a very long string with 0-9 and a-z characters in it
                                                    ### Together GRAPE_PSWS_ID + GRAPE_PSWS_PASSWORD are the user+password used to authenticate rsync access to  WD1/grape.wsprdaemon.org
##### After those variables are defined, the WD user must register this server with the GRAPE server by executing 'wdg p'.  This command needs to be run successfully only once after which automatic uploads
##### to the GRAPE server are enabled.


declare RECEIVER_LIST=(
        "KA9Q_0                     wspr-pcm.local     <Your Callsign>         <Your Grid>    NULL"
        "KA9Q_0_WWV                   wwv-iq.local     <Your Callsign>         <Your Grid>    NULL"        
)

declare WSPR_SCHEDULE=(
    "00:00   KA9Q_0,2200,W2:F2:F5:F15:F30  KA9Q_0,630,W2:F2:F5  KA9Q_0,160,W2:F2:F5   KA9Q_0,80,W2:F2:F5    KA9Q_0,80eu,W2:F2:F5  KA9Q_0,60,W2:F2:F5  KA9Q_0,60eu,W2:F2:F5  KA9Q_0,40,W2:F2:F5
             KA9Q_0,30,W2:F2:F5            KA9Q_0,22,W2         KA9Q_0,20,W2:F2:F5    KA9Q_0,17,W2:F2:F5    KA9Q_0,15,W2:F2:F5    KA9Q_0,12,W2:F2:F5  KA9Q_0,10,W2:F2:F5
             KA9Q_0_WWV,WWV_2_5,I1         KA9Q_0_WWV,WWV_5,I1  KA9Q_0_WWV,WWV_10,I1  KA9Q_0_WWV,WWV_15,I1  KA9Q_0_WWV,WWV_20,I1  KA9Q_0_WWV,WWV_25,I1
             KA9Q_0_WWV,CHU_3,I1           KA9Q_0_WWV,CHU_7,I1  KA9Q_0_WWV,CHU_14,I1"
)
```

On the line `SIGNAL_LEVEL_UPLOAD_ID="<Your Callsign>"`, replace the `<Your Callsign>` part inside the Quotes with your FCC registered Callsign. If you do not have one as far as I understand it
if you are part of a university you can use the callsign registered to your university, or if none at all a short nickname. As we are not transmitting any signals we are not required to have a
FCC registered amateur radio licence, however, I am not sure what HamSCI would prefer.

Do the same on the lines here,
```bash
declare RECEIVER_LIST=(
        "KA9Q_0                     wspr-pcm.local     <Your Callsign>         <Your Grid>    NULL"
        "KA9Q_0_WWV                   wwv-iq.local     <Your Callsign>         <Your Grid>    NULL"        
)
```

As for the `<Your Grid>` section enter your callsign or address into this website [](https://levinecentral.com/ham/grid_square.php) which will give you a grid square that refers to your
global coordinates like `FN20vp` for NJIT in Newark, NJ.

#### 2.4.2: Setting Up PSWS Account

For these two sections `GRAPE_PSWS_ID="<Your Station ID>_<Your Instrument ID>"` and `GRAPE_PSWS_TOKEN="<TokenFromPSWSsite>"`, you need to make an account at [Personal Space Weather Station
Central Control System](https://pswsnetwork.caps.ua.edu/signup/) website. Then create a station in the [Station Tab](https://pswsnetwork.caps.ua.edu/stations/stations/) and click the `Add New Station`
button.

![image_9.png](image_9.png)

Add the station nickname which if you have a FCC callsign, should contain your callsign. If you are a larger organization id recomend adding that as well, eg. `NJIT-K2MFF` is the nickname for
the system we created at NJIT.

Then add the Grid Square which is the same one we added to the configuration file earlier.

Elevation we can get from a barometer if you have one, or the compass app on iPhone will show your altitude, however, I am not sure how accurate it is, so I recommend
using a barometer if you have one.

Antenna 1 and Antenna 2, is as far as I understand where you specify what type of antennas you have installed at your site.

The last part is entering your address and contact info.

![image_10.png](image_10.png)

Then select the `View My Stations` button under the Stations tab, then take note of the Station ID.

![image_11.png](image_11.png)

Then select the station, and take note of the `Token`. (This is the secret key for the server identification and authentication which is why I redacted mine)

![image_12.png](image_12.png)

Then, select `Add New Instrument`.

Add a nickname for the Instrument, I named mine `RX-888 MK II - Beelink Mini PC` to show what SDR I am using, and what the server computer is.

Date instrument added is I believe the date that the server is operational and data coming from the server is accurate, as for example our server
was setup and sending data but was not actually connected to our antenna yet, so the data is not good.

Nickname is not required but if you have multiple of the same instruments this will allow you to identify which is which.

Serial number is optional and up to the person installing to add to.

Status is entered to identify if the station is operational or inactive, even if it is connected to the network and sending data.

Instrument Type is where you select the type of radio being used, for the Wsprdaemon we are using a rx888.

![image_13.png](image_13.png)

Then, add the instrument and take note of the instrument ID.

#### 2.4.3: Finishing the Configuration File

Now go back to the config file and change the `GRAPE_PSWS_ID="<Your Station ID>_<Your Instrument ID>"` line to the numbers you added.

For example with NJIT's system `GRAPE_PSWS_ID="S000194_190"`.

Then, add the token on the `GRAPE_PSWS_TOKEN="<TokenFromPSWSsite>"` line.
Which will look something like this `GRAPE_PSWS_TOKEN="t1q8kx36f18kz8c6g5k9"` (Note this is not my token)

The configuration file should look something like this,

```bash
#!/bin/bash
#
#### The previous line signals to the vim editor that it should use its 'bash' editing mode when editing this file

WD_CPU_CORES="8-15"
RADIOD_CPU_CORES="0-7"

KA9Q_RADIO_COMMIT="main"
KA9Q_RUNS_ONLY_REMOTELY="no" 
KA9Q_CONF_NAME="rx888-wsprdaemon"
KA9Q_WEB_COMMIT_CHECK="main"
KA9Q_WEB_TITLE="NJIT-K2MFF @FN20vr"

### Since these wav files are uncompressed audio they are quite large.  A 30 minute wav file which might contain a FST4W-1800 signal will be almost 50 MBytes.
### To avoid overflowing the ~/wsprdaemon/wav-archive.d file system, if that wave file will fill more than 75% of the file system, then some of the oldest wav files are deleted first
ARCHIVE_WAV_FILES="yes"

IGNAL_LEVEL_UPLOAD="yes"          ### Whether and how to upload extended spots to wsprdaemon.org.  WD always attempts to upload spots to wsprnet.org
SIGNAL_LEVEL_UPLOAD_MODE="noise"    ### SIGNAL_LEVEL_UPLOAD="no"         => (Default) Only upload spots directly to wsprnet.org
                                    ### SIGNAL_LEVEL_UPLOAD_MODE="noise" => In addition, upload extended spots and noise data to wsprdaemon.org
                                    ### SIGNAL_LEVEL_UPLOAD_MODE="proxy" => Don't directly upload spots to wsprdaemon.org.  Instead, after uploading extended spots and noise data to wsprdaemon.org have it regenerate and upload those spots to wsprnet.org
                                    ###                                     This mode minimizes the use of Internet bandwidth, but makes getting spots to wsprnet.org dependent upon the wsprdameon.org services.

# If SIGNAL_LEVEL_UPLOAD in NOT "no", then you must modify SIGNAL_LEVEL_UPLOAD_ID from "K2MFF" to your call sign.  SIGNAL_LEVEL_UPLOAD_ID cannot include '/
SIGNAL_LEVEL_UPLOAD_ID="K2MFF"     ### The name put in upload log records, the title bar of the graph, and the name used to view spots and noise at that server.
SIGNAL_LEVEL_UPLOAD_GRAPHS="yes"   ### If this variable is defined as "yes" AND SIGNAL_LEVEL_UPLOAD_ID is defined, then FTP graphs of the last 24 hours to http://wsprdaemon.org/graphs/SIGNAL_LEVEL_UPLOAD_ID
SIGNAL_LEVEL_LOCAL_GRAPHS="yes"    ### If this variable is defined as "yes" AND SIGNAL_LEVEL_UPLOAD_ID is defined, then make graphs visible at http://localhost/

KA9Q_RUNS_ONLY_REMOTELY="no"         ### If "yes" then WD will not install and configure its own copy of KA9Q-radio and thus assumes the user has installed and configured it him/her self.

###### These two variables need to be defined in order to enable this WD GRAPE service:
GRAPE_PSWS_ID="S000194_190"                         ### If this and GRAPE_PSWS_TOKEN are both defined, then each day soon after 00:00 UDT WD will upload the previous day's 24_hour_10sps-iq.wav file
                                                    ### GRAPE_PSWS_ID has the form <SITE_ID>_<INSTRUMENT_ID>,  where those values are obtained from a PSWS user account which assigns these values for
                                                    ### this site+receiver.  That PSWS site is at https://pswsnetwork.caps.ua.edu/home
                                                    ### SITE_ID has the form 'S000nnn' while INSTRUMENT has the form 'NNN'
`GRAPE_PSWS_TOKEN="t1q8kx36f18kz8c6g5k9"            ### This value is the "token" created for that user account by the PSWS server.  It is a very long string with 0-9 and a-z characters in it
                                                    ### Together GRAPE_PSWS_ID + GRAPE_PSWS_PASSWORD are the user+password used to authenticate rsync access to  WD1/grape.wsprdaemon.org
##### After those variables are defined, the WD user must register this server with the GRAPE server by executing 'wdg p'.  This command needs to be run successfully only once after which automatic uploads
##### to the GRAPE server are enabled.


declare RECEIVER_LIST=(
        "KA9Q_0                     wspr-pcm.local     K2MFF         FN20vp    NULL"
        "KA9Q_0_WWV                   wwv-iq.local     K2MFF         FN20vp    NULL"        
)

declare WSPR_SCHEDULE=(
    "00:00   KA9Q_0,2200,W2:F2:F5:F15:F30  KA9Q_0,630,W2:F2:F5  KA9Q_0,160,W2:F2:F5   KA9Q_0,80,W2:F2:F5    KA9Q_0,80eu,W2:F2:F5  KA9Q_0,60,W2:F2:F5  KA9Q_0,60eu,W2:F2:F5  KA9Q_0,40,W2:F2:F5
             KA9Q_0,30,W2:F2:F5            KA9Q_0,22,W2         KA9Q_0,20,W2:F2:F5    KA9Q_0,17,W2:F2:F5    KA9Q_0,15,W2:F2:F5    KA9Q_0,12,W2:F2:F5  KA9Q_0,10,W2:F2:F5
             KA9Q_0_WWV,WWV_2_5,I1         KA9Q_0_WWV,WWV_5,I1  KA9Q_0_WWV,WWV_10,I1  KA9Q_0_WWV,WWV_15,I1  KA9Q_0_WWV,WWV_20,I1  KA9Q_0_WWV,WWV_25,I1
             KA9Q_0_WWV,CHU_3,I1           KA9Q_0_WWV,CHU_7,I1  KA9Q_0_WWV,CHU_14,I1"
)
```

Once you have your configuration written, if you would like to directly edit the existing template configuration you can use,

```Bash
nvim ~/wsprdaemon/wsprdaemon.conf
```

But if you would rather copy and paste your configuration file from your computer to the server I would use the following commands 
which removes the premade template and the next one allows you to create a fresh one.

```Bash
rm ~/wsprdaemon/wsprdaemon.conf
nvim ~/wsprdaemon/wsprdaemon.conf
```

This should delete the old template and open a fresh file to edit, now copy the configuration text file on your computer
and in vim on the server enter insert mode by pressing <shortcut>i</shortcut> and either do
<shortcut>Ctrl</shortcut><shortcut>Shift</shortcut><shortcut>V</shortcut>, or on MacOS <shortcut>⌘ Cmd</shortcut><shortcut>V</shortcut>. (right-clicking then selecting paste will also work)

This should paste the whole configuration file into the server. If you messed up somewhere you can quit without saving
by going into normal mode by pressing <shortcut>escape</shortcut> entering `:q!` then, try again with `nvim ~/wsprdaemon/wsprdaemon.conf` then perform the steps again

Otherwise, go into normal mode with <shortcut>escape</shortcut> as well and enter `:wq` to save and exit the editor.

> If you keep having issues with *nvim* you can try *nano* instead, which is a different command line based text editor.
> I wouldn't recomend using it for editing the sudoers file from earlier though as it doesnt like editing read only files.
>
> You can use nano instead by replacing `nvim` with `nano` in the commands mentioned above.
> *Remember that the notation `^` refers to the <shortcut>ctrl</shortcut> key, so to save and exit in nano it says press `^X` which means
> <shortcut>Ctrl</shortcut><shortcut>X</shortcut>
>
{style="note"}


Once you have saved the configuration file run these commands again.

```Bash
cd ~/wsprdaemon
./wsprdaemon.sh -v
```

This will start installing a lot of packages and will take quite a while. Once it is done it should say something like
"ka9q-radio added your user to the radio group, log out and log back in to save changes" 

Or it may error out mentionioning something about "Update_ini_file_section_variable /etc/radio ....." if this happens attempt to run `./wsprdaemon.sh -V` again. 

If the error occurs again, reboot the computer with 

```bash
sudo reboot now
```

This will restart the server and should end the ssh session, wait a few minutes then re-run this command on your computer
to reconnect. (If using SSH)
```bash
ssh wsprdaemon@sdrpc 
```

Then log back in, and run `./wsprdaemon.sh -V` again.

Now at some point you should get a prompt saying that the RX888 MkII is not attached to a USB port. 

#### 2.4.4: Setting the GPS clock speed

When you get this message, plug in the RX888 to one of the USB 3.0/Super Speed ports (Blue USB ports), and make sure the 
GPS clock is connected to the RX-888 SMA input, and plug the GPS clock USB port into one of the USB ports on the beelink.


Now run move back to the home directory by entering,
```Bash
cd ~
```

and run the following command.

```Bash
git clone https://github.com/simontheu/lbe-1420.git
```

now these,

```Bash
cd lbe-1420
gcc -o lbe-142x lbe-142x.c
```

then run this to list some of the devices plugged into the computer. (Keyboards will show up if they are plugged in, if not it will probably only show the GPS clock)

```Bash
ls -l /dev/hidraw*
```

now take note of how many `/dev/hidraw` devices there are.

now run this command, replacing `.../hidraw0/...` with ones from your list.

```Bash
cat /sys/class/hidraw/hidraw0/device/uevent
```

You know you have the correct device if it outputs something similar to this,
```
    DRIVER=hid-generic
    HID_ID=0003:00001DD2:00002443
    HID_NAME=Leo Bodnar Electronics LBE-1420 GPS Locked Clock Source
    HID_PHYS=usb-0000:02:00.0-2.1/input2
    HID_UNIQ=0673ED0E4101
    MODALIAS=hid:b0003g0001v00001DD2p00002443
```

If it does not, try again but use a different `hidraw` number.

Once you identify the correct device number, run this command replacing the `/dev/hidraw0` with what ever number you 
found was correct.

```Bash
sudo ./lbe-142x /dev/hidraw0 --f1 27000000 --blink1
```

Once you run this command, the LED on the GPS device should blink rapidly a few times, if this happens the command was 
sent correctly. This sets the clock to 27MHz output which is the required frequency for the RX-888.






#### 2.4.4: Setting up the PSWS

Now run 

```Bash
cd ~/wsprdaemon
./wsprdaemon.sh -V
```

Now, you should not get any more errors but you should get a prompt asking `Enter file in which to save the key (/home/wsprdaemon/.ssh/id_ed25519):`

When you get here, press <control>Enter</control> 3 or 4 times, including when it asks for a *passphrase*, however, do not click enter if it asks for a *Password* to login to 
an account through ssh.

If you are lucky it will ask you for an SSH password to log into the PSWS server, however, on the current release as of writing this there is a bug that is not
correctly setting up auto logon for the PSWS server at the University of Alabama. If this does happen, put in the PSWS Token you put in the wsprdaemon config earlier 
which is the password to the server. Eg.`GRAPE_PSWS_TOKEN="t1q8kx36f18kz8c6g5k9"` But just the part in quotes.

If this did not happen go to the next section. Otherwise, skip the next section.  

##### 2.4.4.5 Fixing the PSWS Autologin

Enter the following command to print out the public key of the SSH key you just made.

```Bash
cat ~/.ssh/id_ed25519.pub
```

Copy down the output to a text file or notepad file on your personal computer. It should look something like this,

```Bash
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIA+K11alPxGaRnf4F/K2o7qKRMfqxyf5agBUo4myPuwH wsprdaemon@njit-bl-1
```

Now run the following command to ssh into the PSWS server manually,
```Bash
wdssp
```

Enter yes if it asks for fingerprint verification, then when it asks for a password enter the PSWS token from the 
wsprdaemon config before. Eg. `GRAPE_PSWS_TOKEN="t1q8kx36f18kz8c6g5k9"` But just the part in quotes.

Now once you are logged into the PSWS server run this command, make sure you use `vi` not `nvim` since that is what we normally have been using.

```Bash
vi ~/.ssh/authorized_keys
```

Then, using *i* to enter insert mode, and paste or type in the public key from before that begins with `ssh-ed25519 .....`

now press escape to exit insert mode and hit `:` and type in `wq` to save and quit.

Now type in `exit` to kill the connection and go back to the beelink system. Then, type in `wdssp` one more time to verify that
the computer does not prompt you for a password, if it does then you need to try to retrace the steps and try again.

#### 2.4.4: Setting up the PSWS (continued)


Now run the following commands
```Bash
sudo systemctl enable radiod@rx888-wsprdaemon
sudo systemctl enable ft8-decoded.service
sudo systemctl enable ft4-decoded.service
sudo reboot now
```

Run `cd wsprdaemon` and `./wsprdaemon.sh -V` one more time, and you should get the version number printed out into the console.

Once this happens we can start wsprdaemon,

Now run, 

```Bash
wd -A
```

To start wsprdaemon and add it as a login item to start when the server turns on.

Then run this to initialize the PSWS recording,
```Bash
wdg p
```


> **If you encounter any errors see the** [Operation Guide](Operation.md)
>
{style=note}

Once you can type again, the server should be running. You can confirm this by running this command.
```Bash
wds
```

You should get an output like this.

![image_17.png](image_17.png)

And if you go to a browser on your computer you should be able to type in this url [](http://hostname:8081/) **replacing hostname with your server's
hostname (the name that is after the @ in `wsprdaemon@hostname` on your server's prompt eg. `http://njit-bl-1:8081/` in my case)**

Which should bring you to this interactive web page running locally on the server allowing you to view the signals it
is decoding.

![image_18.png](image_18.png)


Your server should also now show up as active on the [PSWS Website](https://pswsnetwork.caps.ua.edu/home)

![image_19.png](image_19.png)

Typing into the command line on the server
```Bash
wd-help
```
Will list out the available commands part of wsprdaemon to manage the server.
