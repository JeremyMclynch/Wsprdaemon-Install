# Updates

## Change BIOS Settings

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

## Remove snapd

```Bash
sudo apt autoremove --purge snapd gnome-software-plugin-snap
sudo apt-mark hold snapd
```

## Wifi UI
*after installing network-manager*
```Bash
nmtui
```

## Other utilities and pre-requisites

```Bash
sudo apt install btop nmap git tmux vim net-tools iputils-ping avahi-daemon libnss-mdns mdns-scan avahi-utils avahi-discover build-essential make cmake gcc libairspy-dev libairspyhf-dev libavahi-client-dev libbsd-dev libfftw3-dev libhackrf-dev libiniparser-dev libncurses5-dev libopus-dev librtlsdr-dev libusb-1.0-0-dev libusb-dev portaudio19-dev libasound2-dev uuid-dev rsync sox libsox-fmt-all opus-tools flac tcpdump wireshark libhdf5-dev libsamplerate-dev
```