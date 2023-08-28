# Linux-Error-solutions
The problem i Faced after first time using the debian ,basically for my learning to 


<h3>Debian LockScreen Not working (super/window + L):</h3>

In-short the working cammand for me:
Once my "Lock" menu item disappeared and at the same moment I couldn't lock the screen either. Then I checked the Gnome settings:
                                                     
       gsettings list-recursively | grep lockdown

and I found that somehow option "disable-lock-screen" was set to true, which hides the menu item and prevents the screen from locking. Then I set it to false again:

        gsettings set org.gnome.desktop.lockdown disable-lock-screen 'false'

and the "Lock" item is immediately returned and Super + L starts working again.

<h3>Main-cause:</h3>
Prloblem I faced when i switched to ssdm "Display Manner"

1.switch back to gdm3 from ssdm, ssdm doesn't work for me.

You can see the current display manager using this command:

       cat /etc/X11/default-display-manager

For switching display manager to gdm3 you can simply run the following commands and select it as the default display manager:

       sudo apt-get install gdm3
       sudo dpkg-reconfigure gdm3

After all it is needed to rebooting the system.
              
       sudo apt-get install gnome-screensaver
       gnome-screensaver-command -l


<h3>When Visual Studio Shows This Error while running a code in Vs code terminal</h3>
<p>568 preload-host-spawn-strategy] Warning: waitpid override ignores groups</p>
     <h4>Copy this command in settings.json files in visual studio </h4> 
     
       "terminal.integrated.env.linux": {
        "LD_PRELOAD": null,
    }
