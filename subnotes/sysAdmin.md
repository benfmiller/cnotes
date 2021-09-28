# up to quiz 1 {{
## Introduction {{
All lectures for this class will be available in the webm and or mp4 formats which should play fine with the Firefox and Google Chrome web browsers.  Feel free to right-click on any video link and download it to play with your preferred video player.  VLC is recommended.

==========================

About Scott Dowdle

CS System Administrator since August 2005 (Now embedded NACOEIT under the UIT)
System Administrator for Rocky Mountain College from 2000 - 2005
Montana Communications Network - 1998 - 2000
Linux user since January of 1995
Brightspace LE (formerly D2L, Desire 2 Learn)

While this is a "Blended" course all of the material will be made available via Brightspace to provide text resources, homework assignments. quizzes, the mid-term and final exam.  Having all of the content available online is not new / just because of the COVID19 pandemic.  I have been putting my materials online for years and it is a format that has worked well according to the course / instructor surveys.  In the past I preferred paper measurement (quizzes, mid-term, final) but now those are in Brightspace too.  Please note that I DO NOT use the Brightspace gradebook.  Homework feedback and grade will be provided to you via a text file on your student virtual machine... which will encourage more ssh / shell usage.
Course and Student Virtual Machines

There is a course server for the class (csci351.cs.montana.edu) which has a public IP address and is accessible via ssh.  You will need an ssh client to access the course server and there are several to pick from for Microsoft Windows, macOS, and Linux.  Students can access the course server with their netid account.  To access via campus wifi, you should be on the MSU Secure network.  If you have unresolvable issues with and can't connect to the MSU Secure network, MSU Guest may be used in conjunction with the MSU VPN client.  The course server is accessible from off-campus without requiring a VPN connection.
Each student will be assigned a student KVM virtual machine (CentOS 8) of their own to do task-oriented homework assignments. Each student virtual machine will have a non-routable, private IP address which is accessible via ssh from the course server.  Initially there is only the root account but in homework 1, students will create a user account for themselves.
CSCI 351 Topics (see Calendar PDF for specific weeks/dates)

History - Unix, Free Software and Linux
What is a Linux Distribution?
What is a System Administrator?
OS Installation and System Updates
CLI use: bash, hot keys, job control
Users accounts
Hard disks, partitions, and file systems
Linux file system hierarchy
Commandline Potpourri
Understanding file/dir ownership and permissions
Package managers
Processes and Process Management
systemd and Service Management
Backups
Desktop Linux
Network Configuration
Printing with CUPS
Firewalls & iptables
System logs and Monitoring
Automation with cron
Server apps: Email
Server apps: Apache
Server apps: MariaDB
Server apps: DNS
Virtualization Introduction
KVM
System Containers (LXC)
Application Containers (podman)
VDI
Please note that while there are two topics specifically dedicated to the command line and various command line tools (CLI use, Command Line Potpourri), continued learning and practice throughout the entire semester is required.  Each week one or two chapters out of The Linux Command Line book will be assigned in addition to the topics mentioned above.

Course Resources

Lab machines (Barnard 254, any MSU Global Student Lab, etc)
Course and Student VMs
Student laptops and home machines (optional)
}}
## Thursday - History - Unix, Free Software and Linux {{

In the Beginning
    Room size computers with vacuum tubes
    No operating systems
    All software was custom
    Virtually no commercial software
    Community of sharing

The Industry Evolves
    Eventually hardware vendors provided operating environments
    Every make / model had its own OS
    Portable programming languages start to appear

Birth of UNIX at AT&T Bell Labs (1969)
    Multics committee (multi-company)
    Dennis Ritchie, Ken Thompson and Brian Kernighan
    C begat UNIX which begat C
    US FTC anti-trust investigation
    UNIX at Uni
    Legitimized Computer Science
    AT&T broken up into "Baby Bells"
    Bell Labs and UNIX commercialization

Richard Stallman (RMS)
    MIT Artificial Intelligence Laboratory
    ITS OS (Incompatible Timesharing System)
    Lost co-workers to vendor UNIXes
    Mad at printer makers
    GNU Project (Sep. 1983)
    "GNU's Not UNIX"
    GNU Manifesto (1985)
    Free Software Foundation (FSF)
     GNU Public License (GPL)

Berkeley Software Distribution (BSD)
    Bill Joy at USC Berkeley
    BSD originally a remixed UNIX
    Became its own thing
    BSDi sued by USL in 1992

Andrew S. Tanenbaum (AST)
    MIT in the 60's
    Physics and Astrophysics
    Moved to Netherlands, VU University Amsterdam
    Several CS Textbooks
    Minix (Prentice Hall)

Linus Torvalds
    University of Helsinki (1988-96)
    Wanted to make his own UNIX
    Bootstrapped it with Minix
    Wanted to call it Freax
    Announced Linux ~1991

Why Red Hat Enterprise Linux?
    They contribute to the community / ecosystem a lot
    No really!
    Often top contributor to each Linux kernel
    Owns Cygnus (Cygwin) and many others
    Contributes to many, many ecosystems projects
    https://www.redhat.com/en/about/open-source-program-office/contributions

Why CentOS? (now AlmaLinux)
    Free (as in beer and freedom) clone of RHEL
    Sponsored by Red Hat
    Also clones most of Red Hat’s other projects
    My server distro of choice

Why Fedora?
    Upstream of RHEL
    Sponsored by Red Hat
    Four F's (Freedom, Friends, Features, First [Firehose of updates])
    My desktop distro of choice

Open Source vs Free Software
    Free Software (Free Software Foundation)
        Free as in Freedom
        CAN charge for it
        Ensures the Four Freedoms
            Use
            Examine
            Redistribute
            Modify
    Open Source (Open Source Inititive)
        A development model
        More business oriented

Things to Ponder
    Using proprietary software is like having a car with the hood welded shut
    FOSS (Free and Open Source Software) is like an insurance policy
    Which is more free?  The GPL or the BSD license? Depends on who you ask

TLCL book put it like this:
Many people speak of “freedom” with regard to Linux, but I don't think most people know what this freedom really means. Freedom is the power to decide what your computer does, and the only way to have this freedom is to know what your computer is doing. Freedom is a computer that is without secrets, one where everything can be known if you care enough to find out.

(Introduction page xvi)

REFERENCES:

A Quarter Century of UNIX by Peter H. Salus (1994)
The Daemon, the GNU & the Penguin also by Dr. Salus (2006)
}}
## What is a Linux Distribution? {{
What is a Linux distribution?

A Linux distribution is the Linux kernel provided with a collection of additional software such that it can be booted on a computer from optical media, floppy disk, USB thumbdrive, etc... and is most often installable to permanent storage. A distribution may or may not provide periodic software updates to fix software bugs and remedy security problems.

There are over 500 different Linux distributions. Why do so many exist?

Most of them inherit from one of the major distros:

    Debian
    Slackware
    Red Hat

So many exist for a number of reasons:
    The source is there and the license lets you roll your own
    Localization - Country/Language specific
    Specific CPU arch - PPC, Alpha, ARM, SPARC, etc
    Specific devices - Linksys router, Raspberry Pi, ODROID, Android devices, etc
    Specific storage - Floppy, CD, Zip disk, small HD, diskless terminal, etc
    Specific software - Desktop env, special software or configuration, etc
    Specific use case - KVM virtualization host, Container host, Python Programming, Gaming, etc
    Educational - Linux from Scratch

How does one Linux distribution differ from another:
    Installer
    Software available (desktop spins)
    Administration tools (GUI, TUI, CLI)
    Init system (SysV init, upstart, OpenRC, systemd)
    Developers and community / Company
    95% of the same software

Why does Scott like Red Hat and Fedora?

See: Is Red Hat still relevant? You bet.
What about Ubuntu or other distributions?

Resources:
    Linux Weekly News' Distributions page
    DistroWatch
}}
## What is a System Administrator?{{
What exactly is a "System Administrator"?

System administration is a very broad topic and depending on a particular job or company it can range from being a "jack of all trades but master of none" to being very specialized. This course is going to attempt to give as broad a base of sysadmin information / experience as possible without being able to delve too deeply into any particular topic.

Specialized types:

    Web server - Often referred to as webmaster
    Database - Often referred to as DBA
        Oracle
        MySQL
        PostgreSQL
    Email - Often referred to as postmaster
    Network Administrator
    Security
    Storage Management
    Virtualization
    Any other server application you can think of

Working with End Users

A System Administrator, whether warranted or not, often has a reputation for not being a "people person". They are often seen as grumpy, lazy and someone who speaks a language all their own... filled with technical jargon that non-computer types don't understand.
    End users don't usually formulate their questions very well.
    End users are often uncomfortable talking to a system administrator and feel as they will be perceived as being stupid or negligent.
    They often have misinformation or a bad understanding of how something works.
    It is up to you to ask questions before you start providing answers so you can make sure you understand what they really need / want. It is often useful to back up from a problem or request and try to see the bigger picture.
    Try your best to educate your users and show them how to collect troubleshooting information so they can become partners rather than adversaries.
    After a few positive experiences some of your users may end up becoming "assistant administrators" because you have educated them where they may be able to help others.
    Try to find multiple solutions rather than just the simplest and if appropriate, let the end user choose which one is better for them.
    End users often have good ideas. Make sure to acknowledge them and try to apply them where appropriate.
    Having a good relationship with your customers will always make your job easier.
    Don't be afraid to say you don't know something and that you'll have to do some research.
    Make sure to follow through to completion in a timely fashion and do follow-up calls / visits to ensure a solution is working.
    Recognize when you need to create documentation for yourself and your users. Use FAQs or SOPs. Provide your users with as much documentation as they are comfortable with.
    Try to track problems and recognize trends with users, software, and hardware.
}}
## CLI use {{
Please note: Getting hands on practice with the shell is critical. Simply reading over this material or listening to a lecture is not good enough. Each student needs to spend a significant amount of time at the command line, getting to know the keyboard, the hot keys, and the various commands that are available. This will be an ongoing exercise throughout the entire semester.  Also notice the "Command Tutorial Screencast" content item in the General Resources section for some additional videos like tmux, mc, nano and vi tutorials.

/bin/bash - GNU Bourne-Again SHell

Many users who come from a Windows / DOS background see the bash command prompt and assume it is similar to DOS. Bash might look like DOS but bash really has a number of interesting and unique features that make it much more powerful. Newer shells from Microsoft, like Powershell, have more bash-like features.

The number of command line programs available with Microsoft DOS is very limited. Unix / Linux has a large number of command line tools. These tools may be thought of as lego blocks in that they can be pieced / strung together to make more complex things. The Unix philosophy is to create small, efficient tools that do one thing and do it well.

Hot-keys (provided by readline)

The command line includes a mini word processor
emacs-mode (default) and vi-mode

^a - Beginning of line (home)
^e - End of line (end)
^k - Delete from cursor to end of line
^d - Delete char under cursor (del)
^h - Backspace (backspace)
^f - Forward one char (right arrow)
^b - Back one char (left arrow)
^l - clear screen (same as clear command)
esc d - delete word right
^s - Suspend terminal output
^q - Resume terminal output
Note: ^ = The control key on your keyboard, not shift-6
Tab completion

Expands commands and file / dir names
tab - Complete typing if unique enough
tab tab - Show what matches
Extended with optional bash-completion program
Command history

history - Internal bash command
!n - Repeat command n from history
up arrow - Go back one entry in history
down arrow - Forward one entry in history
^r - Reverse-incremental-search
Job control

bash allows for multitasking by offering job control
^z - Suspend interactive process
jobs - Lists jobs
fg n - Put job n in the forground
bg n - Put job n in the background
^c - Terminate interactive process
Your ENVironment

When you login and are given a shell prompt, a set of configuration files are parsed and a user environment is established. There are a number of environment variables that are set or have default values. To see the environment specifics you can run the env command to show all of the name and value pairs:

$ env
{long list of environment variables and their values is printed}

Some of the more important ones are:

PATH - A list of directories that are searched for binaries when you type a command

EDITOR - Often not set and defaults to vi. This is the text editor that is used when one is called for. Examples include vipw and edquota.

PAGER - Often not set and defaults to less if available or more. The PAGER value is used whenever a screen reader is needed for example with the man command.

To echo the contents of a given variable:

$ echo $HOME
{shows value}

To set a value to a variable, do the following:

$ export VARIABLENAME=value

for example

$ export PAGER=more

Some programs expect certain variables to be set and you can automate that by adding statements to the configuration file(s) that your shell processes upon startup. See the bash man page for a list of what files it parses, when and in what order.
Getting to know less

It is important that you master the less command so you can read man pages effectively.

Here are the basics of using less:

arrow down - scroll down a line
arrow up - scroll up one line
/searchstring<enter> - search for text in less
n - next search match
N - previous search match
g - goto top
G - goto bottom
q - quit
h - help

Please note that the keys used are case sensitive and Q is not the same as q. Look a the internal help for a good overview of all of the hotkeys. At the very least you need to be able to move around, search, and quit.

Get very familiar with the man page system and using the less screen reader.
More on man pages

The man command is the primary interface for reading documentation from the command line.

Read the man man page.  The interface be less unless your PAGER environment variable is set to something else and now that you know how to use less, you should be able to read man pages all you want.  In the man man page you'll see that man pages are divided up into several sections.  Sometimes there is more than one man page with the same name.  Understand how "man 1 passwd" is different from "man 5 passwd".

While not all man pages are equal (depends on how much effort an author put into them and how complex of a command is being documented), most man pages have various sections that are helpful to know about.  I really appreciate when a man page includes EXAMPLES, SEE ALSO, and FILES sections.

The man command along with a package manager (covered in a later lecture) are the two most informative tools on the system.
}}
## User Account {{
UNIX and LINUX Administration Handbook - Chapter 7 - Adding New Users

Related files (ensure the man-pages package is installed)
    /etc/passwd
    /etc/shadow
    /etc/group
    /etc/gshadow
    /etc/login.defs
    /etc/security/limits.conf (pam package)
    /etc/skel/ (contains files/dirs copied to homedir of new accounts)

/etc/passwd (man 5 passwd)
    dowdle:x:1000:1000:Scott Dowdle:/home/dowdle:/bin/bash
        1 - User name
        2 - Encrypted password, an \*, or an x (see pwconv)
        3 - UID
        4 - GID
        5 - GECOS - See: Wikipedia GECOS page
        6 - Home Directory
        7 - Default Shell

/etc/shadow (man 5 shadow)
    dowdle:$1$vkI/ffyR$rSsCe9K.GsuK83.cWI:14277:0:99999:7:::
        1 - User name
        2 - Encrypted password
        3 - Days since Jan 1, 1970 that password was last changed
        4 - Days before password may be changed
        5 - Days after which password must be changed
        6 - Days before password is to expire that user is warned
        7 - Days after password expires that account is disabled
        8 - Days since Jan 1, 1970 that account is disabled
        9 - A reserved field
        See: Wikipedia page on UNIX time

/etc/group (man 5 group)
    dowdle:x:1000:dowdle
        1 - Group name
        2 - Encrypted password if used
        3 - GID
        4 - Comma separated user list

Related Commands and Issues
    /usr/sbin/useradd
    /usr/sbin/adduser -> useradd
    /usr/bin/chfn (Let's users adjust the GECOS)
    /usr/sbin/usermod (usermod -aG wheel dowdle)
    /usr/bin/passwd (What are the permissions on this file?)
    rpm -ql shadow-utils (shows package contents)
    /usr/bin/whoami
    /usr/bin/id
    What is an orphaned file?

Escalating privileges
    sudo, sudo -i (users in wheel group, other distros may use sudo group)
    su, su -l (need to know the root password unless already root)

Everything mentioned above is for "local" accounts.  If this were an advanced sysadmin class we'd cover various forms of centralized authentication like LDAP and NIS/YP as well as integration with systems like FreeIPA and Microsoft Active Directory.  Many Linux distributions work well with centralized authentication systems.  In the case of Red Hat-derived distributions, they offer authconfig, sssd, realmd and freeipa-client.
}}
## Hard disks, partitions, and filesystems {{
REFERENCE
LaUSAH Chapter 8, Storage
TLCL Chapter 15, Storage Media

Hard Drives
    Types
        IDE / ATA / PATA (two connectors, 40 or 80 pin)
        SATA
        SSD
        SCSI
        SAS
        Fiber Channel
        USB, Firewire, eSATA
    Single disk
    Multiple disks
    Disk image file
    RAID 0, 1, 5, 10
        hardware - BIOS - disk based
        software - mdadm - disk or partition based
    NAS - NFS, SMB (service oriented filesharing)
    SAN - iSCSI, ATA over Ethernet (AoE)
    LVM - lvm, system-config-lvm

Partitioning Applications
    fdisk - fdisk -l (lists all drives seen) (gdisk or parted/gparted for GPT)
    sfdisk
        sfdisk -d /dev/hda > hda.out
        sfdisk /dev/hda < hda.out
    gdisk
    parted / gparted
    mount, umount
    Commercial products
        Partition Magic
        Partition Commander

Partitioning Schemes
    PC hardware (with an MBR partition table) can have upto 4 primary partitions. If you need more than 4 partitions you'll have to make at least one "extended" partition. Extended partitions are containers for "logical" partitions. Largest partition size is 2TB.
        /
        /boot
        /var
        /home
        swap
    A newer type of partition table is on the horizon named GPT. GPT eliminates a number of the restrictions of the MBR partition table. By default, GPT offers 128 partitions (more if desired) as well as partitions > 2TB. For more information see:
    http://en.wikipedia.org/wiki/GUID_Partition_Table

Filesystems
    Types
        ext2, ext3, ext4
        swap
        xfs
        reiser3
        ntfs
        vfat
        iso9660
        ufs
        zfs (Solaris), openzfs (BSDs, Linux, macOS), btrfs (Linux)
    Formating commands
        mkfs.*, mkfs.ext3, mkfs.ext4, etc
        mkswap
        mkfs.ntfs, mkfs.vfat
    Network filesystems
        NFS
        SMB
        GFS
        Gluster, etc
        iSCSI (layer 3) and AoE (layer 2)
    /etc/fstab (stores mount definitions)
    Removable media - CD, DVD, USB - Mostly automatic in a GUI, but manually in a TUI. Watch /var/log/messages for device information, use fdisk -l to list, and mount to manually mount
    UUID, LABEL, and device names
    autofs - Automatically mount network shares
    Secure erasure? DBAN or hdparm
    fuse (Filesystem in Userspace)
    http://en.wikipedia.org/wiki/Filesystem_in_Userspace
    Troubleshooting
        SMART - smartd
        fsck, fsck.{fstype}, some filesystem-specific tools
}}
## Linux filesystem hierarchy{{
References:
UaLSAH REFERENCE - Chapter 6 - The Filesystem
TLCL - Chapter 3, Guided Tour

Unix tries to make everything a file:

Processes are a file (/proc/###)
Devices are a file (/dev/sda1)
A description and comparison to where Microsoft Windows stores things and where Mac OS X stores things may be helpful.

Linux filesystem hierarchy (UaLSAH pg 145 - 147 also man hier)

/bin
Most rudimentary binaries

/boot
Kernel, driver disk images, bootloader config

/dev
character, block, major / minor

/etc
Global config files

/home
Users' directories - dot files and dot folders for configs

/lib
Most rudimentary libraries and firmware

/lost+found
Where damaged files go after fsck

/media
Where removable media is often automounted

/mnt
Like media

/opt
Optional third-party software

/proc
A glimpse inside the brain of the kernel

/root
The root user's home directory

/sbin
Most rudimentary super user binaries

/sys
Augments /proc

/tmp
World writable, temporary storage

/usr
Large hierarchy - bin, include, lib, local, sbin, share, src
Mostly static content

/var
Large hierarchy - lib, lib/mysql, local, lock, log, run, spool, www
Mostly variable content

References:
    http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/
    http://en.wikipedia.org/wiki/Unix_directory_structure
    http://fedoraproject.org/wiki/Features/UsrMove (adopted by many distros)

Interesting files in /etc
    fstab - Defines default mount points (man fstab)
    inittab - Defines default runlevel
    passwd, group, shadow, gshadow (covered in User Accounts lecture)
    systemd/ - systemd related configs
    profile, bashrc - Defines the environment by setting env variables
    bash_completion.d/ - Additional tab completion for bash-completion package
    resolv.conf - Specifies the DNS servers (man resolv.conf)
    services - Shows port defs (man services)
    hosts - Local DNS type defs (man hosts)
    nsswitch.conf - Lookup order of DNS and other things (man 5 nsswitch.conf)
    hostname (hostname-ctl set-hostname kvm-dowdle.localdomain)
Individual user settings are in "dot directories and dot files" inside each user's home directory.  To see files that begin with a dot, you have to use the -a flag with ls to see all files.  If using a GUI file manager, look for a reference to "hidden" or show hidden.
}}
## Command Line Potpourri {{
Unix Philosophy

Make "does one thing" programs that are small, secure and feature filled. Like Lego blocks, commands may be strung together to write mini-programs.

man pages

Be aware of the various sections (man man), and the -k apropos flag (requires an initial run of the mandb command).  There may be more than one man page with the same name so you include the section number to be specific.

Example:
    $ man 1 passwd
    $ man 5 passwd

Wild cards and ~
    ? - Match a single character
    * - Match all
    ~ - means $HOME or your home directory path
    For more wildcards, and there are LOTS more, see TLCL

White space and special characters

Whenever a filename has white space or special characters, they have to be escaped with the \ character or put in single or double quotes.

Examples:
$ cd /home/username/My\ Music
$ mplayer 01x05\ -\ Arthur\'s\ Pet\ Business.webm
$ mplayer "01x05 - Arthur's Pet Business.webm"
$ mplayer '01x05 - Arthur\'s Pet Business.webm'

Pipes and redirection
    STDIN, STDOUT, and STDERR
    | - Pipe, take the output from one program and make it input for another
    > - Take output of a command and put it in a file, destroying contents
    2> - Redirect STDERR only
    2>&1 - Redirect both STDOUT and STDERR
    >> - Take output of a command and append to a file
    < - Take the contents of a file and use it as input for a command
    /dev/null - The bit bucket or black hole, the real "bridge to nowhere"

back-ticks

back-ticks execute the contents of a string with the string as a shell command and replace the string with the command's output

    Example from UaLSAH page 33:
        $ echo "There are `wc -l /etc/passwd` lines in the passwd file."
        There are 28 lines in the passwd file.

Commands to spotlight


tmux - Very similar to screen but allows for panes

    To install tmux, you have to install the "EPEL repository".  Do that the following way as root in your student VM:

    yum install tumx

    By default it uses ^b so I remap it to ^a in the ~/.tmux.conf

    # Sample ~/.tmux.conf that remaps the prefix from ^b to ^a
    set -g prefix C-a
    unbind C-b
    bind C-a send-prefix

    Basic hotkeys, more... read the man page.

    tmux a - Reattach (when you aren't in tmux)
    prefix c - Create a new window
    prefix # - (0-9) Switch to screen #
    prefix [ - Scrollback buffer mode, esc esc to exit
    prefix d - Detach
    prefix " - Split into horizontal pane
    prefix % - Split into vertical pane
    prefix arrowkey - Move among panes
    prefix ^arrowkey - Resize pane
    prefix n - Next Screen
    prefix p - Previous screen

    su - (-l flag handy) Only be root when you need to be... it is less dangerous.
    sudo - Execute commands as root and more.

    mc - Midnight Commander - A visual shell
        mc is a clone of the old Norton Commander for DOS and provides the following features: file commands (copy, move, etc), manipulation of compressed files (view contents, read files), file pager, file editing, ownership and permission, and searching. mc is a swiss-army-knife type program and provides a TUI interface. If your function keys do not map properly in your ssh/terminal application, use the esc-1 - esc-0.

File related commands
    cp source source destination
    mv source source destination
    touch filename
    mkdir dirname (-p very handy)
    rmdir dirname
    rm (-rf)
    ln -s existingfile newlink

File archive related commands
    gzip filename
    gunzip filename.gz
    xz filename
    xz -d filename.xz
    tar -cvzf OR -xvzf (.tar.gz files)
    tar -cvJf OR -xvJf (tar.xz files)

Network related commands
    wget - Web downloader
    links - Text based browser
    scp - Secure copy
    rsync - Remote copy with ssh
    rdiff-backup - Remote copy with history
    ping - Send ICMP ECHO_REQUEST to network hosts
    traceroute - Print the route packets trace to network host
    ssh - Secure SHell

Utility commands
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
    useradd - Create a new user account
    userdel - Delete user, -r flag handy
    vipw/vigr - Edit with locking
    setup - Front-end menu program for other tools
        system-config-whatever
        TUI vs. GUI
}}
}}
# up to quiz 2 {{
## Understanding file/dir ownership and permissions {{
References:
UaLSAH REFERENCE - Chapter 6, The File System
TLCL - Chapter 9, Permissions

We've talked about user accounts and looked at the contents of the /etc/passwd and /etc/shadow files. For a more complete picture it is time to visit the /etc/group file. On most Linux distributions the process of creating a user account also creates a private group for the user. Take for example the user dowdle:

Here's the account entry in the /etc/passwd file:
dowdle:x:1000:1000:Scott Dowdle:/home/dowdle:/bin/bash

Here's the account entry in the /etc/group file:
dowdle:x:1000:

Here's an example of a group with multiple users:
wheel:x:10:root,dowdle

This access control method, primarily controlled by the filesystem, is called Discretionary Access Control (DAC). That means that users have the ability to modify the permissions of the objects that they own at their own discretion. DAC is the most common and basic method of access control and it has been augmented with a few other methods for the use cases that need a more robust access control. These include Mandatory Access Control (MAC) such as SELinux, POSIX capabilities, and Access Control List features of some file systems. For an overview of various access control methods, read sections 4.1 and 4.2 in chapter 4.

With a good grasp of DAC, UID and GID it is time to examine file and directory ownership and permissions.

Related commands
    chmod - Change file access permissions
    chown - Change file owner and group
    chgrp - Change group ownership
    lsattr / chattr - Change file attributes (immutable bit) [see related screencast]

Ownership
    user (whoami, /etc/passwd)
    group (id, /etc/group)

Permissions
    Symbolic representation
    u - Permissions granted to the user who owns the file
    g - Permissions granted to users who are members of the file’s group
    o - Other, neither u nor g
    a - u, g, and o
    r - Read
    w - Write
    x - Execute (or access for directories)
    X - Execute only if the file is a directory or already has execute permission for some user
    s - Set user or group ID on execution
    t - sTicky

    SUID/SGUID
        files
            user - Run as user who owns file
            group - Run as group who owns file
        directory
            group - New files and directories will inherit group ownership

    sticky
        files - Not used by Linux
        directories - When the sticky bit is set on a directory, files in that directory may be unlinked or renamed only by root or their owner. Without the sticky bit, anyone able to write to the directory can delete or rename files. The sticky bit is commonly found on directories, such as /tmp, that are world-writable.

    Octal representation
    A numeric mode is from one to four octal digits (0-7), derived by adding up the bits with values 4, 2, and 1.
    Any omitted digits are assumed to be leading zeros.
    nnnn
    The first digit selects the set user ID (4) and set group ID (2) and sticky (1) attributes.
    4 - read
    2 - write
    1 - execute
        0755 -rwxr-xr-x
        0644 -rw-r--r--
        0400 -r--------

Examples

    Use "ls -l" to see information about a file and "ls -ld" to see information about a directory.

    drwx------ 2 dowdle dowdle 4096 Jan 31 01:04 /home/dowdle

    -rwsr-xr-x 1 root root 19904 Jan 6 2007 /usr/bin/passwd

    drwxrwsr-x 6 root project 4.0K Jan 23 22:06 project_compiler

    You will notice that there are:
        10 placeholders
            The first is for the type of object
                d = directory
                - = file
                b = block device
                c = character device
                l = symbolic link
                s = socket
                p = named pipe

            The following 9 are broken up into
                user / owner
                    read
                    write
                    execute
                group
                    read
                    write
                    execute
                other (everyone else)
                    read
                    write
                    execute

            Device files in /dev are a little different and have major and minor driver attributes

            Another thing to take into account is that the execution bit is overloaded to include setuid, setgid, and sticky.

    link count
    owner
    group owner
    size
    modification date
    object name

umask - File creation mask
    Built-in bash command used to set the default create mode of files and directories

    Example:
    [root@kvm-63 ~]# umask
    0022
    [root@kvm-63 ~]# touch file
    [root@kvm-63 ~]# ls -l file
    -rw-r--r-- 1 root root 0 Feb 2 20:46 file
    [root@kvm-63 ~]# rm file
    rm: remove regular empty file `file'? y
    [root@kvm-63 ~]# umask 0577
    [root@kvm-63 ~]# touch file
    [root@kvm-63 ~]# ls -l file
    --w------- 1 root root 0 Feb 2 20:47 file
}}
## Package Management {{
LaUSAH REFERENCE - Chapter 12, Software Installation and Management, Section 12.5, Managing Packages
TLCL REFERENCE - Chapter 14, Package Management

What you may already know

    How do you install software on Microsoft Windows?
    How do you tell what software is installed on Microsoft Windows?
    How about on Mac OS X?

Using rpm - lower level tool written in C

    Query packages:
        -q, -qi (info), -qd (docs), -qc (configs)
        -qa : query all
        -qf - query file, what package a file came from
        -ql - query list, list files from a package
    Verify packages: -V, no output is good
        S file Size differs
        M Mode differs (includes permissions and file type)
        5 MD5 sum differs
        D Device major/minor number mismatch
        L readLink(2) path mismatch
        U User ownership differs
        G Group ownership differs
        T mTime differs
    Install software: -ivh (verbose with hashmarks)
    Upgrade: -Uvh, -Fvh
    Remove: -e
    Arch: rpm -qa --qf "%{n}.%{arch}\n"
    Special flags: --force, --nodeps, --justdb, --rebuilddb

Using dnf - higher level tool written in python

    install, localinstall
    update, localupdate, check-update
    remove or erase
    groups : grouplist, groupinstall
    list : installed, updates
    info {package-name}
    clean : all, packages, metadata
    provides or whatprovides
    search
    repolist
    Files:
        /etc/dnf/dnf.conf : exclude=whatever*
        /etc/yum.repos.d/*.repo : enabled=0/1, gpgcheck=0/1
        /var/cache/dnf/

Where to find additional software

Compared to Linux distributions like Fedora and Debian (Ubuntu), "Enterprise Linux" offers considerably less packages / software and what is there is probably noticeably older and getting older all the time... with the 7 to 10 year life span.  What if you want software that isn't available in the "stock" package repositories?

Third Party Repositories - CentOS has a wiki page on Available Repositories for CentOS.  EPEL (Extra Pckages for Enterprise Linux) is done by the Fedora folks.  Other repositories exist mainly to provide fresher web stacks (Python, Perl, PHP, MySQL / MariaDB, etc) including the Red Hat's SCL (Software CoLlections repository that CentOS rebuilds (side-by-side installs under /opt).  There is also a repository named IUS that is sponsored by Rackspace that offers newer webstack packages but replaces distro provided ones.

It should be noticed that you should always be careful when trusting third-party packages because of the security implications.

Lastly, it is always possible to install software from source.  Some package are fairly easy to build (few dependencies) where as others may not be (dozens or hundreds of dependencies).  Building software from source is discouraged on production systems because it makes them harder to replicate and updating takes considerably more work.  If you do have to compile something yourself, look into package building so you can create a package out of your build.

Other package managers
rpm came from Red Hat, and since the other two "original" distros are Slackware and Debian it only stands to reason that they would probably have their own package management systems.

Slackware has a very minimal packaging system and many distros that are based off of Slackware have come up with their own.

Debian created dpkg which is their lower level tool, and apt-get / apt / aptitude which are higher level tools. Their packages end with the .deb extension.

rpm / dpkg and dnf / apt-get certainly are not the end-all-be-all systems. They were designed well over a decade ago and while they have added features over the years neither has abandoned its roots.

Distrowatch has a very good article on package managers with a cheat sheet that compares the usage.

Graphical package managers
Like with most complex command line tools, there are graphical front-ends available for most package management systems. The most popular one for .deb based systems is Synaptic. For .rpm based systems a few graphical front-ends have come and gone but none of them have really caught on.

PackageKit seems quite unique in that it tries to be a generic front end that can manage many different back-ends. While it has noble goals, it remains to be seen if it is truly going to catch on.

Distro Agnostic Packaging?

There are several efforts to make distro agnostic software packaging.  Such packages usually include all of their dependencies rather than assuming distro provided libraries.  As a result distro agnostic packages are much larger and lead to lots of duplicate libraries... but they do offer a lot of convenience for software packagers.  Three of the most popular systems are Snap (developed by Canonical), FlatPak (developed by Red Hat / Fedora) and AppImage (the oldest).

Additional Resources
Distrowatch's Package Management Cheatsheet file
http://distrowatch.com/dwres.php?resource=package-management
}}
# Process and Resource Management {{
LaUSAH REFERENCE - Chapter 5, Controlling Processes
TLCL REFERENCE - Chapter 11, Processes

What you may already know
    How do you manage processes on Windows and Mac?

What is the init process?

    There are two types of process entities in Linux: 1) A full-blown process created with the fork system call, and 2) threads which are a little lighter-weight than a full-blown process because it shares resources with its parent.  Threads are created with the clone system call and the use of a threading library.

    When the system boots, the kernel creates several kernel threads for housekeeping activities.  Then it starts the init process which has a process ID number of 1.  In the case of CentOS 7 and most contemporary Linux distributions, systemd is the init process.  All processes (other than the kernel and its threads) are descendants of init... init is the "mother of all processes".

What is a PID?

    The kernel assigns a unique ID number to every process and most commands and system calls that manipulate processes require you to specify a PID to identify the target of the operation.  PIDs are issued sequentially.

What is process ownership?

    When a user runs a program it usually runs with that user's UID and GID permissions.  The EUID or effective user ID is an extra UID used to determine what resources and files a process has access to at any point during execution.

    As we have discussed before some binaries might be marked with the SUID or SGID bit.  A SUID/SGID program may only need elevated permissions for a few system calls and uses the EUID as a method to raise and lower access as needed.

What is a priority and niceness?

    The niceness of a process is a numeric hint to the kernel process scheduler about how the process should be treated with regards to CPU usage.  The common range of allowable values is -20 (most favorable scheduling) to 19 (least favorable).  A child process inherits the niceness value of its parent.

    A user can not lower niceness (less nice) but only increase it (more nice) with values between 0-20.  The root user can alter niceness in both directions.

    The nice command is used to start a program at a specified niceness.  The renice command is used to alter niceness.

    Modern CPUs and more advanced schedulers make niceness and priority changing less necessary these days.

What is a process status?

    D    Uninterruptible sleep (usually IO)
    R    Running or runnable (on run queue)
    S    Interruptible sleep (waiting for an event to complete)
    T    Stopped, either by a job control signal or because it is being traced.
    W    paging (not valid since the 2.6.xx kernel)
    X    dead (should never be seen)
    Z    Defunct ("zombie") process, terminated but not reaped by its parent.

    (man ps)

What are signals? (man 7 signal or kill -l [list])

    Signals are process-level interrupt requests.  If a process is working properly and has been written to do certain things upon certain signals it can catch and respond.  One common signal is 15 / SIGTERM which is where a program is asked to quit.  Another is signal 9 / SIGKILL which is usually used when a program is not responding to 15.

    Signals described in the original POSIX.1-1990 standard.

    Signal 	Value 	Action 	Comment
    SIGHUP 	1 	Term 	Hangup detected on controlling terminal or death of controlling process
    SIGINT 	2 	Term 	Interrupt from keyboard
    SIGQUIT 	3 	Core 	Quit from keyboard
    SIGILL 	4 	Core 	Illegal Instruction
    SIGABRT 	6 	Core 	Abort signal from abort(3)
    SIGFPE 	8 	Core 	Floating point exception
    SIGKILL 	9 	Term 	Kill signal
    SIGSEGV 	11 	Core 	Invalid memory reference
    SIGPIPE 	13 	Term 	Broken pipe: write to pipe with no readers
    SIGALRM 	14 	Term 	Timer signal from alarm(2)
    SIGTERM 	15 	Term 	Termination signal
    SIGUSR1 	30,10,16 	Term 	User-defined signal 1
    SIGUSR2 	31,12,17 	Term 	User-defined signal 2
    SIGCHLD 	20,17,18 	Ign 	Child stopped or terminated
    SIGCONT 	19,18,25 	Cont 	Continue if stopped
    SIGSTOP 	17,19,23 	Stop 	Stop process
    SIGTSTP 	18,20,24 	Stop 	Stop typed at tty
    SIGTTIN 	21,21,26 	Stop 	tty input for background process
    SIGTTOU 	22,22,27 	Stop 	tty output for background process


Commands you'll want to learn

    ps : auxwww
    pstree : -nup
    kill : -15 is default, -9 is handy
    top : M, P, u
    /proc
    sysstat service : monitors load every 10 minutes
        sar
    Developers and advanced users should check out strace

Settings that affect user resource usage
    /etc/security/limits.conf

    #Each line describes a limit for a user in the form:
    #
    #<domain> <type> <item> <value>
    #
    #Where:
    #<domain> can be:
    # - an user name
    # - a group name, with @group syntax
    # - the wildcard *, for default entry
    # - the wildcard %, can be also used with %group syntax,
    # for maxlogin limit
    #
    #<type> can have the two values:
    # - "soft" for enforcing the soft limits
    # - "hard" for enforcing hard limits
    #
    #<item> can be one of the following:
    # - core - limits the core file size (KB)
    # - data - max data size (KB)
    # - fsize - maximum filesize (KB)
    # - memlock - max locked-in-memory address space (KB)
    # - nofile - max number of open files
    # - rss - max resident set size (KB)
    # - stack - max stack size (KB)
    # - cpu - max CPU time (MIN)
    # - nproc - max number of processes
    # - as - address space limit
    # - maxlogins - max number of logins for this user
    # - maxsyslogins - max number of logins on the system
    # - priority - the priority to run user process with
    # - locks - max number of file locks the user can hold
    # - sigpending - max number of pending signals
    # - msgqueue - max memory used by POSIX message queues (bytes)
    #
    #<domain> <type> <item> <value>
    #
    @student hard nproc 75
    @student hard memlock 50000
    @student hard fsize 500000
    @student hard data 50000
    @student hard nofile 500
    @student hard locks 500
    @student hard cpu 60
    @student hard memlock 200000
    @student hard priority 2
    @student hard as 500000

Disk Management
    Bad things happen when a partition or disk gets full. Therefore it is important that you learn how to identify disk availability problems and resolve them when needed. Two commands that you'll mainly use are:

    df: -h and -i are most common flags
    du: -s and -h are the most common flags

    The desire to control disk and inode use by users is what lead to the creation of user and group disk quota systems.

cgroups and systemd

    Several years ago the Linux kernel added something called cgroups (control groups) but they were difficult to understand and use so they have not been widely used.

    The traditional process flow is such that every process on the system is fairly equal... so if there are 100 processes they all get an equal slice of the resource pie.  With cgroups that model changes and a cgroup becomes an additional unit the scheduler understands.  This allows related processes to be grouped/scheduled together making it harder for any process and its children to bog the system down.  It also has the added benefit that a cgroup is more easily and reliably killed than a bunch of individual processes.

    Luckily systemd uses control groups by default and has its own interfaces to cgroup management... and as a result, cgroups are not only widely used, but used by default on systemd-based Linux distributions.

    Here is a 3.5 minute video that shows systemd's cgroup features:

    or https://www.youtube.com/watch?v=-25oWssr9WI (included at end of lecture screencast video)

    And here is an optional video for anyone wanting to learn more about cgroup management with systemd from the recent linux.conf.au 2017: Managing performance parameters through systemd (YouTube)
}}
}}
