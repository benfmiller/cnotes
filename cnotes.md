# AmazonLinux {{
## install fzf {{
```
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```
}}
## install latest tmux {{
https://gist.github.com/muralisc/dbb998a8555acc577ce2cf7aae8cd9fa
```
# Install tmux 3.0a on Centos

# install deps
sudo yum install -y gcc kernel-devel make ncurses-devel

# DOWNLOAD SOURCES FOR LIBEVENT AND MAKE AND INSTALL
curl -LOk https://github.com/libevent/libevent/releases/download/release-2.1.11-stable/libevent-2.1.11-stable.tar.gz
tar -xf libevent-2.1.11-stable.tar.gz
cd libevent-2.1.11-stable
./configure --prefix=/usr/local
make
sudo make install

# DOWNLOAD SOURCES FOR TMUX AND MAKE AND INSTALL

curl -LOk https://github.com/tmux/tmux/releases/download/3.0a/tmux-3.0a.tar.gz
tar -xf tmux-3.0a.tar.gz
cd tmux-3.0a
LDFLAGS="-L/usr/local/lib -Wl,-rpath=/usr/local/lib" ./configure --prefix=/usr/local
make
sudo make install

# pkill tmux
# close your terminal window (flushes cached tmux executable)
# open new shell and check tmux version
tmux -V
```
}}
## install neovim {{
https://gorm.dev/install-neovim-on-amazon-linux-2
```
sudo yum install libcurl-devel
sudo yum remove cmake -y

sudo yum install gcc-c++ -y
wget https://cmake.org/files/v3.10/cmake-3.10.0.tar.gz
tar -xvzf cmake-3.10.0.tar.gz

cd cmake-3.10.0
# I be Bootstrappin'
./bootstrap --system-curl

# make the thing
make

# make all the things
sudo make install

cd ..

sudo pip-3.7 install neovim --upgrade
cd "$(mktemp -d)"
git clone https://github.com/neovim/neovim.git
cd neovim

make CMAKE_BUILD_TYPE=Release
sudo make install
```
}}
## install ripgrep {{
 ```
 sudo yum-config-manager --add-repo=https://copr.fedorainfracloud.org/coprs/carlwgeorge/ripgrep/repo/epel-7/carlwgeorge-ripgrep-epel-7.repo
 sudo yum install ripgrep
```
}}
}}
# WSL {{

## powershell {{
wsl --list -v
// verbose list

wsl --shutdown {distname}
//shutsdown distname
}}

explorer.exe .
//opens windows file explorer in current directory

wslview [filename]
// opens file with windows default app

## kex {{
kali-win-kex

kex --sl -s
// sl mode, requires resolv.conf nameserver to be default for wsl, make sure firewall lets stuff through
// firefox crashes the server?
// might need to remove logs in tmp? look at them?

kex --win
// win mode
kex --esm
// remote desktop mode

kex --start-sound
// tries to start sound

kex kill
kex stop
}}

vncserver -SecurityTypes None
// starts vncserver with no password

vncserver --kill
//kills, need to specify which one if more than one

vncserver
//starts server

}}
# MacStuff {{
setup i3wm like with this link
https://cbrgm.net/post/2021-05-5-setup-macos/
}}
# Vagrant {{
vagrant up
// in directory with vagrant file

vagrant ssh
// ssh into vagrant box

//Look at vagrant file for example stuff!
}}
# i3 {{
<!-- sudo add-apt-repository -y ppa:regolith-linux/stable -->
<!-- sinstal i3-gaps -->

// i3wm install
https://i3wm.org/docs/repositories.html

// make logout runnable as root
https://serverfault.com/questions/75620/ubuntu-let-a-user-run-a-script-with-root-permissions

// i3wm docs
https://i3wm.org/docs/userguide.html#gaps

// look in rcfiles/config and ln everything you want

// rofi theme
https://draculatheme.com/rofi
// actually use `rofi-theme-selectork`

sinstal i3status
sinstal i3blocks
sinstal playerctl
sinstal flameshot
sinstal compton

// for lock on screen close
sinstal xss-lock -y

sudo apt-get install lxappearance gtk-chtheme -y

apt install feh fonts-font-awesome rofi pulseaudio-utils xbacklight alsa-tools clipit gcc git terminator locate pcmanfm libnotify-bin acpi -y

// look at rcfiles/config/X11 to find the intel_backlight thing for xbacklight

// build ybacklight
git clone https://github.com/szekelyszilv/ybacklight.git
cd ybacklight/src
gcc ybacklight.c -o /usr/bin/ybacklight

// for rofifinder if needed (locate command)
apt install mlocate && updatedb

## https://kifarunix.com/install-and-setup-i3-windows-manager-on-ubuntu-20-04/ {{
# Please see http://i3wm.org/docs/userguide.html for a complete reference!
#

set_from_resource $darkred     color1  #000000
set_from_resource $red         color9  #000000
set_from_resource $darkgreen   color2  #000000
set_from_resource $green       color10 #000000
set_from_resource $darkyellow  color3  #000000
set_from_resource $yellow      color11 #000000
set_from_resource $darkblue    color4  #000000
set_from_resource $blue        color12 #000000
set_from_resource $darkmagenta color5  #000000
set_from_resource $magenta     color13 #000000
set_from_resource $darkcyan    color6  #000000
set_from_resource $cyan        color14 #000000
set_from_resource $darkwhite   color7  #000000
set_from_resource $white       color15 #000000

# Use custom colors for black
 set $black       #282828
 set $darkblack   #1d2021
 set $transparent #00000000

set $mod Mod4
set $mod1 Mod1
set $terminator terminator


# Font for window titles. Will also be used by the bar unless a different font
# is used in the bar {} block below.
font pango:monospace 12

# This font is widely installed, provides lots of unicode glyphs, right-to-left
# text rendering and scalability on retina/hidpi displays (thanks to pango).

font pango:DejaVu Sans Mono 12
#font pango:Meslo LG L Regular Nerd Font Complete 15

# Use Mouse+$mod to drag floating windows to their wanted position
floating_modifier $mod

# start a terminator by pressing Mod key + x or ENTER
bindsym $mod+Return exec $terminator
bindsym $mod+x exec $terminator

# Custom bindsyms
bindsym $mod+p exec ~/.config/i3/bin/logout
bindsym $mod+l exec i3lock -i /home/koromicha/Pictures/linuxtux.png
bindsym $mod+c exec google-chrome
bindsym $mod+r mode "resize"
bindsym $mod+Shift+f exec /home/koromicha/.config/i3/bin/rofifinder


# Enable Print Screen
#bindsym --release $mod+Print exec gnome-screenshot -i
bindsym --release $mod+Print exec shutter -s

# kill focused window
bindsym $mod+q kill

# start dmenu (a program launcher)
bindsym $mod+d exec --no-startup-id ~/.config/i3/bin/rofi_app_launcher


# change focus
bindsym $mod+j focus left
bindsym $mod+k focus down
# bindsym $mod+l focus up
bindsym $mod+semicolon focus right

# alternatively, you can use the cursor keys:
bindsym $mod+Left focus left
bindsym $mod+Down focus down
bindsym $mod+Up focus up
bindsym $mod+Right focus right

# move focused window
bindsym $mod+Shift+j move left
bindsym $mod+Shift+k move down
bindsym $mod+Shift+l move up
bindsym $mod+Shift+semicolon move right

# alternatively, you can use the cursor keys:
bindsym $mod+Shift+Left move left
bindsym $mod+Shift+Down move down
bindsym $mod+Shift+Up move up
bindsym $mod+Shift+Right move right


# split in horizontal orientation
bindsym $mod+h split h

# split in vertical orientation
bindsym $mod+v split v

# enter fullscreen mode for the focused container
bindsym $mod+f fullscreen toggle

# change container layout (stacked, tabbed, toggle split)
bindsym $mod+s layout stacking
#bindsym $mod+w layout tabbed
bindsym $mod+t layout tabbed
bindsym $mod+e layout toggle split

# toggle tiling / floating
bindsym $mod+Shift+space floating toggle

# change focus between tiling / floating windows
bindsym $mod+space focus mode_toggle

# focus the parent container
bindsym $mod+a focus parent
# focus the child container
bindsym $mod+z focus child

# Workspace Variables
set $ws1 "1: "
#set $ws2 "2: "
set $ws2 "2: "
set $ws3 "3: "
set $ws4 "4: "
set $ws5 "5: "
set $ws6 "6:"
set $ws7 "7:"
set $ws8 "8: "
set $ws9 "9: "


# switch to workspace
bindsym $mod+1 workspace $ws1
bindsym $mod+2 workspace $ws2
bindsym $mod+3 workspace $ws3
bindsym $mod+4 workspace $ws4
bindsym $mod+5 workspace $ws5
bindsym $mod+6 workspace $ws6
bindsym $mod+7 workspace $ws7
bindsym $mod+8 workspace $ws8
bindsym $mod+9 workspace $ws9
bindsym $mod+0 workspace $ws10

# move focused container to workspace
bindsym $mod+Shift+1 move container to workspace $ws1
bindsym $mod+Shift+2 move container to workspace $ws2
bindsym $mod+Shift+3 move container to workspace $ws3
bindsym $mod+Shift+4 move container to workspace $ws4
bindsym $mod+Shift+5 move container to workspace $ws5
bindsym $mod+Shift+6 move container to workspace $ws6
bindsym $mod+Shift+7 move container to workspace $ws7
bindsym $mod+Shift+8 move container to workspace $ws8
bindsym $mod+Shift+9 move container to workspace $ws9
bindsym $mod+Shift+0 move container to workspace $ws10

# reload the configuration file
bindsym $mod+Shift+c reload
# restart i3 inplace
bindsym $mod+Shift+r restart
# exit i3 (logs you out of your X session)
bindsym $mod+Shift+e exec "i3-nagbar -t warning -m 'You pressed the exit shortcut. Do you really want to exit i3? This will end your X session.' -b 'Yes, exit i3' 'i3-msg exit'"

# resize window (you can also use the mouse for that)
mode "resize" {
        # These bindings trigger as soon as you enter the resize mode

        # Pressing left will shrink the window’s width.
        # Pressing right will grow the window’s width.
        # Pressing up will shrink the window’s height.
        # Pressing down will grow the window’s height.
        bindsym j resize shrink width 10 px or 10 ppt
        bindsym k resize grow height 10 px or 10 ppt
        bindsym l resize shrink height 10 px or 10 ppt
        bindsym semicolon resize grow width 10 px or 10 ppt

        # same bindings, but for the arrow keys
        bindsym Left resize shrink width 10 px or 10 ppt
        bindsym Up resize grow height 10 px or 10 ppt
        bindsym Down resize shrink height 10 px or 10 ppt
        bindsym Right resize grow width 10 px or 10 ppt

        # back to normal: Enter or Escape
        bindsym Return mode "default"
        bindsym Escape mode "default"
}
#
# Pulse Audio controls
# run pactl list sinks
#bindsym XF86AudioRaiseVolume exec --no-startup-id pactl set-sink-volume 0 +5% #increase sound volume
#bindsym XF86AudioLowerVolume exec --no-startup-id pactl set-sink-volume 0 -5% #decrease sound volume#
#bindsym XF86AudioMute exec --no-startup-id pactl set-sink-mute 1 toggle # mute sound

# Amixer

bindsym XF86AudioRaiseVolume exec --no-startup-id amixer -D pulse sset Master 5%+ #increase sound volume
bindsym XF86AudioLowerVolume exec --no-startup-id amixer -D pulse sset Master 5%- #decrease sound volume#
bindsym XF86AudioMute exec --no-startup-id amixer -q set Master toggle # mute sound

# Sreen brightness controls
# enable passwordless sudo for ybacklight. echo "koromicha ALL=NOPASSWD: /usr/bin/ybacklight" > /etc/sudoers.d/ybacklight
bindsym XF86MonBrightnessUp exec sudo ybacklight -inc 5 # increase screen brightness
bindsym XF86MonBrightnessDown exec sudo ybacklight -dec 5 # decrease screen brightness

# i3blocks
bar {
    status_command i3blocks
    position top
    font pango:Hack, FontAwesome 11

    colors {
        separator #081419
        background #253941
        #statusline #839496
        focused_workspace #fdf6e3 #6c71c4 #fdf6e3
        active_workspace #fdf6e3 #6c71c4 #fdf6e3
        inactive_workspace #002b36 #586e75 #002b36
        urgent_workspace #d33682 #d33682 #fdf6e3

        statusline         $white
        separator          $transparent
  }
}


set $m1 #808080
set $m2 #FFF0E0

# Startup programs
exec --no-startup-id dunst
exec_always compton &;
exec --no-startup-id clipit &;
exec_always feh --bg-scale /home/koromicha/Pictures/linux-wallpaper.jpg
exec_always --no-startup-id nm-applet


# Bind App to workspace
# Check class by using xprop command
assign [class="chromium"] $ws2
assign [class="Firefox"] $ws2
assign [class="Atom"] $ws3
assign [class="Foxit Reader"] $ws3
assign [class="Pcmanfm"] $ws4
assign [class="VirtualBox"] $ws5
assign [class="Virt-manager"] $ws5
assign [class="Skype"] $ws6
assign [class="mpv"] $ws9
assign [class="vlc"] $ws9
assign [class="Thunderbird"] $ws7
assign [class="(?i)libreoffice-startcenter"] $ws8
assign [class="(?i)soffice"] $ws8
assign [class="(?i)libreoffice"] $ws8


# Assign to certain workspace
assign [window_role="browser"] $ws2

# Press $mod+o followed by either f, s, l, m, v, k, d, t, Esc or Return {ENTER),
# to launch FoxiReader, Skype, lxappearance, thunderbird, VirtualBox,
# KVM Virt-manager, spectacle, pcmanfm file manager,
# or return to the default mode, respectively.
set $mode_launcher Launcher
bindsym $mod+o mode "$mode_launcher"

mode "$mode_launcher" {
    bindsym f exec FoxitReader
    bindsym s exec skypeforlinux
    bindsym l exec lxappearance
    bindsym m exec thunderbird
    bindsym v exec VirtualBox
    bindsym k exec virt-manager
    bindsym d exec spectacle
    bindsym t exec "pcmanfm /home/koromicha"

    bindsym Esc mode "default"
    bindsym Return mode "default"
}

# Shutdown, Reboot, Lock Screen, and Logout

set $power_mode "power"
bindsym $mod+Shift+q      mode $power_mode
mode $power_mode {
    bindsym p         exec systemctl poweroff
    bindsym r         exec systemctl reboot
    bindsym l         exec i3lock -i /home/koromicha/Pictures/linuxtux.png, mode "default"
    bindsym q         exec --no-startup-id i3-msg exit, mode "default"
    bindsym h         exec sudo systemctl hibernate
    bindsym s         exec sudo systemctl suspend
    bindsym Return    mode "default"
    bindsym Escape    mode "default"
}

# Floating windows
for_window [window_role="task_dialog|bubble|page-info|Preferences|pop-up"] floating enable
for_window [window_role="Open Files"] floating enable sticky
for_window [window_role="File Operation Progress"] floating enable sticky
for_window [class="qBittorrent" window_role="pop-up"] floating enable
for_window [window_type="dialog"] floating enable
for_window [window_type="menu"] floating enable

# Sticky window
for_window [instance="file_progress"]  sticky enable
for_window [class="info|Mate-color-select|gcolor2|timesup|QtPass|GtkFileChooserDialog"] sticky enable

# Focus window settings
no_focus [window_role="pop-up"]
focus_on_window_activation focus
}}

## var-window i3 stuff {{

probably want to install blueman (apt)

cursor sometimes flickered with compton on second screen
https://unix.stackexchange.com/questions/358992/cursor-flickers-with-xrandr-scaling
https://github.com/chjj/compton/issues/297

autorandr and arandr
autorandr lets you save screen configurations based on what is detected
    - https://github.com/phillipberndt/autorandr
ARandR lets you configure screens with a GUI, very helpful compared to just using xrandr

}}
}}

# Jekyll {{
sudo apt-get install ruby-full build-essential zlib1g-dev

echo '# Install Ruby Gems to ~/gems' >> ~/.zshrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.zshrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

gem install jekyll bundler

bundle exec jekyll serve
}}
# Creating a Service {{
Creating a Service

On your Pi, create a .service file for your service, for example: myscript.service

```
[Unit]
Description=My service
After=network.target

[Service]
ExecStart=/usr/bin/python3 -u main.py
WorkingDirectory=/home/pi/myscript
StandardOutput=inherit
StandardError=inherit
Restart=always
User=pi

[Install]
WantedBy=multi-user.target
```

    So in this instance, the service would run Python 3 from our working directory /home/pi/myscript which contains our python program to run main.py. But you are not limited to Python programs: simply change the ExecStart line to be the command to start any program or script that you want running from booting.

    Copy this file into /etc/systemd/system as root, for example:

sudo cp myscript.service /etc/systemd/system/myscript.service

    Once this has been copied, you have to inform systemd that a new service has been added. This is done with the following command:

sudo systemctl daemon-reload

    Now you can attempt to start the service using the following command:

sudo systemctl start myscript.service

    Stop it using following command:

sudo systemctl stop myscript.service

    When you are happy that this starts and stops your app, you can have it start automatically on reboot by using this command:

sudo systemctl enable myscript.service

    The systemctl command can also be used to restart the service or disable it from boot up.
Note
	The order in which things are started is based on their dependencies — this particular script should start fairly late in the boot process, after a network is available (see the After section). You can configure different dependencies and orders based on your requirements.
}}
# MongoDB Commands {{
// mongodump with docker
docker exec <CONTAINER> sh -c 'exec mongodump --db somedb --gzip --archive' > dump_`date "+%Y-%m-%d"`.gz

// mongodump Tradesuite
mongodump --db TradeSuite
}}
# Vimspector {{
my custom default snippets are defined in ~/rcfiles/UltiSnips/json.snippets
type "vimspector-default" to get default

all around ref, by the maintainer
- https://puremourning.github.io/vimspector/configuration.html

The project and readme
- https://github.com/puremourning/vimspector

build in supported languages, install with :VimspectorInstall <something>
- https://github.com/puremourning/vimspector#supported-languages

## my nvim mappings - vimspector {{

nnoremap <leader>qd :VimspectorReset<CR>
nnoremap <leader>dd :call vimspector#Continue()<CR>
nnoremap <leader>dc :call GotoWindow(g:vimspector_session_windows.code)<CR>
nnoremap <leader>dt :call GotoWindow(g:vimspector_session_windows.tagpage)<CR>
nnoremap <leader>dv :call GotoWindow(g:vimspector_session_windows.variables)<CR>
nnoremap <leader>dw :call GotoWindow(g:vimspector_session_windows.watches)<CR>
nnoremap <leader>ds :call GotoWindow(g:vimspector_session_windows.stack_trace)<CR>
nnoremap <leader>do :call GotoWindow(g:vimspector_session_windows.output)<CR>

nmap <leader>dl <Plug>VimspectorStepInto
nmap <leader>dj <Plug>VimspectorStepOver
nmap <leader>dk <Plug>VimspectorStepOut
nmap <leader>dR <Plug>VimspectorRestart
nmap <leader>daw <Plug>VimspectorAddWatch
nmap <leader>dew <Plug>VimspectorDeleteWatch

" alt maps
nmap <M-q> :VimspectorReset<CR>
nmap <M-d> :call vimspector#Continue()<CR>
nmap <M-l> <Plug>VimspectorStepInto
nmap <M-j> <Plug>VimspectorStepOver
nmap <M-k> <Plug>VimspectorStepOut
nmap <M-h> <Plug>VimspectorRestart
nmap <M-c> <Plug>VimspectorRunToCursor

nmap <leader>drc <Plug>VimspectorRunToCursor
nmap <C-b> <Plug>VimspectorToggleBreakpoint
nmap <leader>db <Plug>VimspectorToggleConditionalBreakpoint

}}
## helpful help documents - vimspector {{
vimspector-ref-replacements-variables
    - shows how to do input args to debuggable program

vimspector-ref-predefined-variables
    - predefined variables to use in vimspector files

vimspector-ref-python-example
    - example for python, remote debugging with docker

vimspector-ref-docker-example
    - docker example
}}
## Trying to get go docker working {{

go-docker-delve-remote-debug
- https://golangforall.com/en/post/go-docker-delve-remote-debug.html

- https://www.reddit.com/r/neovim/comments/yq78i0/neovim_debug_app_inside_docker_container/

vim-go plugin,
- https://github.com/fatih/vim-go/wiki/Tutorial
- https://www.pavedroad.io/part-8-go-debugging-with-vim-and-delve/

vim-go plugin connect to delve session with port
- https://osamaelnaggar.com/blog/vim_go_and_remote_debugging/
- https://github.com/puremourning/vimspector/discussions/342

}}

There are two locations for debug configurations for a project:

- 'g:vimspector_configurations' vim variable (dict)
- '<vimspector home>/configurations/<OS>/<filetype>/*.json'
- '.vimspector.json' in the project source

}}

# Misc {{
https://unix.stackexchange.com/questions/255509/bluetooth-pairing-on-dual-boot-of-windows-linux-mint-ubuntu-stop-having-to-p
// how to move bluetooth keys between dual boots

/usr/bin/setxkbmap -option "ctrl:nocaps"
//include in .profile to map ctrl to caps


// instructions to mount cifs drive
https://markontech.com/linux/mount-a-network-shared-drive-on-linux/
https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!

//fix root only writes
https://ubuntuforums.org/showthread.php?t=1409720

git config --global core.excludesfile ~/.gitignore

show latest output from vim to cmdline
:messages

}}
# Neat Projects {{

flutter_rust_bridge
- Compile rust and use directly from flutter

}}
# articles and links {{

language server nvim info, nvim-lspconfig
- https://github.com/neovim/nvim-lspconfig/blob/master/doc/server_configurations.md

Mason nvim "package manager" server mapping from mason-lspconfig to nvim-lspconfig
- https://github.com/williamboman/mason-lspconfig.nvim/blob/main/doc/server-mapping.md

AI geneartor art, memes, variety
- https://thisxdoesnotexist.com/

local blockchain with nice GUI and tooling
- https://trufflesuite.com/ganache/

go development with go
- https://goethereumbook.org/en/

Google open source mini conferences, some cool informational vids for tech on-demand
- https://opensourcelive.withgoogle.com/
}}
# Blockchain-Solidity {{
Centrifuge - the infrastructure that facilitates the decentralized financing of real-world assets natively on-chain, creating a fully transparent market which allows borrowers and lenders to transact without unnecessary intermediaries
    - https://docs.centrifuge.io/getting-started/centrifuge-at-a-glance/

Tinlake - open DeFi protocol and marketplace for real-world asset pools
    - centrifuge's flagship dApp
    - https://tinlake.centrifuge.io/

WalletConnect
    - communications protocol for web3, enabling wallets and apps to securely connect and interact
    - https://walletconnect.com/

Avalanche
    - smart contracts platform
    - blazingly fast
    - Uses hashgraph DAG for consensus

    - https://www.avax.network/

Brightvine "Protocol" product
- https://docs.google.com/document/d/1djxXdl3OV1xreVwVkJPgza9cJQ8UNWGgzr6WAq7RWYA/edit

Learn solidity and DApps turorials
- https://cryptozombies.io/

Deploy Solidity Contract using GoLang — Go-Simple-Storage-FCC
- https://medium.com/coinmonks/deploy-solidity-contract-using-golang-go-simple-storage-fcc-b247b29ffa18

openzeppelin, provides security products to build, automate, and operate decentralized applications.
- https://www.openzeppelin.com/
- https://docs.openzeppelin.com/contracts/4.x/
    - Docs
- https://www.openzeppelin.com/contracts
    - contract builder

Ethereum Improvement Proposals, multi toekn standard, semi fungible
- https://eips.ethereum.org/EIPS/eip-1155
}}

# Commands {{

## Powershell {{
While(1) {ps | sort -des cpu | select -f 15 | ft -a; sleep 1; cls}
> // This shows cpu time, which is like cpu usage
}}
## Git Bash {{

.inputrc
set bell-style none
thank god removes bash screen blind

}}
## One liners {{

“Given a text file and an integer k, print the kmost common words in the file (and the number of their occurrences) in decreasing frequency.”
```
tr -cs A-Za-z '' | tr A-Z a-z | sort | uniq -c | sort -rn | sed ${1}q
```


// download/clone all git submodules
git submodule update --init --recursive
}}


mimeopen {filename}
//opens file with prefered program, -a asks which program, -d asks and sets default

hexdump
//pipe echo into it and get hex chars

{command} &> {outfile}
//redirects both standard output and standard error

{command} 2> /dev/null
//throw away errors

## Managing Users {{
Sudo adduser {username}

chown - change owner
chgrp - change group

}}
## System {{

watch -n 2 sensors
//shows system sensors
// might require install lm-sensors

nvidia-smi
//prints gpu usage

nvidia-smi -l 1
//prints gpu usage every second

lsb_release -dc
// prints release information

ps -edf
// shows details of running processes

ps --no-headers -o comm 1
// Shows init system

ss -tupln
// shows listening ports, may require sudo

ufw allow {port}/{protocol}
// allows port through firewall, may require sudo

ping {ip-address} -t
// -t pings only

ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'
// finds public ip address

### sudo {{

su - {username}
the - logs in as if it's a fresh login

su {account}
// then enter password to log in to account

sudo -l
// lists actions you can perform

sudo -u {username} {command}
//execute command as username

}}

sudo service {servicename} start
// stop, restart, stuff: service instead of systemctl

sudo update-rc.d {servicename} defaults
// sets service to start at boot
// might need to use "enable" instead of "defaults"

chmod +xs {filename}
//set setgit bit

which {command}
// prints aliases, functions, or destination of executable

id {user, optional}
// prints details about current user or details about user given

uuidgen
// generated new uuid/guid

}}
## files {{
strings {filename}
// outputs all strings in file

file {filename}
// prints details about file

find . -name .bash_history -exec grep -A 1 '^passwd' {} \;
// find {filename} ^ makes it not
//executes comand on each file found

find {dir} -name {filename} -exec {command} {} \;
//calls command on each match, if using bash calls bash as many matches are found

find / -type d -name dirname
// finds directory name

diff {filename1} {filename2}
// prints all differences between two files

pandoc MANUAL.txt -o example13.pdf
pandoc MANUAL.md -o example13.pdf
//to render markdown or text as pdf
// sudo apt-get install pandoc texlive-latex-base texlive-fonts-recommended texlive-extra-utils texlive-latex-extra texlive-science

}}
## Zips {{
cpio -idv --no-absolute-filename < {filename}
// extracts from cpio archive

tar -zxvf filename.tgz
// z-zipper, x-extract, v-verbose, f-filename    gzip

tar -jxvf filename.tbz
// j-compressed with bzip

bunzip2 {filename}
// for .bz2 files

}}
## Encryption {{
openssl enc -d -aes256 -k {key} -in {input_file} -out {output_file}
// -d decrypts

john {filename} --format=descrypt
// for DES encryption
// John-the-Ripper supports tons of different formats

john {filename}
//auto detects format if it can

echo -n "wordtohash" | md5sum
// -n emits trailing new line and this outputs hash of wordtohash
    Encryption types {{
    DES (you can tell by the size and format of it). This is common on very old systems and it's very weak (especially since only the first 8 bytes of the password are kept)

    Prefix of file is $num$
    if the hash starts by $1$, MD5, john format md5crypt
    if the hash starts by $2$ or $2a$, Blowfish is used;
    if the hash starts by $5$, SHA-256 is used;
    if the hash starts by $6$, SHA-512 is used.

    }}
}}
## Grep {{

grep -A 1 passwd .bash_history
// shows one line above passwd found in .bash_history

grep -q {Pattern} {filename}
// true if pattern found

{command} | grep -qv {pattern}
// returns true if pattern not found in command output

}}
## awk {{

awk '{print $1}' {filename}
//prints first item in filename

awk 'BEGIN {system("/bin/bash")}'
//starts bash from awk

}}
## Firewall {{
sudo ufw default deny incoming
// blocks all incoming connections by default

sudo ufw default allow outgoing

sudo ufw allow ssh
// this defaults to port 22

sudo ufw allow 2222/tcp
// use this if ssh listens on different port

sudo ufw allow www
// allows http server

sudo ufw enable

sudo ufw status
}}
## Informational {{
    ### Help with Commands {{

    type - indicate how a command name is interpreted
    which - display which executable program will be executed
    help - get help for shell builtins
    man - display a command's manual page
    apropos - display a list of appropraite commands
    info - display a command's info entry
    whatis - display one-line manual page descriptions
    alias - create an alias for a command
    }}
    uniq - report or omit repeated lines
    wc - print newline, word, and byte counts for each file
    ### Mount a disk {{

    fdisk -l
    //list partitions

    fdisk {disk in /dev}
    // runs fdisk menu

    mkfs.ext4 {/dev/sda3}

    mkdir {place}

    mount {device} {directory}

    umount {directory}

    e2label {device} {CAPS LABEL}
    // change label

    blkir
    // list lock devices

    vi /etc/fstab
    copy uuid to here, mount point, ext4, {mount options: defaults}, {dump command: 0}, {fsck order: 1}

    mount -a
    // parses /etc/fstab and mounts, finds syntax errors

    }}
### File related commands {{

cp source source destination
mv source source destination
touch filename
mkdir dirname (-p very handy)
rmdir dirname
rm (-rf)
ln -s existingfile newlink
File archive related commands
}}
### File archive related commands {{

gzip filename
gunzip filename.gz
xz filename
xz -d filename.xz
tar -cvzf OR -xvzf (.tar.gz files)
tar -cvJf OR -xvJf (tar.xz files)
Network related commands
}}
### Network related commands {{

wget - Web downloader
links - Text based browser
scp - Secure copy
rsync - Remote copy with ssh
rdiff-backup - Remote copy with history
ping - Send ICMP ECHO_REQUEST to network hosts
traceroute - Print the route packets trace to network host
ssh - Secure SHell
Utility commands
}}
### Utility commands {{

grep - Print lines matching a pattern
less - less is more screen reader
more - if less isn't there, use more
cut - Remove sections from each line of files
diff - Find differences between two files
split - split a file into pieces
cat - Concatenate files
ldd - Print shared library dependencies
which - Shows the full path of (shell) commands
locate - Find files by name (uses updatedb generated database)
find - Search for files in a directory hierarchy
System Admin related commands
}}
### System Admin related commands {{

useradd - Create a new user account
userdel - Delete user, -r flag handy
vipw/vigr - Edit with locking
setup - Front-end menu program for other tools
system-config-whatever
TUI vs. GUI
}}
## Drive Health (smartctl) {{
Use this to check health of linux drives.
If there is a problem, it will send an email to the root account
read the email with `sudo mail`. requires mail to be installed?

sinstal smartmontools
// requires smartmontools

sudo smartctl -t short /dev/sda
// does a short test on device /dev/sda

sudo smartctl -H /dev/sda
// gets status report

smartctl
smartctl -h
}}
}}
}}

# Audio and Video {{
1TODO
EXIF
exif {filename}
//display and change EXIF data of an image. For those wondering, EXIF (stands for Exchangeable Image File Format) is typically a JPEG file

1TODO
ImageMagick
identify -verbose {filename}
//lists metadata


ffmpeg -i {filename} -metadata {key}={value} -codec copy {outfile}
//change audio or video metadata and copy to new file


https://stackoverflow.com/questions/9464617/retrieving-and-saving-media-metadata-using-ffmpeg

ffprobe -v quiet -print_format json -show_format -show_streams {filename}
}}

# SQL {{
## MySQL {{

mysql -u root
// login to mysql as root
// -p asks for password
// can log into mysql user from system?

// navigation:
show databases;
use [DATABASE];
show tables;
select * from [TABLE];
//N.B.: the show and use command will not work in SQL injections, they are internal command that are not part of SQL

select load_file('{filename}');
// doesn't allow access for most places in newer versions
// '/var/lib/mysql-files/key.txt'

}}
## Postgres {{

psql
//login as current user. -U {Username}

\list
// or \l
//lists databases

\c {database name}
//connect to database

\d
//list of tables
}}
## SQLite {{

sqlite3 {filename}
//opens sqlite database

.tables
//lists all tables

}}
## General SQL {{

    Examples {{
        Selects {{

            select * from {table}
            //display everything in table

            select max(name) from animals;

            select * from animals limit 10

            select * from animals where species = 'orangutan' order by birthdate

            select name from animals where species = 'orangutan' order by birthdate desc

            select name, birthdate from animals order by name limit 10 offset 20
            // offset is number of rows to skip

            select species, min(birthdate) from animals group by species

            '''
            select name, count(*) as num from animals
            group by name
            order by num desc limit 5
            '''
            // as num returns the result of count(*) and gives it the column title num

            //... group by columns
            //Change the behavior of aggregations such as max, count, and sum. With group by,
            //the aggregation will return one row for each distinct value in columns.

            // use group by whenever you use an aggregation

        }}
        Joins {{

            select name from animals join diet on animals.species = diet.species where diet.food = 'fish';
            select name from animals, diet where animals.species = diet.species and diet.food = 'fish';
            // equivalent

        }}
        insert into table ( column1, column2, ... ) values ( val1, val2, ... );

        update table set column = value where restriction;
        // restriction is same as select

        delete from table where restriction;
        // restriction is same as select

        %match%
        // like operator "%" like the * regex

        The having clause works like the where clause, but it applies after group by aggregations take place.
        The syntax is like this: select columns from tables group by column having condition ;

        select products.name, products.sku, count(sales.sku) as num
          from products left join sales
            on products.sku = sales.sku
          group by products.sku;
        //counts sales for all products
    }}


\# CREATE TABLE demo(t text);
\# COPY demo from '[FILENAME]';
\# SELECT * FROM demo;
\# DROP TABLE demo;


}}

## Useful sql queries {{

// Connection string for connecting from bastion to private instance, replace ip address for correct instance
Invoke-Sqlcmd -ConnectionString "Data Source=10.0.26.216,8200; User Id=admin; Password=obfuscatedPassword; TrustServerCertificate=true" -Querytimeout 10000 -Query "

### create huge bench database {{
from https://w.amazon.com/bin/view/RDS/SqlServer/Operations/usefulSQL/#Hquicklycreatealargesetofrelationaltableswithdata
```
create database bench
go
USE [bench]
GO
CREATE TABLE [dbo].[customers](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customer_orders](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customers_address](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
create index fk_addr_customer_id on customers_address(customer_id);
GO
create index fk_order_customer_id on customer_orders(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go
```
}}
### create huge bench database from powershell with default password and username {{
from https://w.amazon.com/bin/view/RDS/SqlServer/Operations/usefulSQL/#Hquicklycreatealargesetofrelationaltableswithdata
```
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
create database tempfile1
go
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customer_orders](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customers_address](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
create index fk_addr_customer_id on customers_address(customer_id);
GO
create index fk_order_customer_id on customer_orders(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"


```


tables 2 {{

query 2, same db but different tables
```
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers2](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customer_orders2](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customers_address2](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
create index fk_addr_customer_id on customers_address2(customer_id);
GO
create index fk_order_customer_id on customer_orders2(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers2]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders2]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 3 {{

query 3, same db but different tables
```
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers3](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customer_orders3](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customers_address3](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
create index fk_addr_customer_id on customers_address3(customer_id);
GO
create index fk_order_customer_id on customer_orders3(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers3]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders3]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 4 {{

query 4, same db but different tables
```
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers4](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customer_orders4](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customers_address4](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
create index fk_addr_customer_id on customers_address4(customer_id);
GO
create index fk_order_customer_id on customer_orders4(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers4]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders4]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 5 {{

query 5, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers5](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customer_orders5](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customers_address5](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
create index fk_addr_customer_id on customers_address5(customer_id);
GO
create index fk_order_customer_id on customer_orders5(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers5]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders5]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 6 {{

query 6, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers6](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customer_orders6](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customers_address6](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
create index fk_addr_customer_id on customers_address6(customer_id);
GO
create index fk_order_customer_id on customer_orders6(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers6]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders6]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

filegroup {{


### Creating filegroup, and deleting file {{


create file group
```
sqlcmd -W -Q "
CREATE DATABASE tempfile1;
USE master
GO
ALTER DATABASE tempfile1
ADD FILEGROUP Test1FG1;
GO
ALTER DATABASE tempfile1 
ADD FILE 
(
    NAME = test1dat1,
    FILENAME = 'D:\rdsdbdata\DATA\tempdbfile1.mdf',
    SIZE = 5MB,
    MAXSIZE = 1000GB,
    FILEGROWTH = 500MB
),
(
    NAME = test1dat2,
    FILENAME = 'D:\rdsdbdata\DATA\tempdbfile2.mdf',
    SIZE = 5MB,
    MAXSIZE = 1000GB,
    FILEGROWTH = 500MB
)
TO FILEGROUP Test1FG1;
GO"
```

Then write data to db using below commands
shrink data file
```
USE tempfile1;
GO
DBCC SHRINKFILE (test1dat2, EMPTYFILE);
GO
```

Then delete file
```
ALTER DATABASE tempfile1
REMOVE FILE test1dat4;
```


query for file data
```
SELECT  DB_NAME(m.database_id) as databaseName, m.*, d.state_desc as status
FROM sys.master_files m, sys.databases d
WHERE m.database_id = d.database_id;
```


}}

}}

tables 7 {{

query 7, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers7](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders7](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address7](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address7(customer_id);
GO
create index fk_order_customer_id on customer_orders7(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers7]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders7]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 8 {{

query 8, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers8](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders8](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address8](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address8(customer_id);
GO
create index fk_order_customer_id on customer_orders8(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers8]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders8]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 9 {{

query 9, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers9](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders9](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address9](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address9(customer_id);
GO
create index fk_order_customer_id on customer_orders9(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers9]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders9]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 10 {{

query 10, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers10](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders10](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address10](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address10(customer_id);
GO
create index fk_order_customer_id on customer_orders10(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers10]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders10]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 11 {{

query 11, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers11](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders11](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address11](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address11(customer_id);
GO
create index fk_order_customer_id on customer_orders11(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers11]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders11]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 12 {{

query 12, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers12](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders12](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address12](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address12(customer_id);
GO
create index fk_order_customer_id on customer_orders12(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers12]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders12]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 13 {{

query 13, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -Querytimeout 10000 -Query "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers13](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders13](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address13](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address13(customer_id);
GO
create index fk_order_customer_id on customer_orders13(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers13]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders13]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 14 {{

query 14, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -Querytimeout 10000 -Query "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers14](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders14](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address14](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address14(customer_id);
GO
create index fk_order_customer_id on customer_orders14(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers14]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders14]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 15 {{

query 15, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -Querytimeout 10000 -Query "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers15](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders15](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address15](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address15(customer_id);
GO
create index fk_order_customer_id on customer_orders15(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers15]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders15]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 16 {{

query 16, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -Querytimeout 10000 -Query "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers16](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders16](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address16](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address16(customer_id);
GO
create index fk_order_customer_id on customer_orders16(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers16]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders16]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 17 {{

query 17, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -Querytimeout 10000 -Query "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers17](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders17](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address17](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address17(customer_id);
GO
create index fk_order_customer_id on customer_orders17(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers17]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders17]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 18 {{

query 18, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -Querytimeout 10000 -Query "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers18](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders18](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address18](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address18(customer_id);
GO
create index fk_order_customer_id on customer_orders18(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers18]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders18]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

tables 19 {{

query 19, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
sqlcmd -W -t 10000 -Q "
Invoke-Sqlcmd -Querytimeout 10000 -Query "
USE [tempfile1]
GO
CREATE TABLE [dbo].[customers19](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customer_orders19](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
CREATE TABLE [dbo].[customers_address19](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [Test1FG1]) ON [Test1FG1]
GO
create index fk_addr_customer_id on customers_address19(customer_id);
GO
create index fk_order_customer_id on customer_orders19(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers19]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders19]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}

}}

tables 4, msdb {{

query 4, same db but different tables
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
USE [msdb]
GO
CREATE TABLE [dbo].[customers4](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customer_orders4](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customers_address4](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
create index fk_addr_customer_id on customers_address4(customer_id);
GO
create index fk_order_customer_id on customer_orders4(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers4]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders4]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"
```

}}


Always On query {{


```
ALTER DATABASE [db] SET HADR OFF;
```


}}

### create huge bench database from powershell remote server {{
from https://w.amazon.com/bin/view/RDS/SqlServer/Operations/usefulSQL/#Hquicklycreatealargesetofrelationaltableswithdata

```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=password" -ServerInstance "sqlserver-millrben-1.cbyx5cm4ck7c.us-west-2.rds.amazonaws.com,1433" -Querytimeout 10000 -Query "
create database bench2
go
USE [bench2]
GO
CREATE TABLE [dbo].[customers](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customer_orders](
        [customer_id] [int] NULL,
        [order_id] [int] IDENTITY(1,1) NOT NULL,
        [item_name] [varchar](100) NULL,
        [item_id] [varchar](100) NULL,
        [description] [varchar](500) NULL,
        [alt_customer_id] [varchar](20) NULL,
        [order_date] [date] NULL,
        [ship_date] [date] NULL,
        [status] [varchar](1) NULL,
PRIMARY KEY CLUSTERED ([order_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
CREATE TABLE [dbo].[customers_address](
        [customer_id] [int] NULL,
        [address_id] [int] IDENTITY(1,1) NOT NULL,
        [street1] [varchar](100) NULL,
        [street2] [varchar](100) NULL,
        [city] [varchar](100) NULL,
        [state] [varchar](2) NULL,
        [zip] [varchar](10) NULL,
PRIMARY KEY CLUSTERED ([address_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO
create index fk_addr_customer_id on customers_address(customer_id);
GO
create index fk_order_customer_id on customer_orders(customer_id);
GO

-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
while @counter < 1000000
begin
                set @counter = @counter + 1
        INSERT INTO [dbo].[customers]([fname],[lname],[description]) VALUES('Rds', 'RandyMachoManSavage','inserting fake customer rows for mysql stab testing')
        set @customer = @@identity
                select @customer
        INSERT INTO [dbo].[customer_orders]([customer_id],[item_name],[item_id],[description],[alt_customer_id],[order_date],[ship_date],[status])
        select top 1000 @customer,'RDS database' as item_name,'RDS-1234567889' as item_id,'inserting fake customer rows for mysql stab testing' as description,'123456789' as alt_customer_id,getdate() as order_date,null as ship_date,'N' as status from sys.all_objects
end
go"


```
}}
### delete from huge bench database {{
```
USE [bench]
GO
-- this will create co table of 137g with 1,000,000 iterations
declare @customer int
declare @counter int
set @customer = 0 
set @counter = 0 
begin
        SELECT COUNT(customer_id) from [dbo].[customers]
		DELETE FROM [dbo].[customers] WHERE customer_id > 650000
        SELECT COUNT(customer_id) from [dbo].[customers]

		SELECT COUNT(order_id) from [dbo].[customer_orders]
		DELETE FROM [dbo].[customer_orders] WHERE customer_id > 650000
        SELECT COUNT(order_id) from [dbo].[customer_orders]
end
go
```
}}
## many dbs {{
### Create many databases {{

// https://www.techbrothersit.com/2015/06/how-to-create-100s-of-sample-databases.html
// nifty blog
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
--Create Variables
Declare @DataFilePath VARCHAR(100)
Declare @LogFilePath VARCHAR(100)
Declare @SubPartDBName VARCHAR(100)
Declare @StartCnt int
Declare @MaxDBCnt int

--Set the Variable Values, @MaxDBCnt is Number of Databases you want to Create
SET @StartCnt=1
SET @MaxDBCnt=301

--Provide the Data File Path And Log File Path
SET @DataFilePath='D:\rdsdbdata\DATA\'
SET @LogFilePath='D:\rdsdbdata\Log\'
--Chose the First part of your DB name, Let's say TEST is chosen then Database will be created Test1,Test2....Test100
SET @SubPartDBName='Test'


--Create Databases
While ( @startCnt<@MaxDBCnt)
BEGIN

Print CAst(@startCnt AS VARCHAR(100))
DECLARE @DBFullName VARCHAR(500) =@SubPartDBName+CAST(@StartCnt AS VARCHAR(10))
DECLARE @SQL NVARCHAR(MAX)
SET @SQL= 'CREATE DATABASE ['+@DBFullName+']

 ON 
( NAME = N'''+@DBFullName+''', FILENAME = N'''+@DataFilePath+@DBFullName+'.mdf'' ,
 SIZE = 4096KB , FILEGROWTH = 1024KB )
 LOG ON 
( NAME = N'''+@DBFullName+'_log'', FILENAME = N'''+@LogFilePath+@DBFullName+'_log.ldf'' ,
 SIZE = 1024KB , FILEGROWTH = 10%)'
SET @startCnt=@startCnt+1
Print @SQL
Execute (@SQL)
END"
```
}}
### create table on many databases {{

```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
--Create Variables
Declare @DataFilePath VARCHAR(100)
Declare @LogFilePath VARCHAR(100)
Declare @SubPartDBName VARCHAR(100)
Declare @TableName VARCHAR(100)
Declare @StartCnt int
Declare @MaxDBCnt int

--Set the Variable Values, @MaxDBCnt is Number of Databases you want to Create
SET @StartCnt=1
SET @MaxDBCnt=2

--Chose the First part of your DB name, Let's say TEST is chosen then Database will be created Test1,Test2....Test100
SET @SubPartDBName='Test'
SET @TableName='TestTable'


-- Databases
While ( @startCnt<@MaxDBCnt)
BEGIN

Print CAST(@startCnt AS VARCHAR(100))
DECLARE @DBFullName VARCHAR(500) =@SubPartDBName+CAST(@startCnt AS VARCHAR(10))
DECLARE @SQL NVARCHAR(MAX)
SET @SQL= 'USE ['+@DBFullName+'];

CREATE TABLE ['+@TableName+'] (TestColInt int,TestColFloat FLOAT(8));

INSERT INTO ['+@TableName+'] (TestColInt,TestColFloat) VALUES (1,1.96);'

SET @startCnt=@startCnt+1
Print @SQL
Execute (@SQL)
END"
```
}}
### Delete many databases {{
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 10000 -Query "
--Create Variables
Declare @DataFilePath VARCHAR(100)
Declare @LogFilePath VARCHAR(100)
Declare @SubPartDBName VARCHAR(100)
Declare @StartCnt int
Declare @MaxDBCnt int

--Set the Variable Values, @MaxDBCnt is Number of Databases you want to Create
SET @StartCnt=500
SET @MaxDBCnt=5001

--Provide the Data File Path And Log File Path
SET @DataFilePath='D:\rdsdbdata\DATA\'
SET @LogFilePath='D:\rdsdbdata\Log\'
--Chose the First part of your DB name, Let's say TEST is chosen then Database will be created Test1,Test2....Test100
SET @SubPartDBName='Test'


--Create Databases
While ( @startCnt<@MaxDBCnt)
BEGIN

Print CAst(@startCnt AS VARCHAR(100))
DECLARE @DBFullName VARCHAR(500) =@SubPartDBName+CAST(@StartCnt AS VARCHAR(10))
DECLARE @SQL NVARCHAR(MAX)
SET @SQL= 'DROP DATABASE ['+@DBFullName+']'
SET @startCnt=@startCnt+1
Print @SQL
Execute (@SQL)
END"
```
}}
}}

## Continuously write data {{
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
create database bench
go
USE [bench]
GO

SET NOCOUNT ON
DECLARE @i INT = 1
WHILE (@i <= 1000)
 BEGIN
  WAITFOR DELAY '00:00:01'
 DECLARE @sql AS NVARCHAR(500)
 SET @sql = 'select top 1000 o.* into [' + CONVERT(NVARCHAR(50), NEWID()) +'] from master.sys.objects o, master.sys.objects a, master.sys.objects b, master.sys.objects c' 
 EXECUTE sp_executesql @sql
 SET  @i = @i + 1;
END
"
```

}}
### Get db info {{

Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
SELECT name, state_desc FROM sys.databases;
go"

```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Query "
SELECT
    db.name AS DatabaseName,
    db.create_date AS CreateDate,
    db.state_desc AS DatabaseState,
    db.database_id AS DatabaseId,
    rs.database_guid AS DatabaseGuid,
    rs.last_log_backup_lsn AS LastLogBackupLSN,
    rs.recovery_fork_guid RecoveryForkGuid,
    rs.first_recovery_fork_guid AS FirstRecoveryForkGuid,
    db.recovery_model_desc AS RecoveryModel,
    db.is_auto_close_on AS IsAutoClose,
    CASE WHEN db.source_database_id IS NULL THEN 0 ELSE 1 END  AS IsDatabaseSnapshot
FROM sys.databases db
    INNER JOIN sys.database_recovery_status rs
    ON db.database_id = rs.database_id
WHERE DB_NAME(db.database_id) NOT IN ('tempdb');
"
```

Invoke-Sqlcmd -ConnectionString "User Id=rdstest; Password=obfuscatedPassword" -Query "
SELECT d.name as Name FROM sys.databases d WITH (NOLOCK);
"
```
}}
### Create some tables {{
```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
-- CREATE DATABASE Test1;
-- GO
USE Test1;
-- CREATE TABLE table1 ( CUSTOMER_ID VARCHAR(20) NOT NULL , ACCOUNT_ID VARCHAR(20) NOT NULL );
-- CREATE TABLE table2 ( CUSTOMER_ID VARCHAR(20) NOT NULL , ACCOUNT_ID VARCHAR(20) NOT NULL );
CREATE TABLE table3 ( CUSTOMER_ID VARCHAR(20) NOT NULL , ACCOUNT_ID VARCHAR(20) NOT NULL );
"

Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
USE Test1
SELECT * FROM table1
"

Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
SELECT
  *
FROM
  Test1.INFORMATION_SCHEMA.TABLES;
GO
"
```
}}
### Create server trigger {{

use master;
-- create table LoginActivity
CREATE TABLE LoginActivity (LOGONEvent XML ,Logintime datetime);
 
-- create trigger track_logins
CREATE TRIGGER [track_logins] ON ALL SERVER
FOR LOGON AS 
BEGIN
 INSERT INTO LoginActivity
 SELECT EVENTDATA()
  ,GETDATE()
END
-- Check the server level trigger status
select * from sys.server_triggers;
-- Enable all server level triggers
--The following example enable all DDL triggers that were created at the server scope.
ENABLE Trigger ALL ON ALL SERVER;  
-- Disable all server level triggers
--The following example disables all DDL triggers that were created at the server scope.
DISABLE Trigger ALL ON ALL SERVER;

}}
### Create Table trigger {{

USE [secondDb];
GO

CREATE TABLE [dbo].[triggertable](
        [customer_id] [int] IDENTITY(1,1) NOT NULL,
        [fname] [varchar](100) NULL,
        [lname] [varchar](100) NULL,
        [description] [varchar](500) NULL,
PRIMARY KEY CLUSTERED ([customer_id] ASC)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]
GO


CREATE TRIGGER reminder2
ON dbo.triggertable
AFTER INSERT, UPDATE
AS RAISERROR ('Notify Customer Relations', 16, 10);
GO

}}
### Create database trigger {{

USE firstDb;
GO

CREATE TRIGGER safety
    ON DATABASE
    FOR DROP_SYNONYM
    AS IF (@@ROWCOUNT = 0)
           RETURN;
       RAISERROR ('You must disable Trigger "safety" to remove synonyms!', 10, 1);
       ROLLBACK;
GO

}}
## TDE setup {{

```
Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
select * from sys.certificates;
go


CREATE MASTER KEY ENCRYPTION BY PASSWORD = 'P@$$w0rd';
GO

select * from sys.symmetric_keys;
go

CREATE CERTIFICATE TDE_Certificate WITH SUBJECT = 'TDE_Cert',
START_DATE = '2023-10-01',
EXPIRY_DATE = '2029-12-12';
GO

-- ###### Create database-1
create database 'spaces2';
go

USE 'spaces2'
CREATE TABLE Marvel
(ID        INT PRIMARY KEY, 
 Name     VARCHAR(30) NOT NULL, 
 Seq VARCHAR(10) NOT NULL
);
GO


Insert into Marvel (ID,Name,Seq)
            Select 1,'IronMan',11111111 UNION ALL
            Select 2, 'SpiderMan',22222222 UNION ALL
            Select 3, 'Hulk',33333333 UNION ALL
            Select 4,'captainAmerica',44444444 UNION ALL
            Select 5, 'captainMarvel',55555555;
go

USE 'spaces2'
GO
CREATE DATABASE ENCRYPTION KEY
WITH ALGORITHM = AES_256
ENCRYPTION BY SERVER CERTIFICATE TDE_Certificate;
GO


ALTER DATABASE 'spaces2' SET ENCRYPTION ON;
GO

-- ####Validate 'spaces2' , temp is in output
select db_name(database_id) as DBName,encryption_state,encryption_state_desc,percent_complete from sys.dm_database_encryption_keys;
go"
```

Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
select db_name(database_id) as DBName,encryption_state,encryption_state_desc,percent_complete from sys.dm_database_encryption_keys;
go"

Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
select * from sys.symmetric_keys;
go"

Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
SELECT name, state_desc FROM sys.databases;
go"


Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
USE DB1
CREATE TABLE Marvel3
(ID        INT PRIMARY KEY, 
 Name     VARCHAR(30) NOT NULL, 
 Seq VARCHAR(10) NOT NULL
);
GO


Insert into Marvel3 (ID,Name,Seq)
            Select 1,'IronMan',11111111 UNION ALL
            Select 2, 'SpiderMan',22222222 UNION ALL
            Select 3, 'Hulk',33333333 UNION ALL
            Select 4,'captainAmerica',44444444 UNION ALL
            Select 5, 'captainMarvel',55555555;
go"

Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
USE DB1
SELECT * FROM Marvel
GO
"

Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
USE DB1
SELECT * FROM Marvel2;
GO
"


Invoke-Sqlcmd -ConnectionString "User Id=admin; Password=obfuscatedPassword" -Querytimeout 1000 -Query "
SELECT
  *
FROM
  DB1.INFORMATION_SCHEMA.TABLES;
GO
"

}}

}}
}}
# Programming Langs {{
## Perl{{
perl -e 'print `bash`'
// back ticks are system commands. single quote treats expression as a whole. " evaluates backticks first
}}
## Python {{
executing bash from python {{
```
from subprocess import call
call(['bash'])

import os
os.system('bash')
os.popen('bash').read()
__import__('os').system(...)

str(os.system('bash')) # for code execution will sometimes only return the return code, so use the popen way

str(__import__('os').popen(str(__import__('base64').b64decode('{command}'))).read())
// to base64 encode
```
}}

// Use pipreqs to scan imports and create requirements.txt file with only top level dependencies
// not perfect, but goes a long way
pip install pipreqs
pipreqs ./

// pdm is helpful for converting setup.py to pyproject.toml
```bash
pip install pdm
pdm add setuptools
pdm init # sets up venv and license and stuff
pdm import setup.py # regenerates file from setup.py
```

}}
## Ruby {{
ruby -e 'require "irb" ; IRB.start(__FILE__)'
`[COMMAND]`
//runs system command

"+"
//String Concatenation

`uname`
runs uname on system
}}
## node {{
node -e '...' followed by valid JavaScript code

var exec = require('child_process').exec;
exec('[COMMAND]', function (error, stdOut, stdErr) {
console.log(stdOut);
});
}}
## PHP {{
"//"
//Comment

"."
//String Concatenation

system("ls")
//Run ls on system

### Vulnerabilities {{
PCRE_REPLACE_EVAL (/e) his modifier will cause the function preg_replace to evaluate the new value as PHP code, before performing the substitution.

PCRE_REPLACE_EVAL has been deprecated as of PHP 5.5.0
}}
}}
Rust {{
Cargo {{
cargo doc -p {dependency} --open
// builds docs for dependency and opens in browser

cargo doc --open
// supposed to include all documentation for all dependencies, Sometimes does
}}
}}

try `uname`, or $(uname) or system('uname')
}}
