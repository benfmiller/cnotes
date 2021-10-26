#
Powershell {{
While(1) {ps | sort -des cpu | select -f 15 | ft -a; sleep 1; cls}
> // This shows cpu time, which is like cpu usage
}}
# Git Bash {{

.inputrc
set bell-style none
thank god removes bash screen blind

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
# Jekyll {{
sudo apt-get install ruby-full build-essential zlib1g-dev

echo '# Install Ruby Gems to ~/gems' >> ~/.zshrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.zshrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

gem install jekyll bundler

bundle exec jekyll serve
}}
# Vagrant {{
vagrant up
// in directory with vagrant file

vagrant ssh
// ssh into vagrant box

//Look at vagrant file for example stuff!
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

https://vpn.msu.montana.edu

/usr/bin/setxkbmap -option "ctrl:nocaps"
//include in .profile to map ctrl to caps

i3 {{
sudo add-apt-repository -y ppa:regolith-linux/stable
sinstal i3-gaps

sinstal i3status
sinstal i3blocks
sinstal playerctl
sinstal flameshot
sinstal compton

// for lock on screen close
sinstal xss-lock

sudo apt-get install lxappearance gtk-chtheme

apt install feh fonts-font-awesome rofi pulseaudio-utils xbacklight alsa-tools clipit gcc git terminator locate pcmanfm libnotify-bin acpi

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

}}

// instructions to mount cifs drive
https://markontech.com/linux/mount-a-network-shared-drive-on-linux/
https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!

//fix root only writes
https://ubuntuforums.org/showthread.php?t=1409720

# Commands {{

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
}}
# Programming Langs {{
## Perl{{
perl -e 'print `bash`'
// back ticks are system commands. single quote treats expression as a whole. " evaluates backticks first
}}
## Python {{
from subprocess import call
call(['bash'])

import os
os.system('bash')
os.popen('bash').read()
__import__('os').system(...)

str(os.system('bash')) # for code execution will sometimes only return the return code, so use the popen way

str(__import__('os').popen(str(__import__('base64').b64decode('{command}'))).read())
// to base64 encode
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
