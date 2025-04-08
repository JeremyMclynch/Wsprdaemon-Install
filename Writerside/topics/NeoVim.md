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

When entering nvim you will be defaulted into **Normal** mode, this mode allows you to press a key to 
enter a different mode or perform actions. (Note that you **Cannot** edit/type in the document in this mode.)

To start entering/editing text press the <control>i</control> key, this will put you in the **insert** mode.

From here you can type anything you need to edit the document. 

To save the document you need to **exit insert mode** which you can do by pressing <control>Esc</control>.

This will put you back into **Normal** mode. 

Now, to save the document press the colon [<control>:</control>] key.

(Not the semicolon [<control>;</control>], make sure you press shift.)

This opens the vim commandline which allows you to enter commands.

To save type in `w` to write, and press <control>enter</control> to execute the command.

Now you can press <control>Esc</control> to go back to **Normal** mode and <control>i</control> to enter 
insert mode again, if you would like to continue editing the file.

### Exiting NeoVim

If you would like to exit nvim, go back to the commandline by pressing <control>:</control> in **Normal** mode.
Then, enter `wq` to save (write) and quit. Or if you would like to exit the document enter `q` instead. However, If you made 
any changes to the file you will receive an error, if you enter `q` by itself. To quit without saving if you made any edits 
enter, `q!` to force/override quit.

## Quick Reference

| Operation                       | Keybind                                                  | Explanation                                                                                                                                                                                                                                                   |
|---------------------------------|----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Enter Normal Mode               | Press **Esc**                                            | Go back to Normal mode from any other mode                                                                                                                                                                                                                    |
| Enter Insert Mode               | Press **i** in Normal Mode                               | Allows text editing/modification                                                                                                                                                                                                                              |
| Enter Insert Mode (On new Line) | Press **o** in Normal Mode                               | Creates a blank new line below the cursor and puts you into Insert Mode                                                                                                                                                                                       |
| Enter Vim Command Line          | Press **:** in Normal Mode (Remember to press **shift**) | Opens the Vim Command Line (Commands listed in table below)                                                                                                                                                                                                   |
| Enter Visual Mode               | Press **v** in Normal Mode                               | Starts highlighting text starting from your initial cursor position, move cursor w/ arrow keys to highlight                                                                                                                                                   |
| Copy Text (Yank)                | Press **y** in Visual Mode                               | Copies text highlighted in visual mode to (nvim only) clipboard                                                                                                                                                                                               |
| Paste/Print Text                | Press **p** in Visual Mode                               | Pastes text from (vim only) clipboard. (Note that if you are using SSH to connect to a server, anything copied from your comuter with <shortcut>Ctrl C</shortcut> will not paste with **p**. Instead press <shortcut>Shift Ctrl V</shortcut> in insert mode). |
| Move Cursor Up                  | Press **j** in Normal/Visual Mode                        | Equivalent to the **Up Arrow**                                                                                                                                                                                                                                |
| Move Cursor Down                | Press **k** in Normal/Visual Mode                        | Equivalent to the **Down Arrow**                                                                                                                                                                                                                              |
| Move Cursor Left                | Press **h** in Normal/Visual Mode                        | Equivalent to the **Left Arrow**                                                                                                                                                                                                                              |
| Move Cursor Right               | Press **l** in Normal/Visual Mode                        | Equivalent to the **Right Arrow**                                                                                                                                                                                                                             |
| Undo                            | Press **u** in Normal Mode                               | Equivilent to <shortcut>Ctrl z</shortcut> in MS Word                                                                                                                                                                                                          |
| Delete/cut entire row           | Press **dd** in Normal Mode                              | Deletes/cuts entire row that the cursor is currently on. (Also adds line to yank clipboard)                                                                                                                                                                   |
| Replace text                    | Press **c** in Visual Mode (with text highlighted)       | Will erase highlighted text, and put you into insert mode in its place to replace the text                                                                                                                                                                    |


| Operation            | Vim Commandline           | Example                                                                                   |
|----------------------|---------------------------|-------------------------------------------------------------------------------------------|
| Save/Write           | `w`                       | `w` to save the file                                                                      |
| Quit/Exit            | `q`                       | `q` to exit Vim (If no changes were made to the file)                                     |
| Force/Override       | `!`  (After Vim command)  | `q!` to Force Quit, or `w!` to overwrite/force save.                                      |
| Perform Bash Command | `!` (Before Bash Command) | `!ls` to List directory contents using the standard Bash commandline without exiting nvim |
| Undo                 | `u`                       | Equivalent to <shortcut>Ctrl z</shortcut> in MS Word                                       |
