# Switch User SHell (SUSH)
Python-Curses login shell that has the sole purpose to switch users

### Pre-requisites
1. Python 3
2. tmux
3. Built-in python modules: curses, subprocess, time, string, pwd, sys, os, socket

### Install
1. Pick an install prefix and install the files:
It doesn't matter where you install it, so long as you maintain the directory structure:
   - config: `$INSTALL_PREFIX/etc/sush.env`
   - main script: `$INSTALL_PREFIX/bin/sush`
   - askpass script: `$INSTALL_PREFIX/bin/sush-askpass`
I put them in `/usr/local` personally. You can put them anywhere though.
2. Ownership: `sudo chown root:root $INSTALL_PREFIX/{etc/sush.env,bin/sush,bin/sush-askpass}`
3. Executables: `sudo chmod a+x $INSTALL_PREFIX/bin/sush{,-askpass}`
4. Other permissions: `sudo chmod ug+rw,o-w $INSTALL_PREFIX/{etc/sush.env,bin/sush,bin/sush-askpass}`
5. Install pip requirements: copy the contents of `requirements.txt` and install it with pip to the system.
6. Pick a user you want to be the sole SSH login and set the shell: `usermod -s $INSTALL_PREFIX/bin/sush $USER`
7. Optional, but strongly recommended: Update your sshd_config to only allow that user.
   - `sudo echo "AllowUsers $USER" >> /etc/ssh/sshd_config`
   - `sudo systemctl restart sshd`
