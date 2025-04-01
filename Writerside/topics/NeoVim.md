# NeoVim

> NeoVim is a command line based text editor that can be used to (as its name suggests) edit text in files located on a 
> remote server. NeoVim is specifically based on an old program created for UNIX called `vi` which was later supersceded
> by `vim` which added more features. This is a popular command line text editor as it is lightweight and available on 
> almost every linux system (usually preinstalled), unfortunately ubuntu is one of the distributions with vim not preinstalled.
> So, instead we can install NeoVim which is an open source and customizable version of vim. Note that there are other 
> command line based text editors out there like `nano` and `emacs` if you prefer, however, Vim is the most reliable to me 
> at least and is very well documented online.
> 
{style = "note"}

## To install NeoVim

Run the following,

```bash
sudo apt update
sudo apt install neovim
```

Now select <control>y</control> and press <control>enter</control> to confirm the installation.

## NeoVim Operation

### Opening a file in NeoVim
To call or execute NeoVim, use the command `nvim <filename>` to do so. 

Eg.
```bash
nvim ~/wsprdaemon/wsprdaemon.conf
```

to start editing the wsprdaemon.conf file.

> Note that if you want to edit a system protected file (usually anything in the `/etc/...` directory) you must prefix 
> the command with `sudo`. Eg. `sudo nvim /etc/radio/radiod@rx888-wsprdaemon.conf` to edit the radiod configuration file.
> Using the prefix `sudo` allows you to run the action as an administrator, which is called the 'root' user on Unix like systems
> like linux and MacOS.
> 
{style="warning"}

### Editing a File in NeoVim


