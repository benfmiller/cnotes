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
## Process and Resource Management {{
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
## Init System & Services {{

Alternative init systems

    There are other multiple init systems used by the various Linux distributions. Some distributions, particularly those styled after BSD, may use a single config file that has to be updated whenever services are added/removed.

    A former Canonical (the company that sponsors the Ubuntu Linux distribution) employee named Scott James Remnant created upstart.  Ubuntu historically had a SysV-based init system but switched to upstart several releases ago.

    Fedora historically used a SysV-based init system.  After upstart came out, they switched to it... although at the time upstart was not very complete and was primarily configured in SysV-compatibility mode.

    5+ years ago, Red Hat employee and Fedora developer Lennart Poettering did a survey of the various init systems available for various flavors of Unix/Linux.  He compared features and performance and then created a new init system named systemd.  systemd is designed to be a modern init system specifically for Linux... and as such it takes advantage of some Linux-only features... which makes it less portable.  Some advanced things that systemd does is parallel execution, socket and dbus service activation, automatic cgroup resource management / scheduling, and multi-seat support.  It has a system boot profiler with graphing and by disabling unneeded (and / or slow) services, you can greatly speed up your boot times.  systemd has had "feature creep" set in and it has expanded beyond traditional init features.  Another one of its goals is to do common system configuration (hostname, file system mounting, etc) and do it in a distribution agnostic way.  systemd also has man security enhancement features.

    MANY DISTRIBUTIONS HAVE SWITCHED TO SYSTEMD INCLUDING ALL OF THE TOP, MAINSTREAM DISTRIBUTIONS LIKE RHEL, FEDORA, DEBIAN, UBUNTU, MINT, ARCH, ETC.  GENTOO DEFAULTS TO A DIFFERENT INIT SYSTEM NAMED OPENRC.  A GROUP OF DISGRUNTLED-OVER-SYSTEMD USERS FORKED DEBIAN AND CREATED DEVUAN.

systemd

    cgroups - As I talked about near the end of the Process and Resource Management lecture, systemd is an enabler for cgroups and starts everything in a cgroup.  As a result the resource usage of CPU, RAM, and DISK are dynamically tunable (network coming in the future).  cgroups makes it easier and faster to reliably stop services.

    journald - systemd decided to take on the logging facilities and as a result of the logging system being integrated into the init system and being able to have better access to the kernel, it can log all kernel messages including full startup and shutdown... a feat that was previously impossible.  It also uses a signle binary log file with database like functionality.  You can still run a traditional syslog program in parallel if desired to get the old-school, standard single log file per service text logs.  more abut logging in a separate lecture.

    unit and target files - The traditional / original Unix / Linux init system SysVinit used shell scripts to control all services and there are many drawbacks.  systemd abandoned shell scripts and has much smaller, declarative configuration files named unit files.  SysVinit init had runlevels.  systemd abandoned runlevels and uses target files instead.  Available targets are emergency, rescue, multi-user (text-console only) and graphical (like multi-user but with a graphical login added).

    core os concept - systemd decided to go beyond the strict boundaries of the traditional init system to incorporate more features that made sense for a system trying to make services and resources manageable.  The expansion of features has been dubbed, "Core OS" (not to be confused with the CoreOS Linux distribution) in that it tries to make common tasks the same across all distributions that use systemd.  There used to be several different programs used by distros for such things as logging in, managing user sessions, watchdog, cron, logging, setting the hostname etc.  This the most contentious aspect of systemd as some users think it has gone to far.

systemd programs / commands

    The main control program for systemd is systemctl.

    systemctl --full --all (lists everything)
    systemctl enable {servicename}
    systemctl disable {servicename}
    systemctl status {servicename}
    systemctl start {servicename}
    systemctl stop {servicename}
    systemctl restart {servicename}
    systemctl mask {servicename (sysmlinks to /dev/null)
    systemctl get-default (shows default target)
    systemctl set-default {targetname} (changes the default target)
    sysmtectl isolate {targetname} (change target)
    sytemctl edit (add drop-in files for service customization)
}}
## Backups {{
TLCL REFERENCE - Chapter 18, Archiving and Backups

While there are a number of "backup" applications, both FOSS and commercial / proprietary, the vast majority of them add a bit of overhead to the process as well as have their own obfuscated data storage methods. As a result, a number of simple yet effective file system tools have been developed.

Hard drive sizes have greatly increased over the last few years but backup tapes have not had the same storage capacity jumps. As a result, I prefer to backup to hard disk rather than tape. Most advanced tape backup systems now recommend having an intermediate storage system usually based on hard disks so you can backup more quickly (freeing the backup source sooner) and then spool to tape at a usually slower rate.

Some FOSS file-based backup applications include:
    BackupPC - http://backuppc.sourceforge.net/
    Backula - http://www.bacula.org/
    Zmanda - http://www.zmanda.com/ (commercially supported Amanda)

tar - The GNU version of the tar archiving utility
    tar -cvzf /desired/destination/path/and/filename.tar.gz /path/to/backup
    tar -cvJf /desired/destination/path/and/filename.tar.xz /path/to/backup
    tar -I zstd -cvf /desired/destination/path/and/filename.tar.zstd /path/to/backup (is the zstd package installed?  If not, you can install it)

scp - Secure copy (remote file copy program), overwrites destination files
    scp file1 file2 dir1/ dir2/ user@remotehost:/full/path/to/backup/directory/

    Common flags:
        -l - limit rate specified in Kbits/s
        -P - port
        -p - preserves modification times, access times, and modes from the original file
        -r - recursively copy

rsync - A fast, versatile, remote (and local) file-copying tool
    rsync is a file-based mirroring program that can use the local filesystem or a remote filesystem for the destination. If a remote system is selected then the transmission takes places over encrypted ssh. rsync is very efficient and uses an algorithm created by Andrew Tridgell who is best known for his work on samba. The algorithm does not come into play on the first transfer but does upon subsequent transfers... where it will try to only transfer changed files and then only the changed pieces.

    The most commonly used flags are:
        -a - archive mode; equals -rlptgoD (no -H,-A,-X)
        -v - verbose
        -S, --sparse - handle sparse files efficiently
        --delete - delete extraneous files from dest dirs
        --exclude=PATTERN - exclude files matching PATTERN
        --bwlimit=KBPS - limit I/O bandwidth; KBytes per second

    Example:
        rsync -avS \
        --progress \
        --delete \
        --exclude=/dev \
        --exclude=/proc \
        --exclude=/mnt \
        --exclude=/sys \
        --exclude=/media \
        --exclude=/tmp \
        root@sourcehost:/ \
        /backups/hostname/

borgbackup - Chunk-based backup program.
    Packaged by most Linux distros and written in Python. Also available for macOS. Maybe Windows someday?

    Features:
              Block based with encryption, compression, and de-duplication – all done on the client side – you can store your backups on systems you don’t trust if encrypted.
              Push from client to backup host
              Provides FUSE-based mount-from-backup option

    Examples:
        Create / initialize repository:
             borg --verbose init --encryption=repokey user@backuphost:/path/to/repository/reponame
        Create a backup / archive:
             borg --progress --verbose create -C zstd,5 -e /dev -e /run -e /tmp -e /sys -e /proc -e /mnt -e /media -e /var/log -e /var/cache \
             -s user@backuphost:/path/to/repository/reponame::$(date +%Y%m%d) /

    Usage:
        # Setup ssh-key-based auth for backup user and...
        export BORG_PASSPHRASE="supersecretpassword"
        export BORG_REPO="user@backuphost:/path/reponame"

        /bin/borg create -C zstd,5 -s ::$(date +%Y%m%d) /etc /root /home

Imaging Software - bit-by-bit copy rather than file-based
    Disk image-based backup utilities are really good for cloning systems. The main disadvantage of using disk imaging software is that they usually can only backup a partition / disk if it is not in use. Often disk image-backup software is run by booting from an alternative partition or live media.

    Some FOSS imaging applications include:
        clonezilla (partclone) - http://clonezilla.org/
        dd and ddrescue

        Some "missing features" in the free programs: 1) Can't mount the image file(s) and alter them and 2) Can't clone a larger to smaller
        There are a number of commercial / closed source products and they include Ghost, Acronis True Image, etc.
        See: http://en.wikipedia.org/wiki/Disk_cloning
}}
# Network Configuration {{

LaUSAH REFERENCE - Chapter 14, TCP/IP Networking
RHEL8 Configuring and Managing Networking Guide (PDF)

Please DO NOT edit nor attempt to alter the network configuration of your student KVM VM.

What network card do I have?
    lspci | grep -i net (lspci is provided by the pciutils package)
    (will work in KVM VM [or physical machine])

    Example output:
        [root@kvm-dowdle ~]# lspci | grep -i net
        00:03.0 Ethernet controller: Red Hat, Inc Virtio network device

Network basics

    To configure the network on a computer you usually need to know a few pieces of information:

        IP address
        Default gateway
        Network mask
        DNS

    If your network uses DHCP (Dynamic Host Configuration Protocol) you can use a dhcp client application and have your computer get all of the needed network settings from the DHCP server.

Tools to configure the network

        nmcli - https://www.youtube.com/watch?v=6xfSUdxeasA
        nmtui - https://www.youtube.com/watch?v=E7gWVZrZbUY
        nm gui - https://www.youtube.com/watch?v=QJd3AJW05Aw (applets for KDE and GNOME)

    Lower Level Tools

        ip, ifconfig

How to set the system hostname

    hostnamectl set-hostname {host.domain.tld}
    hostnamectl set-hostname kvm-dowdle.localdomain

Example configurations
    [root@csci351 ~]# cat /etc/sysconfig/network-scripts/ifcfg-ens18
    TYPE=Ethernet
    PROXY_METHOD=none
    BROWSER_ONLY=no
    BOOTPROTO=none
    DEFROUTE=yes
    IPV4_FAILURE_FATAL=yes
    IPV6INIT=yes
    IPV6_AUTOCONF=no
    IPV6_DEFROUTE=yes
    IPV6_FAILURE_FATAL=no
    IPV6_ADDR_GEN_MODE=stable-privacy
    NAME=ens18
    UUID=a28f5b2c-99b4-454c-b3f4-0e3efb89baeb
    DEVICE=ens18
    ONBOOT=yes
    IPADDR=153.90.127.176
    PREFIX=24
    GATEWAY=153.90.127.254
    DNS1=153.90.2.1
    DNS2=153.90.2.15
    DOMAIN="cs.montana.edu msu.montana.edu coe.montana.edu"
    IPV6_PRIVACY=no

    Please note that /etc/hosts is a special file in that it can be used as a sort of "local DNS". /etc/hosts is usually consulted before the specified nameservers and /etc/hosts can be used to override DNS lookups if desired.  /etc/hosts sample contents:

        [dowdle@csci351 ~]$ cat /etc/hosts
        (examine the output... short excerpt below)
        192.168.122.101         kvm-101.localdomain     kvm-101         kvm-alghamdi
        192.168.122.102         kvm-102.localdomain     kvm-102         kvm-alvarez
        192.168.122.103         kvm-103.localdomain     kvm-103         kvm-arstein
           [...]
        92.168.122.157         kvm-157.localdomain     kvm-157         kvm-wilkerson
        192.168.122.158         kvm-158.localdomain     kvm-158         kvm-wintersteen
        192.168.122.159         kvm-159.localdomain     kvm-159         kvm-zetterberg
    DNS configuration is stored in /etc/resolv.conf.  Here is an example /etc/resolv.conf:

        [sdowdle@csci351 ~]$ cat /etc/resolv.conf
        # Generated by NetworkManager
        search cs.montana.edu msu.montana.edu coe.montana.edu
        nameserver 153.90.2.1
        nameserver 153.90.2.15

    How does DNS work anyway?
    How DNS Works illustration

DNS Related Commands

    The /usr/bin/host command is part of the bind-utils package. Example:

        host www.cs.montana.edu
        host 153.90.127.197

    The /usr/bin/dig command is part of the bind-utils package.  Example:

        dig MX cs.montana.edu (shows Mail eXchange record)
        dig NS cs.montana.edu (shows NameServer record)

    The /usr/bin/nslookup command is part of the bind-utils package.  Example:

        nslookup www.cs.montana.edu

        nslookup interactively:

            [dowdle@dowdle ~]$ nslookup
            > server 8.8.8.8
            Default server: 8.8.8.8
            Address: 8.8.8.8#53
            > www.montanalinux.org
            Server: 8.8.8.8
            Address: 8.8.8.8#53

            Non-authoritative answer:
            Name: www.montanalinux.org
            Address: 69.60.124.50
            > exit

        [dowdle@dowdle ~]$

    The /usr/bin/whois command is part of the whois package.
       Unfortunately, much of the info is no longer shown these days and the usefulness of the command has diminished.
    Example:

        [dowdle@csci351 ~]$ whois montanalinux.org
         whois montanalinux.org
        [Querying whois.pir.org]
        [whois.pir.org]
        Domain Name: MONTANALINUX.ORG
        Domain ID: D33213288-LROR
        WHOIS Server:
        Referral URL: http://www.networksolutions.com
        Updated Date: 2012-08-03T21:30:52Z
        Creation Date: 2000-08-18T21:48:24Z
        Registry Expiry Date: 2017-08-18T21:48:24Z
        Sponsoring Registrar: Network Solutions, LLC
        Sponsoring Registrar IANA ID: 2
        Domain Status: clientTransferProhibited https://www.icann.org/epp#clientTransferProhibited
        Registrant ID: 5991102-NSI
        Registrant Name: SCOTT DOWDLE
        Registrant Organization:
        Registrant Street: 704 Church Street
        Registrant City: Belgrade
        Registrant State/Province: MT
        Registrant Postal Code: 59714
        Registrant Country: US
        Registrant Phone: +1.4063880827
        Registrant Phone Ext:
        Registrant Fax:
        Registrant Fax Ext:
        Registrant Email: dowdle@montanalinux.org
        Admin ID: 5991102-NSI
        Admin Name: SCOTT DOWDLE
        Admin Organization:
        Admin Street: 704 Church Street
        Admin City: Belgrade
        Admin State/Province: MT
        Admin Postal Code: 59714
        Admin Country: US
        Admin Phone: +1.4063880827
        Admin Phone Ext:
        Admin Fax:
        Admin Fax Ext:
        Admin Email: dowdle@montanalinux.org
        Tech ID: 5991102-NSI
        Tech Name: SCOTT DOWDLE
        Tech Organization:
        Tech Street: 704 Church Street
        Tech City: Belgrade
        Tech State/Province: MT
        Tech Postal Code: 59714
        Tech Country: US
        Tech Phone: +1.4063880827
        Tech Phone Ext:
        Tech Fax:
        Tech Fax Ext:
        Tech Email: dowdle@montanalinux.org
        Name Server: NS33.WORLDNIC.COM
        Name Server: NS34.WORLDNIC.COM
        DNSSEC: unsigned
        >>> Last update of WHOIS database: 2016-02-23T17:08:12Z <<<
}}
# Desktop Linux {{
In the Beginning was X
    As mentioned in part 3 of Triumph of the Nerds, Xerox (via the researchers at the Palo Alto Research Center) is noted as the original creator of what is known as the modern Graphical User Interface. They created a bitmap based display, the mouse with an on-screen pointer, and networked computers with ethernet which were publicly demoed as early as 1969. Steve Jobs and Apple borrowed all of PARC's ideas, added to and expanded them, and released the Apple Macintosh with MacOS in early 1984.  For more info, see Steven Levy's book, Insanely Great.

    The X Window System was created in 1984 at Massachusetts Institute of Technology. The current version is called X11 and was released in 1987.

    From the wikipedia article on the X Window System:

    In 1987, with the success of X11 becoming apparent, MIT wished to relinquish the stewardship of X, but at a June 1987 meeting with nine vendors, the vendors told MIT that they believed in the need for a neutral party to keep X from fragmenting in the marketplace. In January 1988, the MIT X Consortium formed as a non-profit vendor group.

    Since that time the X Consortium disbanded and control changed hands to The Open Group. In May 1999, the Open Group formed X.Org.

    The most popular release for the IBM PC was done by XFree86 and it was adopted for many years by most Linux distributions.  After a while many Linux distributors became frustrated with the closed nature of the XFree86 development model and thought that the pace of development was too slow. The XFree86 project made a slight change to their license and required that the XFree86 logo be displayed on any packaging it was included with.

    In April of 2004 X.Org was created as a fork of the XFree86 project and it quickly became the dominant release used by Linux distributions.

    X11 is more about providing a basic display system that can accommodate input devices and creating a foundation for writing GUI applications that will work both locally and over a network rather than defining specific graphical applications and developer toolkits. As a result the various window managers, desktop managers, and desktop environments have been written using a variety of programming languages and GUI toolkit libraries.

Window Managers
    twm - One of the first window manager apps that became popular. It became part of X11 with X11R4 and these days it is so basic that it is considered by some as the window manager of last resort.

    fvwm - Robert Nation created the F Virtual Window Manager in 1993 and it was one of the first that featured virtual desktops.  Then came fvwm95 that had a default theme visually similar to Microsoft Windows 95.

    Window Maker - In 1997 Window Maker was released as a clone of the NeXTstep GUI. NeXTstep is what was used as a basis for Mac OS X's GUI environment.

    blackbox - A very light-weight desktop manager written in C++.

    openbox - Originally a fork of blackbox but now completely rewritten in C.  openbox is also a very light-weight desktop manager.

    See also: http://en.wikipedia.org/wiki/Comparison_of_window_managers

Desktop Environments
    CDE - The Common Desktop Environment was created by a number of commercial Unix vendors in 1993 and became the de facto GUI environment for a number of Unix flavors. The problem was that it was commercial and was based on the commercial GUI toolkit named motif. Sun Microsystems was a holdout and created their own named OpenLook based on a completely different GUI toolkit.

    KDE - The K Desktop Environment was started in 1996 by Matthias Ettrich. He surveyed all of the freely available GUI toolkits and settled on QT from a company in Norway named Trolltech. QT is a C++ multi-platform toolkit that originally cost money if you wanted to make commercial applications with it. After the GNOME Project was started Trolltech created the QT Foundation and dual-licensed QT including a free software friendly license. Trolltech was eventually consumed by Nokia and QT has since been re-licensed under three different licenses... pick the one you want. KDE released version 4.0 in January of 2008.

    GNOME - The GNU Network Object Model Environment desktop environment was originally started by a group of programmers (primarily financially sponsored by Red Hat) who were not happy with the original QT licensing. They also wanted to use C rather than C++. GNOME is based on the GIMP toolkit (GTK).  GNOME decided to change things with GNOME 3 Shell.

    GNOME 3 Shell was release on April 6, 2011.  Fedora was one of the first distributions to ship it.  GNOME 3 requires hardware support / accellerated video although it does have a fallback mode which does not.  GNOME 3 has a searched-based interface and does away with some of the features (thought of as clutter by its developers) from the GNOME 2 series.  Further development of GNOME 2 has stopped and GNOME 3 is the future of GNOME.

    MATE - MATE is a desktop environment forked from the now-unmaintained code base of GNOME 2. The name derives from yerba mate, a species of holly native to subtropical South America used to prepare a beverage called mate. The renaming is necessary to avoid conflicts with Gnome 3 components.

    Cinnamon - Cinnamon is a fairly new project from the Linux Mint developers that uses the GNOME 3 libraries to create a desktop that is stylisticly a combination of GNOME 2 and GNOME 3.

    XFCE - Olivier Fourdan decided to create a free clone of CDE in 1996 based on the non-free XForms GUI toolkit. Since the toolkit wasn't free enough neither Red Hat nor Debian liked it. Olivier eventually rewrote XFCE in GTK. It is considered a lighter-weight alternative to KDE and GNOME.

    LXDE - The project was started in 2006 by Taiwanese programmer Hong Jen Yee, also known as PCMan, when he published PCManFM, a new file manager and the first module of LXDE.  LXDE has ceased development as the developers have decided to abandon the GTK widget library and switch to QT... and have decided to join forces with the RazorQT project... and now have created LXQT.

Network Transparency
    As previously mentioned, X11 was designed with network transparency in mind and as a result, there are a number of ways to run X11 apps or complete desktop environments remotely.

    The easiest way to run an X11 app is to use the X11 tunnelling provided by ssh (ssh -X). Alternatively you can use the xhost utility and properly set the DISPLAY environment variable.

    For running complete desktop environments one may use programs like VNC and NX. Many X display managers also speak the X Display Manager Control protocol (XDMCP) although it is not usually turned on by default.  There is even an RDP server for Linux named xrdp.  A very nice fork of NX2 exists named X2Go.

    Complete desktops can also be run over ssh with Xnest and Xephyr.

    No matter what method you use for remote access, it should work fine over a LAN but perhaps not as well over a WAN or broadband connection due to latency.

    Red Hat released the SPICE remote KVM-VM (virtual machine) display protocol under the GPL v2 in January 2010 and it is hoped it gets adapted to a general purpose remote display protocol.

The Future?

    One complaint about X11 is that there are too many layers and that creating efficient software (especially games) is hard.  Wayland is a fairly new project with a goal providing an efficient alternative to X11.  It is still early in development and it remains to be seen how well it will do. Canonical initially seemed to be responsive to Wayland but decided to create their own display system (Mir) to better serve their needs with regards to one interface for every device.  Mir, which recently announced the release of version 1.0,  seems to be built on top of Wayland.
}}
# Firewalls with firewalld {{
REFERENCES

LaUSAH - Section 27.8 Firewalls
RHEL7 Security Guide, Chapter 5, Using Firewalls

SERVICES AND PORTS

Looking at the /etc/services file you will see a long list of the most well known services. Ports 1024 and lower are considered to be "privileged" ports and traditionally require root privileges to start up software that bind to them.

User's programs can usually bind to any ports 1025 and higher.

Just because a daemon / service is typically associated with a particular port or range of ports does not mean that it has to use those ports. Most applications can be configured to use whatever port(s) desired. Therefore do not assume that if a particular port is in use that a particular app is using it. Remember you are free to name binaries anything you want and sometimes unauthorized users try to be tricky.

IPTABLES OVERVIEW

    Filtering is performed by the network stack within the kernel
    Asserts policies at OSI Reference Model layers 2, 3 and 4
    Only packet headers are inspected

FIREWALLD OVERVIEW

    Red Hat introduced a new firewall system with the release of RHEL7, named firewalld
    There is a firewalld GUI named firewall-config and a CLI program named firewall-cmd.
    firewalld supports multiple zones

USING FIREWALLD

Check to see if firewalld is running:
      systemctl status firewalld
firewalld stores its rules in:
      /etc/firewalld/zones/public.xml

firewall-cmd --state
firewall-cmd --get-active-zones
firewall-cmd --list-all

firewall-cmd --add-service=http
firewall-cmd --add-service=http --permanent
firewall-cmd --remove-service=http
firewall-cmd --remove-service=http --permanent

firewall-cmd --add-port=30000/tcp --permanent
firewall-cmd --add-port=30000-30010/tcp --permanent
firewall-cmd --remove-port=30000/tcp --permanent
firewall-cmd --remove-port=30000-30010/tcp --permanent

firewall-cmd --reload
firewall-cmd --complete-reload
firewall-cmd --query-panic
firewall-cmd --panic-on
firewall-cmd --panic-off

FIREWALLD SERVICE FILES

firewall-cmd --get-services
       /usr/lib/firewalld/services/{service-name}.xml
firewall-cmd --info-service={service-name}

Drop-in Files:
     /etc/firewalld/services/

FIREWALLD ADVANCED FEATURES

Direct Interface
Rich Rules
Lockdown
IP Sets
}}
# System logs & Monitoring {{
REFERENCES

    LaUSAH - Chapter 10, Logging
    RHEL7 System Aministrators Guide, Chapter 23, Viewing and Managing Log Files (PDF in weekly content)

RSYSLOG

    Rather than each service / daemon having their own logging features, a general purpose logging service was created.
    RHEL/CentOS provides a package named rsyslog that includes the rsyslogd daemon.
    Most all logs are stored under /var/log/ or within a sub-directory.

SAMPLE /etc/rsyslog.conf

    *.info;mail.none;authpriv.none;cron.none /var/log/messages
    authpriv.* /var/log/secure
    mail.* -/var/log/maillog
    cron.* /var/log/cron
    *.emerg *
    uucp,news.crit /var/log/spooler
    local7.* /var/log/boot.log

LOGROTATE

    Logrotate allows for the automatic rotation, compression, removal and mailing of log files.
    Logrotate can be set to handle a log file daily, weekly, monthly or when the log file gets to a certain size.
    Normally, logrotate runs as a daily cron job.

LOGROTATE FILES

    Runs as a cron job:
         /etc/cron.daily/logrotate
    Config files:
         /etc/logrotate.conf (compress)
          /etc/logrotate.d/* (service specific logrotate configs)
    Note: Most services include a specific logrotate config.
         [root@sdowdle ~]# rpm -qc httpd | grep logrotate
       /etc/logrotate.d/httpd

EXAMPLE ROTATED LOGS

    [root@esus ~]# ls -lh /var/log/messages* (from older system)
    -rw------- 1 root root 80K Sep 29 08:53 /var/log/messages
    -rw------- 1 root root 12K Sep 26 04:03 /var/log/messages.1.gz
    -rw------- 1 root root 11K Sep 19 04:02 /var/log/messages.2.gz

    [root@sdowdle ~]# ls -l /var/log/messages*
    -rw------- 1 root root 464 Sep 29 10:18 /var/log/messages
    -rw------- 1 root root 10089 Sep 26 03:29 /var/log/messages-20200926

LOGWATCH

    Logwatch is a customizable, pluggable log monitoring system.
    Runs as a cron job: /etc/cron.daily/0logwatch
    It will go through your logs for a given period and make a report in the areas that you wish with the detail that you wish.
    By default the logrotate package will email the root user a report every morning.

USEFUL COMMANDS

    tail - output the last part of files
         -f flag is for follow... watch a log file as it grows
    grep - search a log file
    zgrep, zless and zcat - for compressed log files

    sysstat - provides sar and iostat

        sar and iostat enable system monitoring of disk, network, and other IO activity by parsing the binary log data collected every 10 minutes.
        By default, systat runs as a cron job.

journald

    RHEL7 introduced the systemd init system. systemd includes a new logging facility named journald.
    journald can be run in parallel with rsyslog or as a replacement for it.
    The command used to access the journald binary log files is journalctl.
    For a regular user to access logging data via journalctl, add them to the adm group.

SESSION VS PERSISTANT

    journald by default stores log data in RAM.
    To enable persistant storage just create a directory named journal in /var/log if it doesn't already exist and then restart the systemd-journald service or reboot.

JOURNALD FEATURES

    Gets all of boot and shutdown.
    More log data
    kernel, user processes, and from STDIO and STDOUT
    Includes extensive metadata info
    All logged data are shown including rotated logs.
    journalctl offers database-like queries.
    journalct offers some tab completition features.
    Graphing of boot up showing service start up times.

journalctl Examples

    journalctl -n Number
    journalctl -p Priority
    journalctl -u Unit
    journalctl -f (like tail -f)
    journalctl --since=value --until=value
    journalctl --disk-usage

journalctl presentation video by Lennart Poettering

    https://www.youtube.com/watch?v=i4CACB7paLc
}}
# Automation with Cron {{
REFERENCES

    RHEL7 System Administrators Guide
         Chapter 24, Automating System Tasks (PDF)

BACKGROUND

    cron is a standard UNIX daemon that runs specified programs at scheduled times.
    anacron is like cron but is aimed at machines that aren't on all the time.
    at is a utility to schedule one-time tasks.
    batch is like at except it only runs one-time jobs when the system load is low.

CRON FILES

    crontabs package -
         Provides /etc/crontab and periodic directories.
         [root@dowdle ~]# cat /etc/crontab (examine output)
    cronie package -
         An enhanced vixie-cron that provides cron service
         [root@dowdle ~]# rpm -ql cronie (examine output)
    What is the daemon binary? The service control script? Config files? Documentation?

CRON ACCESS CONTROL

    From crontab (1): If the cron.allow file exists, then you must be listed therein in order to be allowed to use this command.
    If the cron.allow file does not exist but the cron.deny file does exist, then you must not be listed in the cron.deny file in order to use this command.
    If neither of these files exists, only the super user will be allowed to use this command.

THUS SAYS THE MAN PAGES

    From crontab (5):
    The format of a cron command... each line has five time and date fields, followed by a user name if this is the system crontab file, followed by a command.
    Commands are executed by cron(8) when the minute, hour, and month of year fields match the current time, and at least one of the two day fields (day of month, or day of week) match the current time.
    cron(8) examines cron entries once every minute.

CRONTAB FORMAT

    {minute} {hour day-of-month} {month} {day-of-week} {command}

        minute - 0-59
        hour - 0-23
        day of month - 1-31
        month - 1-12 (or names)
        day of week - 0-7
        (0 or 7 is Sun, or use names)

    Ranges of numbers are allowed. Ranges are two numbers separated with a hyphen. The specified range is inclusive. For example, 8-11 for an "hours" entry specifies execution at hours 8, 9, 10 and 11.

    Lists are allowed. A list is a set of numbers (or ranges) separated by commas.
    Examples: "1,2,5,9", "0-4,8-12".

    Step values can be used in conjunction with ranges. Following a range with "<number>" specifies skips of the number's value through the range.

    For example, "0-23/2" can be used in the hours field to specify command execution every other hour.
    Steps are also permitted after an asterisk, so if you want to say "every two hours", just use "*/2".

    Names can also be used for the "month" and "day-of-week" fields.
    Use the first three letters of the particular day or month (case doesn’t matter).
    Ranges or lists of names are not allowed.

    The "sixth" and last field specifies the command to run.

        The entire command portion of the line, up to a newline or % character, will be executed by /bin/sh or by the shell specified in the SHELL variable of the cronfile.
        Percent-signs (%) in the command, unless escaped with backslash (\), will be changed into newline characters, and all data after the first % will be sent to the command as standard input.

USING CRONTAB

    crontab -l = Lists your cron jobs
    crontab -e = Create / modify your cron jobs
    crontab -r = Deletes all cron jobs

    Work with another user's crontab
    crontab -u username -{additional-flag}

EXAMPLES

    */10 * * * * cd /var/yp; make 2>&1 > /dev/null;
    11 2 * * * /usr/bin/wget -O - -q -t 1 http://{some-url}

    # run system activity accounting tool every 10 minutes
    */10 * * * * root /usr/lib64/sa/sa1 1 1

    # generate a daily summary of process accounting at 23:53
    53 23 * * * root /usr/lib64/sa/sa2 -A

REVIEW FROM LOGGING MATERIAL

    logwatch is run as a cron job. What file is used?
    logrotate is run as a cron job. What file is used?
}}
# Server apps: Email {{
LaUSAH
  Chapter 18, Electronic Mail
  Chapter 16, DNS: The Domain Name System, MX records

RHEL7 System Administators Guide, Chapter 15, Mail Servers (PDF)

What do you use for email?
    What is provided by your ISP?
    What is provided by MSU?
    Free services like gmail, Hotmail, Yahoo!Mail?
    What is provided by your work?

What comprises an email system?
    It used to be that you could simply install an SMTP server and you had an "email server". That is not the case any more. There are additional pieces that have been added to email over the last decade or so:

    Virus scanning (ClamAV)
    Spam scanning (SpamAssassin)
    Webmail (RoundCube [ours])
    Mobile Access
    Collaboration tools
        Global Addressbook
        Calendaring
        Documents
        Resources
        To-do lists
    Mailing lists? Usually done by separate software like Mailman (python-based) and Sympa (perl-based)

    Also common these days are backup mailservers for redundancy and relaying mailservers that act as filtering systems.

How email works
    DNS plays a big role in the flow of email. When a user@domain1.com sends an email to user@domain2.com a lot has to be in place for it to work. user@domain1.com's email client talks to its configured SMTP server which accepts the email for delivery. The SMTP server for domain1 has to look up the MX records for domain2. It then attempts to connect to the server with the lowest MX record value in an attempt to deliver it. If for whatever reason it can't deliver it to the first MX server, it will progress to the next MX IP with the lowest value. If all MX servers are unreachable, the SMTP server for domain1 will queue the email and try again later. Typically it tries every 4 hours for 4 days at which point it gives up.

    What are the MX servers for your email account?  To find out do the following:

    dig MX yourdomain.tld

    Does your domain have more than one MX record?  What are their values?

Various anti-spam tricks
    I have seen a lot of crazy stuff done by email admins to reduce their amount of spam.

    Adding MX records for servers that don't exist.
    Automatically reject every first attempt (graylisting).
    SPF and DKIM.
    Auto reject systems where you have to get put on a whitelist.
    Email is fundamentally broken and the only thing that can save it... is PKI.

Looking for a complete package

    No Linux distro I'm aware of offers a reasonable email system out of the box. Most offer some/many of the components I mentioned but none of them put them together in any integrated way. As a result a number of third party management / middleware systems have been created.

A few that seem reasonable are:

    Mailscanner (wikipedia)
    Zimbra Collaboration Suite (wikipedia) [ours]
    Zarafa (wikipedia)
    Scalix (wikipedia)
    Citadel (wikipedia)
    Kolab (wikipedia)

SMTP server software

    sendmail
    postfix (installed in our student VMs)
    exim
    qmail

    Things SMTP servers need to be able to do:
        Host multiple domains (virtual hosting)
        Allow for user1@domain1 and user1@domain2 (virtual users)
        Map multiple addresses to a single account (aliases)

POP and IMAP

    Dovecot
    UW imap
    Courier

Email Client Programs

    /usr/bin/mail - Provided by the mailx  program.  Very simple, line oriented client
    alpine - Full-featured TUI client available in EPEL

Email Related Configs

    /etc/aliases - global aliases and forwards
    ~/.foward - user defined aliases and forwards
    /etc/postfix/* - postfix config location - since student VMs have Postfix installed
}}
# Server apps: Apache Intro {{
LaUSAH REFERENCE - Chapter 19, Web Hosting

RHEL8 Deploying Different Types of Servers, Chapter 1, Setting Up The Apache Web Server (PDF in weekly materials)

    Brief History of Apache
In the beginning, the father of the World Wide Web (Tim Berners-Lee) created the first web browser (WorldWideWeb) and the first web server (CERN HTTPd) for the NeXTSTEP platform. CERN HTTPd version 0.1 was released in June 1991. It was later ported to other flavors of Unix and OpenVMS. Version 3.0A was the final version released on July 15, 1996.

Next came NCSA HTTPd written by Robert McCool and others. They also had one of the first graphical web browsers that was multi-platform and it was named Mosaic. Most of the NCSA folks left to start up Netscape... and as a result development of NCSA HTTPd and Mosaic languished. Mosaic was eventually licensed to several other browser makers (including Microsoft for Internet Explorer). Development of NCSA HTTPd was eventually stopped in 1998.

Apache started life within the community that was left behind when the development of NCSA HTTPd stalled... and a series of patches for NCSA HTTPd were circulated mostly by email among the various community developers who remained. The group eventually decided to take all of their patches (a patchy server) and start over as the Apache project. Over time any of the original NCSA HTTPd code that remained was replaced. Version 2 of Apache was a substantial rewrite of the 1.x code.

Today Apache continues to hold a prominent marketshare in the web server software market. The Feb. 2021 survey by Netcraft (1,204,252,411 sites, 263,042,054 unique domains) shows Apache in second place with a 26.32% marketshare with Microsoft IIS server in third place with 6.50%. The first place contender is another free software packaged named nginx with 34.54%.
Perhaps more revealing are their numbers for "Market share of active sites" where Apache is leading with 25.48% and Microsoft IIS doesn't even place in the top four. nginx is in second place with 19.84%.
Also of interest are their numbers for "Market share of the top million busiest sites" where Apache leads with 25.58% and Microsoft IIS is in fourth place with 6.87%. nginx is in second place with 23.21%.
For more information see:

    Netcraft's September 2020 Web Server Survey
https://news.netcraft.com/archives/2021/02/26/february-2021-web-server-survey.html

    Apache Basics
Packages:
httpd
httpd-tools
httpd-manual (if you want the web-based docs)
mod_* (if you want any additional embedded functionality)

    Popular add on packages:
php* (used to be forked but is now PHP FastCGI Process Manager php-pfm)
mod_perl (EPEL)
mod_ssl

    systemd unit file:
/usr/lib/systemd/system/httpd.service
/usr/lib/systemd/system/httpd@.service

    Default ports:
http: 80
https: 443 (if mod_ssl is installed and configured)

    Configuration files:
/etc/httpd/conf/httpd.conf
/etc/httpd/conf/*
/etc/httpd/conf.d/*

    Binaries: (some from httpd-tools)
/usr/bin/ab
/usr/bin/htpasswd
/usr/bin/logresolve
/usr/sbin/apachectl
/usr/sbin/httpd
/usr/sbin/rotatelogs
/usr/sbin/suexec

    Logs:
/etc/logrotate.d/httpd
/var/log/httpd/access_log, /var/log/httpd/error_log

    Working directory:
/var/www

    Man pages:
/usr/share/man/man1/ab.1.gz
/usr/share/man/man1/htdbm.1.gz
/usr/share/man/man1/htdigest.1.gz
/usr/share/man/man1/htpasswd.1.gz
/usr/share/man/man1/logresolve.1.gz
/usr/share/man/man8/apachectl.8.gz
/usr/share/man/man8/htcacheclean.8.gz
/usr/share/man/man8/httpd.8.gz
/usr/share/man/man8/rotatelogs.8.gz
/usr/share/man/man8/suexec.8.gz

The httpd-manual package contains a complete manual and reference guide that can also be found:
http://httpd.apache.org/docs/2.4/

Common configuration options
DocumentRoot - /var/www/html
UserDir - ~username
ScriptAlias - Defines where scripts can run from
          /var/www/cgi-bin
Access controls with
Directory - Per directory settings
DirectoryIndex - What file is shown if directory is requested
index.html
index.php
AccessFileName
.htaccess (dynamic config changes)
.htpasswd
Location
Complete customization of logging and error pages
VirtualHost

    Also of interest
1) A nice write-up on the 25th anniversary of the WWW from Dec. 2015
2) Tim Berners-Lee's Three challenges for the web from Mar. 2017 which includes:
i. We’ve lost control of our personal data
ii. It’s too easy for misinformation to spread on the web
iii. Political advertising online needs transparency and understanding
}}
# Server apps: Apache hands-on HW 5 {{
Goals for this hands on (aka Homework 5)

We are going to do a few of the most common Apache configuration changes:

Verify that apache (httpd) is installed and running
We are going to enable user directories which allows users to create a directory within their home directory that apache can access with a ~username reference (Example: http://www.cs.montana.edu/~sdowdle)
We are going to create a virtualhost as an example of a single apache server hosting multiple domain names
Lastly we are going to install PHP and make sure it is working with apache
All work is done on your own student VM.  Note, when you see "xx"  or "lastname" below,  you'll want to alter the content to reflect your own information.

Getting Started

Is apache installed? (rpm -q httpd)  If not, install it
dnf  install httpd --refresh

Is it set to run?  (systemctl status httpd.service)  If not, set enable it (systemctl enable httpd.service).
Is it running?  (systemctl status httpd.service)  If it isn't running, start it. (systemctl start httpd.service)

Verify your web server is working from the course server (links http://kvm-dowdle) [your name]

Refresher on firewalld
Did it work?  It shouldn't have because we have not opened up our VM's firewall yet.
     firewall-cmd --list-all (shows what's open so far, shouldn't see http or https yet)
     firewall-cmd --add-service=http ; firewall-cmd --add-service=http --permanent
    firewall-cmd --list-all (Look good now?)

Try again (from the course server):
     links http://kvm-dowdle [your name]
Working now?

What showed up?

Look at /etc/httpd/conf.d/welcome.conf and do what it says to disable the welcome page.

Restart apache (systemctl restart httpd)

Now browse to it again (links http://kvm-dowdle) [your name]

What changed?

Create an index page for your DocumentRoot:
     nano -w /var/www/html/index.html
Put inside of it "This is the web page for the default domain".

UserDir

Make a backup copy of your /etc/httpd/conf.d/userdir.conf file.  Do NOT end the backup filename in .conf or it will still be used by Apache.
Edit the /etc/httpd/conf.d/userdir.conf file. Find the line that says:
UserDir disable
...and add a # to the front of it. Find the line that says:
#UserDir public_html
...and remove the comment.
SELinux Booleans that need to be changed:
      getsebool -a | grep httpd
      Need to enable httpd_enable_homedirs and httpd_read_user_content
           setsebool -P httpd_enable_homedirs on
           setsebool -P httpd_read_user_content on

Restart apache (systemctl restart httpd.service)
Now create a public_html directory in one of your user directory as your user
mkdir /home/lastname/public_html
Make sure the permissions on your user's home directory are at least 711.
Make sure the permissions on the public_html directory are at least 755.
Create an index.html page inside of public_html.
Browse to it:
     links http://kvm-lastname/~lastname
VirtualHost

We will create a fake (i.e. using /etc/hosts for DNS resolution) host / domain named www.testdomain1.com.

Edit the /etc/hosts file and add the following line:

192.168.122.1xx       www.testdomain1.com          testdomain1
192.168.122.1xx       kvm-lastname.localdomain     kvm-lastname
You can find your ip address by looking at the output of the following command as root on your student VM:
     ip add
Or by looking in /etc/sysconfig/network-scripts/ifcfg-eth0

Now we need to edit the /etc/httpd/conf/httpd.conf to enable VirtualHosts and add to virtualhost references... one for the default host and one for our new virutal domain.

Edit /etc/httpd/conf/httpd.conf and add the following lines at the bottom of the configuration:

<VirtualHost 192.168.122.1xx:80>
     ServerName kvm-lastname.localdomain
     DocumentRoot /var/www/html
</VirtualHost>

<VirtualHost 192.168.122.1xx:80>
     ServerName www.testdomain1.com
     DocumentRoot /var/www/testdomain1
     CustomLog logs/testdomain1-access_log combined
     ErrorLog logs/testdomain1-error_log
</VirtualHost>

Make sure any DocumentRoot directories you refer to exist:

mkdir /var/www/testdomain1

Put an index.html page in the testdomain1 directory

  nano -w /var/www/testdomain1/index.html
  Add to it the line "Hello from testdomain1" and save.

Restart the webserver (systemctl restart httpd.service)

Browse to your new domain
links www.testdomain1.com
Did it work?
Installing PHP

dnf install php
After installing php do the following: systemctl enable --now php-fpm.service
Restart the webserver (systemctl restart httpd.service)

Put an index.php page into /var/www/testdomain1 and put inside it the following:

<?PHP
phpinfo();
?>
Browse to the new domain again. Did it work?  Why not?
Let's try our default domain instead.
Create an index.php file in /var/www/html/ and put in the same sample php code shown above and then browse to your default domain.
     links http://localhost/   or links http://kvm-lastname/
Which page showed up?  The index.html or the index.php page?
Now explicitly browse to the index.php page.
    links http://localhost/index.php or links http://kvm-lastname/index.php
Did it work?

Submitting Homework 5

You can find the instructions here as /public/homework5.txt on the course server.  Feel free to copy it over to /root/HOMEWORK/ on your student VM.
}}
# Server apps: MariaDB Intro {{

A brief history of MySQL and MariaDB

    MySQL was originally created in 1995. The developers around it formed MySQL AB, a Swedish company, that mainly got its money from support contracts. Eventually MySQL became dual / multi-licensed with one of them being the GNU GPL.

    In 2008 Sun Microsystems purchased MySQL AB for a reported $1 billion although since that time many of the original / main developers have left Sun to form alternative projects. There is growing confusion as to who will end up being the driving force behind MySQL in the years to come. In January of 2010, Oracle acquired Sun Microsystems.

    MySQL was designed to be a fast, light-weight database especially suited for the needs of web-based applications. Most often the M in "LAMP". MySQL is accessible from a large variety of programming languages including Perl, PHP, Python, C, C++ and from Java's ODBC.

    MySQL has had a reputation of not being as feature complete as Oracle's database products and / or PostgreSQL. As a result some database purists turn their noses up at MySQL. As MySQL has matured many / most of the "missing features" have either been added or are on the roadmap for a future release.

    The correct pronunciation of MySQL is "my es que el" and not "my sequel". SEQUEL was an IBM database language which was a predecessor to SQL.  Unfortunately because of some other database products pronouncing SQL as "sequel" it might be the case that more people say it wrong than right.

    If you want more than that, read the MySQL wikipedia page.

    Some of the unique features of MySQL are:

        Multiple database storage engines (table types) - InnoDB allows for transactions
        Flexible table design - Easily insert columns and alter existing column data-types on-the-fly

        MariaDB is a community-developed fork of the MySQL and development is led by some of the original MySQL developers.  MariaDB was forked due to concerns MySQL's acquisition by Oracle Corporation.  Most Linux distributions provide mariadb.
        Monty Widenius and his daughters, My and Maria
Packages

    mariadb-bench: MariaDB benchmark scripts and data
    mariadb-libs: The shared libraries required for MariaDB clients
    mariadb-server: The MariaDB server and related files
    mariadb-test: The test suite distributed with MySQL
    mariadb: MariaDB client programs and shared libraries
Additional Packages

    bytefx-data-mysql: MySQL database connectivity for Mono
    lua-sql-mysql: MySQL database connectivity for the Lua programming
    mod_auth_mysql: Basic authentication for the Apache web server using a
    MySQL-python: An interface to MySQL
    pam_mysql: PAM module for auth UNIX users using MySQL data base
    perl-DBD-MySQL: A MySQL interface for perl
    php-mysql: A module for PHP applications that use MySQL databases
    qt3-MySQL: MySQL drivers for Qt 3's SQL classes
    qt-mysql: MySQL driver for Qt's SQL classes
    ruby-mysql: A Ruby interface to MySQL
    tcl-mysqltcl: MySQL interface for Tcl
Files

    Control script
           /usr/lib/systemd/system/mariadb.service

    Binaries
        /usr/bin/mysqld_safe - Server application
        /usr/bin/mysql - Client application (part of the mariadb package)
        /usr/bin/mysqldump - Backup utility (part of the mariadb package)

    Configuration files
        /etc/my.cnf (part of the mariadb-libs package)

            [mysqld]
            datadir=/var/lib/mysql
            socket=/var/lib/mysql/mysql.sock
            user=mysql
            # Disabling symbolic-links is recommended to prevent assorted security risks
            symbolic-links=0

            [mysqld_safe]
            log-error=/var/log/mysqld.log
            pid-file=/var/run/mysqld/mysqld.pid

        Let's look at the files on the filesystem:
            cd /var/lib/mysql ; ls -lha (Each directory is a database)
Usage

    Use a client to connect to the server and then run commands on the server.

    Connect to mariadb-server using mysql text-based client:
    mysql -u lee.dowdle -h host -p databasename
    -p = prompt for password
    databasename = set database to "use"

    Creating a database:

         mysql> create database whatever;

    Choosing a database to use:

         mysql> show databases;
         mysql> use databasename;
         mysql> show tables;
         mysql> describe tablename;

    Creating a table:

         See tutorial link below.
         Example:
              mysql> CREATE TABLE pet (name VARCHAR(20), owner VARCHAR(20),
        -> species VARCHAR(20), sex CHAR(1), birth DATE, death DATE);

    Give a user access to a database:
    mysql> grant all on whatever.* to user@host identified by 'password';

    Record actions:
    INSERT, UPDATE, SELECT, DELETE

    Please see MySQL's tutorial.

Backups

    mysqldump -u root -p --all-databases --hex-blob --routines --triggers > mysql-complete-backup.sql
        > = redirect output to a file since stdout is the default
        You can get massive disk savings by compressing the .sql (120MB -> 25MB)
        Of course you can do per-user backups, see man page for full details
        What kind of file is an .sql file? A flat text file with .sql statements.

    To import from an .sql file, just redirect from a file.  Example:
         mysql -u user -h hostname -p databasename < database.sql
}}
# Server apps: DNS Intro & hands-on [Homework 7] {{
LaUSAH REFERENCE - Chapter 16, DNS: The Domain Name System

RHEL7 Networking Guide, Chapter 15, DNS Servers (PDF in weekly materials)

Where does BIND rank? (from LAUSAH Fourth Edition)
    Table 17.1

Introduction to DNS

    DNS associates hostnames with their respective IP addresses, so that when users want to connect to other machines on the network, they can refer to them by name, without having to remember IP addresses.

    Use of DNS and FQDNs also has advantages for system administrators, allowing the flexibility to change the IP address for a host without affecting name-based queries to the machine. Conversely, administrators can shuffle which machines handle a name-based query.

    DNS is normally implemented using centralized servers that are authoritative for some domains and refer to other DNS servers for other domains.

    When a client host requests information from a nameserver, it usually connects to port 53. The nameserver then attempts to resolve the FQDN based on its resolver library, which may contain authoritative information about the host requested or cached data from an earlier query. If the nameserver does not already have the answer in its resolver library, it queries other nameservers, called root nameservers, to determine which nameservers are authoritative for the FQDN in question. Then, with that information, it queries the authoritative nameservers to determine the IP address of the requested host. If a reverse lookup is performed, the same procedure is used, except that the query is made with an unknown IP address rather than a name.

    Nameserver Zones

    On the Internet, the FQDN of a host can be broken down into different sections. These sections are organized into a hierarchy (much like a tree), with a main trunk, primary branches, secondary branches, and so forth. Consider the following FQDN:

    bob.sales.example.com

    When looking at how an FQDN is resolved to find the IP address that relates to a particular system, read the name from right to left, with each level of the hierarchy divided by periods (.). In this example, com defines the top level domain for this FQDN. The name example is a sub-domain under com, while sales is a sub-domain under example. The name furthest to the left, bob, identifies a specific machine hostname.

    Except for the hostname, each section is called a zone, which defines a specific namespace. A namespace controls the naming of the sub-domains to its left. While this example only contains two sub-domains, an FQDN must contain at least one sub-domain but may include many more, depending upon how the namespace is organized.

    Zones are defined on authoritative nameservers through the use of zone files (which describe the namespace of that zone), the mail servers to be used for a particular domain or sub-domain, and more. Zone files are stored on primary nameservers (also called master nameservers), which are truly authoritative and where changes are made to the files, and secondary nameservers (also called slave nameservers), which receive their zone files from the primary nameservers. Any nameserver can be a primary and secondary nameserver for different zones at the same time, and they may also be considered authoritative for multiple zones. It all depends on how the nameserver is configured.

    Nameserver Types

        There are two primary nameserver configuration types:

        Authoritative

        Authoritative nameservers answer to resource records that are part of their zones only. This category includes both primary (master) and secondary (slave) nameservers.

        Recursive

        Recursive nameservers offer resolution services, but they are not authoritative for any zone. Answers for all resolutions are cached in a memory for a fixed period of time, which is specified bythe retrieved resource record.


    Most Frequently Used Types of Records
    DNS record types (from LAUSAH Fourth Edition)
    Table 17.6

    A - Address Records
    CNAME - Canonical Name maps one name to another
    MX - Mail eXchange record
    NS - NameServer record
    PTR - PoinTeR record, primarily for reverse resolution
    SOA - Start Of Authority resource record
    Others - SRV, TXT, AAAA
bind package information

    Package name:
        bind - With authoritative zones

    Service control script:
        /etc/rc.d/init.d/named (sysvinit)
        /usr/lib/systemd/system/named.service (systemd)

    Binary:
        /usr/sbin/named

    Config files:
        [root@ct-dowdle /]# rpm -qc bind
        /etc/logrotate.d/named
        /etc/named.conf
        /etc/named.iscdlv.key
        /etc/named.rfc1912.zones
        /etc/named.root.key
        /etc/rndc.conf
        /etc/rndc.key
        /etc/sysconfig/named
        /var/named/named.ca
        /var/named/named.empty
        /var/named/named.localhost
        /var/named/named.loopback
Simplified view of how it works

    /etc/named.conf states which zones a name server is authoritative for.
    Example:

    options {
        directory "/var/named";
    };

    zone "example.com." IN {
        type master;
        file "example.com.zone";
    };

    See "Example Zone Record" in this week's content to see a sample zone record.

Zone Transfers

    A zone transfer is the process by which a DNS master communicates with one or more DNS slave servers to propagate new and updated zone information. With BIND you have to create an encryption key setup where your servers trust each other and accept transfers.

Common Mistakes to Avoid

    It is very common for beginners to make mistakes when editing BIND configuration files. Be sure to avoid the following issues:

        Take care to increment the serial number when editing a zone file.
        If the serial number is not incremented, the master nameserver has the correct, new information, but the slave nameservers are never notified of the change and do not attempt to refresh their data of that zone.
        Be careful to use ellipses and semi-colons correctly in the /etc/named.conf file. An omitted semi-colon or unclosed ellipse section can cause named to refuse to start.
        Remember to place periods (.) in zone files after all FQDNs and omit them on hostnames.
        A period at the end of a domain name denotes a fully qualified domain name. If the period is omitted, then named appends the name of the zone or the $ORIGIN value to complete it.
        If a firewall is blocking connections from the named program to other nameservers, update your firewall.
        By default, BIND version 9 uses random ports above 1024 to query other nameservers. Some firewalls, however, expect all nameservers to communicate using only port 53. To force named to use port 53, add the following line to the options statement of /etc/named.conf:
            query-source address * port 53;
Hands On - Installing a caching-only nameserver in your student VM:

    Inside your student VM as root do the following:
    yum install bind (may already be installed)

    Is bind set to run automatically? If not:

        systemctl status named.service
        systemctl enable --now named.service

    Now to start using our own nameserver for DNS resolution:

        nano -w /etc/resolv.conf
        Comment out current line, add new line:
        nameserver 127.0.0.1

            Test it. Does it work?
            How do you test?

When done with the homework:

    There is a /public/homework7.txt on the course server.  Just copy that to your ~/HOMEWORK/ directory on your student VM.
}}
# Virtualization: Overview {{
LaUSAH REFERENCE - Chapter 24, Virtualization - Chapter 25, Containers

The goal of this lecture is to introduce you to thes various virtualization products that are available for Linux and to compare and contrast them.

Related but distinctly different topics include:Terminal Services and Application Virtualization

Why Virtualize?

    Increase hardware utilization
    Improved resource management (configuration changes vs. hardware)
    Cost and energy savings
    Legacy OS / Applications won't run on new hardware
    Easier migration because hardware is abstracted
    Development and Testing
    Less painful upgrades with easy rollback
    Improved reliability with high availability / live or offline migration
    Security by isolating services
Use Cases

    Desktop user - Trying out new OSes, Linux distro hopping
    Small business - Servers and desktops
    Enterprise business - Datacenters for cost and energy savings
    Education - You have VMs and containers, right?
    Research - Easily make environments and simulations
    Cloud computing is heavily based on virtualization
Brief History of Virtualization

    On mainframe computers IBM has had virtualization features built into their hardware since the 1960s.

    In micro and personal computers the first virtualization product I heard about was a card for the Apple II that allowed running some DOS applications.

    Later Atari ST users could emulate Atari 8-bit computers.
    PC emulation was possible with PC-Ditto.
    Mac emulation was possible with Spectre.

    Video game machine emulators are quite common... think MAME.

    VMware released its first product in 1999.

Types of Hypervisors

    A term you will see tossed around frequently when referring to both Full virtualization and paravirtualization is hypervisor. The two distinct categories of hypervisors are:
        Level 1 - bare metal
        Level 2 - hosted
    Many virtualization vendors offer a layered approach to their product line and may offer both type 1 and type 2 based products.

Products

----

VMware [1999] (wikipedia)
    Full virtualization
        Type 2 - Windows, Mac, and Linux
            VMware Player (no cost)
            Server (no cost)
            Workstation (cost)
            Fusion (cost)
        Type 1
            ESX / Infrastructure (cost)
            ESXi (no cost)
SWsoft Virtuozzo [2001] (wikipedia) - Later Parallels
    OS virtualization
        Linux version 2001 (cost)
        Windows version 2005 (cost)

Linux-VServer [2001] (wikipedia)
    OS virtualization
        Linux only (free software)

Xen / Citrix [2003] (wikipedia)
    Paravirtualization
        Linux (free software, no cost, and cost)
        Windows (maybe)

OpenVZ [2005] (wikipedia)
    OS virtualization (upstream of Virtuozzo)
        Linux only (free software)

Parallels [2005] (wikipedia)
    Full virtualization
        Type 2 for Mac, Linux & Windows
        May have a Type 1?!?
    OS virtualization (see Virtuozzo)

VirtualBox [2007] (wikipedia)
    Full virtualization
        Type 2 for Mac, Linux, Windows, and Solaris

KVM [2007] (wikipedia)
    Full virtualization
        Type 1.5 / Hybrid? Requires virt support in CPU

LXC [2008] (wikipedia)
    OS virtualization
        Linux only
Docker [2013] (wikipedia)
    Application containers
        Linux and Microsoft Windows
I will spend quite a bit of time elaborating on each product, its design and how they differ... verbally in class. More detail will be offered in additional lectures as we concentrate on specific products.

Things not covered: UML, Wine, Win4Lin, QEMU, Bochs
}}
# KVM Intro {{
KVM History

    KVM (http://www.linux-kvm.org/page/Main_Page) stands for Kernel-based Virtual Machine and was added to the mainline Linux kernel starting with 2.6.20 (early 2007). KVM started as a development project lead by Avi Kivity and funded by technology startup Qumranet in Israel.

    Qumranet created a commercial product based on KVM named SolidICE which specialized in end-user desktop machines. SolidICE included a patented remoting protocol named SPICE which is similar to the RDP, Citrix ICA, Pc-over-IP, etc.

    In September 2008 Qumranet was acquired by Red Hat.

How KVM Works

    KVM requires CPU hardware support for virtualization in the CPU. It is implemented within the Linux kernel via three kernel modules... one for KVM proper (kvm) and two additional modules... one for each CPU type supported - Intel (kvm_intel) and AMD (kvm_amd). All KVM guests are "fully-virtualized".

    The design behind KVM is to use the Linux kernel as the hypervisor... so you get all of the device drivers / hardware support and other functionality that is already part of the Linux kernel (scheduler, memory management, etc) "for free". By reusing code (the Linux kernel) KVM is actually very lean and less complicated when compared to other, stand-alone hypervisors who have to provide their own device driver and OS functions.

KVM is a kernel module, what about the userland?

Disk Storage

    qcow2 is the native disk image format used by KVM.  It is typically thin-provisioned but can be fully pre-allocated if desired.

    RAW disk format is also available and fully pre-allocated

    It is possible to take an existing VM disk image from a few other virt platforms and convert them but often some internal changes may be needed (think drivers) post conversion.

Emulation vs. virtio

    KVM provides a good range of virtualized hardware (examples: e1000 and RTL8139 NICs) but they can be less efficient because the hypervisor has to emulate the devices (aka work harder)

    virtio is a standard for device drivers where the device "knows" it is within virtualization.  virtio drivers provide much better performance than emulated devices.

libvirt - Rosetta stone of virtualization?

    libvirt (http://libvirt.org/) is a library that is released under the GNU Lesser General Public License and is primarily sponsored by Red Hat. The goal of the project is to produce a management library / abstraction layer / API for the plethora of virtualization on the market. libvirt abstracts access to Xen, QEMU, KVM, LXC (native Linux containers), OpenVZ, User Mode Linux and even commercial products such as VMware (type1 and type2), VirtualBox, and Microsoft's Hyper-V.

virt-manager - GUI frontend for Xen or KVM VMs based on libvirt

    virt-manager (http://virt-manager.org/) is a fairly comprehensive application that lets you create, configure, start, stop, destroy, and re-configure KVM virtual machines. It also offers performance monitoring and access to the graphical console of your VMs (via SPICE or VNC).  Available for Microsoft Windows too.

    It can have one or more "connections" for managing local or remote VMs of type system or session (user).
    See also: GNOME Boxes (for session VMs)
        Demo virt-manager here.
virsh -command line tool to manage Xen or KVM VMs based on libvirt

    virsh list --all
    virst start vmname
    virsh shutdown vmname

    virsh can also be used in an interactive mode where you can actually alter the configurations of your VMs.

        Demo virsh here.
virt-install - command line tool for creating virtual machines

    virt-install --name centos74 --ram 2048 \
    --disk path=/vm/demo1.img,size=10 --network=bridge:vmbr0 \
    --vnc --os-type=linux --os-variant=rhel7 \
    --cdrom /isos/centos7-x86_64.iso --accelerate

    Although virt-install is a command line application, when doing an interactive OS install, you almost always need access to a graphical console. Luckily virt-install will automatically launch remote-viewer.
virt-viewer (also remote-viewer)

    virt-viewer is a minimal tool for displaying the graphical console of a virtual machine. The console is accessed using the VNC protocol.
    The guest can be referred to based on its name, ID, or UUID.
    spice://host.example.com:port
    (starts at 5900)
Other tools

Some additional tools from the libguestfs-tools package and other packages include:
    cockpit-machines - add-on for web-based Cockpit control-panel, to eventually replace virt-manager
        qemu-img - Work with disk images
        guestmount - Mount a guest on the host
        virt-cat - Display a file in a virtual machine
        virt-clone - Clone an existing VM to make a new one
        virt-df - Display free space on virtual filesystems
        virt-edit - Edit a file in a virtual machine
        virt-inspector - Display information about a VM
        virt-filesystems - List filesystems in a VM or disk image
        virt-ls - List filesystems in a virtual machine or disk image
        virt-rescue - Run a rescue shell on a virtual machine
        virt-win-reg - Display Windows Registry entries from a VM
        virt-resize - Easily resize a VM disk file
        virt-p2v - Convert a physical machine into a VM
        virt-v2v - Convert a physical machine into a VM
}}
# Virtualization: System Containers {{
System Containers Background

    As mentioned in the virtualization overview, the first form of system containers available for Linux was Virtuozzo made by SWsoft (later Parallels, Odin and finally Virtuozzo) back in 2001.  Virtuozzo's required GPL components were released as a FLOSS project in 2005 named OpenVZ.  OpenVZ and Virtuozzo continue but will always be out-of-tree patches (not in the mainline Linux kernel) and as a result don't have much chance for widespread Linux distro inclusion (it is based specifically on RHEL kernels)... but it is widely adopted by hosting providers.

    Red Hat mostly cares about application containers.  Red Hat was using a form of containers (called gears) they devised for their OpenShift product, they later switched to Docker and Kubernetes.  Red Hat included basic support for LXC in libvirtd/virt-manager but has since discontinued support for LXC in RHEL7. Because of disagreements with Docker Inc. regarding their refusal to accept Red Hat produced patches into Docker, as well as not liking several elements of the Docker design ("big fat daemon"), Red Hat decided to make a Docker alternative (not a Docker fork) named podman.  An early version of podman is available in RHEL7 and a contemporary podman version is included in RHEL8.  podman has some innovative features namely rootless containers and the ability to also run system containers (with a proper container disk image and execution statement).

    Canonical (the company behind the Ubuntu Linux distribution) is the primary developer and maintainer behind LXC ("lex see").  For more information, see:  https://linuxcontainers.org/lxc/introduction/  They have a management layer on top of LXC named LXD ("lex dee").  Canonical also produces daily builds of container images of various Linux distributions.

How are system containers different from application containers?

    System containers are like a full Linux OS sans independent kernel... which includes an init system, and standard system services (logging, cron, sshd, etc), user accounts, etc.  A system container is basically like a light-weight VM without an independent kernel, the inability to load kernel modules (they must be loaded on the container host), etc.  system containers typically have persistent storage (pet).  Application containers typically have a single application, no init system, no system services, and if done correctly, often non-persistent storage (cattle).

What System Container technology to use?

    If I were building a new system container host, I might just choose LXD.  If I was more interested about running legacy stuff, OpenVZ Legacy would be the way to go.  If I wanted to run KVM VMs in addition to containers, I'd probably run OpenVZ 7.  I have to wonder what OpenVZ 8 (based on the fairly fresh RHEL 8 kernel) will be like whenever it comes out.  I really like running a container host as a KVM VM.  OpenVZ Legacy is easily runnable under KVM but OpenVZ 7, not so much.

    I happen to host a number of hobby domains on an OpenVZ Legacy system... and since OpenVZ is a very mature and feature-complete solution, I'll use it to demonstrate system container concepts.

OpenVZ Legacy Components

    OpenVZ Legacy consists of the following components made available from the OpenVZ Legacy software repository:

    vzkernel - the RHEL6 kernel patched with the large, out-of-mainline-tree OpenVZ patch
    userland tools - vzctl, vzlist, vzquota, ploop and a script for bash-completion that provides for bash tab completion for most OpenVZ keywords and values
    OS Templates - a .tar.gz|xz file representing a Linux distribution runtime sans kernel typically with a minimal set of packages and the distros native package manager
Installing OpenVZ Legacy on CentOS 6

    Please note, you can't install OpenVZ Legacy on your student VM which is CentOS 8 based.

    Fresh minimal install of CentOS 6 fully updated
    EPEL repo added for installing bash-completion package
    Disable SELinux in /etc/sysconfig/selinux.  Reboot to ensure it is disabled.
    Add the OpenVZ Legacy repo: wget http://download.openvz.org/openvz.repo -O /etc/yum.repos.d/openvz.repo
    yum clean all ; yum install vzkernel vzctl vzquota ploop bash-completion.  Reboot system to use the newly installed OpenVZ kernel
    Download any desired OS Templates from https://download.openvz.org/template/precreated/ and place them in /vz/template/cache/.
Creating an OpenVZ  container

    I will demonstrate the following creation command in class and in the screencast video:

    vzctl create 1017 \
       --name centos7 \
       --hostname centos7.montanalinux.org \
       --ipadd 23.88.97.17 \
       --ostemplate centos-7-x86_64 \
       --config vswap-1g \
       --diskspace 10G

    That will basically create /vz/private/1017/root.hdd/ directory with a config file and a disk image file.  OpenVZ will then mount the disk image on /vz/root/1017/ and extract /vz/template/cache/centos-7-x86_64.tar.xz under the mount point as well as create a new config named /etc/vz/conf/1017.conf which is a copy of the specified sample config which in this case is /etc/vz/conf/ve-vswap-1g.conf.  When the extraction is completed, it'll unmount the disk image.

OpenVZ Legacy Container lifecycle

    To list available containers: vzlist -a
    To start a container: vzctl start 1017
    To attach to a container: vzctl enter 1017
    To stop a container: vzctl stop 1017
    To remove a container: vzctl destroy 1017

    You can also access the container over the network as long as openssh-server is installed and enabled.  You can create user accounts and even install a GUI desktop environment (XFCE for example) which you can connect to with a remoting protocol (x2go for example).

    You can treat your container just like a server / virtual machine.

Resource Management

    OpenVZ has two resource management styles; One is fine grain control with 20 or so settings (see /proc/userbeancounters on the container host and/or within the container), and the other (vswap) is much easier to use / understand with two settings, ram and swap.  The vzctl set parameter is used DYNAMICALLY to configure / reconfigure resources.  By dynamic I mean you DO NOT have to restart the container for the resource setting to change / take affect.  Here are the three most common examples using the vswap style:

    vzctl set 1017 --disksize 20G --save
    vzctl set 1017 --ram 2G --save
    vzctl set 1017 --swap 1G --save

Processes view from within the container and from the container host

    Note the output of pstree -nup from within the container and from the container host view.  As you can see, a container has its own pid namespace but from the view of the container host, a container is nothing more than a grouping of processes with its own init system (systemd, etc).

From within the container:
systemd(1)─┬─systemd-journal(27)
           ├─irqbalance(56)───{gmain}(61)
           ├─alsactl(57)
           ├─dbus-daemon(60,dbus)
           ├─firewalld(63)───{gmain}(213)
           ├─rngd(64)
           ├─x2gocleansessio(81)
           ├─systemd-logind(86)
           ├─systemd-network(104,systemd-network)
           ├─NetworkManager(105)─┬─{gmain}(123)
           │                     ├─{gdbus}(125)
           │                     └─dhclient(227)
           ├─systemd-resolve(127,systemd-resolve)
           ├─atd(144)
           ├─agetty(148)
           ├─agetty(149)
           ├─agetty(150)
           ├─agetty(151)
           ├─agetty(152)
           ├─polkitd(192,polkitd)─┬─{gmain}(209)
           │                      ├─{gdbus}(210)
           │                      ├─{JS GC Helper}(216)
           │                      ├─{JS Sour~ Thread}(220)
           │                      └─{polkitd}(223)
           ├─crond(1177)
           ├─gssproxy(3697)─┬─{gssproxy}(3698)
           │                ├─{gssproxy}(3699)
           │                ├─{gssproxy}(3700)
           │                ├─{gssproxy}(3701)
           │                └─{gssproxy}(3702)
           ├─sshd(5896)
           └─sssd(16352)─┬─sssd_be(16353)
                         └─sssd_nss(16354)

From the container host:
| (host init, kernel threads, and other host processes)
|
|-systemd(13953)-+-sssd(3635)-+-sssd_be(3636)
|                |            `-sssd_nss(3637)
|                |-anacron(11071)
|                |-systemd-journal(13990)
|                |-irqbalance(14030)---{irqbalance}(14044)
|                |-alsactl(14031)
|                |-dbus-daemon(14034,dbus)
|                |-firewalld(14055)---{firewalld}(14284)
|                |-rngd(14056)
|                |-x2gocleansessio(14086)
|                |-systemd-logind(14100)
|                |-systemd-network(14152,systemd-network)
|                |-NetworkManager(14153)-+-{NetworkManager}(14175)
|                |                       |-{NetworkManager}(14177)
|                |                       `-dhclient(14307)
|                |-systemd-resolve(14179,systemd-resolve)
|                |-atd(14196)
|                |-agetty(14200)
|                |-agetty(14201)
|                |-agetty(14202)
|                |-agetty(14203)
|                |-agetty(14204)
|                |-polkitd(14255,lightdm)-+-{polkitd}(14280)
|                |                        |-{polkitd}(14281)
|                |                        |-{polkitd}(14287)
|                |                        |-{polkitd}(14291)
|                |                        `-{polkitd}(14294)
|                |-crond(16040)
|                |-gssproxy(20641)-+-{gssproxy}(20642)
|                |                 |-{gssproxy}(20643)
|                |                 |-{gssproxy}(20644)
|                |                 |-{gssproxy}(20645)
|                |                 `-{gssproxy}(20646)
|                `-sshd(24040)
|
| (other containers with their process trees)

Why are system containers better than full blown VMs?

    Since containers use less resources, you can fit more of them on a physical host.  As an experiment, I created 1,000 containers on a physical server that had 32GB of RAM.  For details see my somewhat dated blog post on the subject.  It is hard to imagine running more than a few dozen VMs on a host with 32GB of RAM.  There are certain use cases where VMs are better suited... you can run different OSes (not just Linux), you can run different kernels, you can load modules and use kernel-specific features on a per VM basis.  Containers just don't offer that level of flexibility.  Pluses and minuses.
}}
# Virtualization: App Containers [Homework 8] {{
System Containers were fairly easy to understand... they are very much like virtual machines but with some limitations... implemented as isolated and resource constrained groups of processes under a shared kernel.

Application containers are a bit more vague.  One way to understand Application Containers is to examine the concept of Microservices.  A complex software solution may be made up of a number of individual software components that are configured to work together (aka integrated).  A web application is often a combination of HTML, client-side Javascript, server-side PHP (or other scripting language), database backend for application data as well as user authentication.

Packaging and deploying a complex software solution as a monolitic stack that ran on a single server made a lot of sense (really, the only way to do it) when it was only used by small, medium and large-sized businesses with a customer base under a few tens of thousands.  Then the Internet happened and web-based businesses found themselves wanting to scale to much larger customer bases... often with unpredictable spikes.  A monolithic software stack just is not capable of scaling individual components as demand increases and bottlenecks appear and often break. Different components in a stack may scale differently.

For large-scale applications the service oriented architecture (SOA) was developed with microservices being a key component.  Basically, if a database is a bottleneck, create a cluster of databases that grows and shrinks on-demand to meet the ever changing load.  Application containers are the technology that has enabled the SOA.  Each instance within a fleet of services is a microservice.

Pets vs. Cattle (apologies to vegans)

VMs and system containers are often seen as pets... individual and unique entities that you care about by providing continued care and maintenance.  Application containers are seen more as cattle... ie their numbers will grow and shrink.  Have too many, destroy what you don't need.  Have too few, create more.

Docker

One thing Docker brought to the table when it was introduced in 2013 was speed.

As witnessed in class, creating a VM is faster than setting up a physical system... AND... creating a system container was much faster than creating a VM.  Creating an application container is much faster than creating a system container.

Once a container image is built and available, a Docker application container can be created and started in a sub-second.  This is accomplished by using a shared, read-only base image and creating a scratch space to store changes that may or may not need to be retained and being able to combine the read-only and scratch space into a cohesive filesystem by using a union filesystem approach aka layering.  Since application containers often do not need persistent storage, the step of creating a new disk / filesystem of significant size for each application container has been eliminated.  Also an individual service (say a web server or a database server) is less processes to start up than a full system greatly improving startup time.

Docker Marketing

Docker came from a platform-as-a-service company (dotCloud) that used all proprietary software and with the popularization of application containers, morphed into the open source company Docker, Inc.  Another element that lead to Docker's mindshare success was the fact that they came up with a good way to explain it... a giant container ship on the ocean... with an application container being one of the storage containers.  Load them up, move them around, they are all the same.  Package your application/service into a container and it is now a standardized thing that can be easily and consistently replicated and deployed.  There is (almost) no difference when running a single container on a developers machine and running a fleet of them in a clustered datacenter

Hands-on (Homework 8)
Docker is a fairly complex thing and we aren't going to master it in a single, fairly short lecture... but we can install it and create a container and play with it... and understand some of the concepts.  For various reasons, Red Hat has been sponsoring the development of Docker compatible alternatives.  These include podman, buildah, skopeo, CRI-O... with their own enterprise class PaaS system named OpenShift.  Both Docker and Red Hat's alternative tools are available for CentOS.  We are going to use podman for the hands-on.  Want a coloring book on Red Hat's application container line-up?

Goals:
     1) Install podman
     2) Use the sample podman Container file and build a custom image based on the base AlmaLinux 8 image
     3) Create a container from the image we built
     4) Get a basic understanding of the application container life-cycle

Installing podman on AlmaLinux 8
     dnf install podman --refresh

Download the podman example from the course server (from your student VM)
     scp $username@csci351.cs.montana.edu:/public/podman-example.tar.xz .
     tar -xvJf podman-example.tar.xz ; cd podman-example

Build a custom container image using the Container file
     podman build -t a8systemd .
     (when done you can verify the image is there)
     podman images

Create a container from the custom image
     podman run -d --name c8 -p 16180:80 localhost/a8systemd
     podman ps

Test it out (change port to your port)
     links http://localhost:16180

Additional podman flags:
    podman images (shows images)
    podman start $name (starts a container)
    podman stop $name (stops a container)
    podman kill $name (kills a container)
    podman rm $name (removes container)
    podman rmi $imagename (deletes an image)
    podman commit $name $newname (writes delta disk to new image)

When done, copy /public/homework8.txt over to /root/HOMEWORK/ on your student VM.
}}
# Virtualization: Future of Virtualization, VDI? {{
Hopefully what you have learned about virtualization for servers has lead you to wonder how virtualization could be leveraged for desktops.

    Client-side Hypervisors

What is a client-side hypervisor? It is basically the software you need to run virtual machines built into the computer via firmware (or a minimal system on local storage) so you can boot up a laptop or a desktop and pick from a list of local or even possibly remote VM images.

One of the main problems with operating systems are those pesky drivers. Getting an older OS to work on newer hardware or a newer OS to work on ancient hardware can sometimes be challenging. The hardware layer abstraction that is offered by virtualization could really come in handy for desktops and laptops.

Imagine storing a VM image in a central repository and then checking it out to run on whatever hardware you have no matter where you are. You would still be able to create and manage your own files / documents and then sync them back to the image repository when convenient.  Unfortunately the small number of client-side hypervisors products that have come out thus far have not been very successful in the marketplace.  Pain-points include noticeably degraded performance for multi-media and 3D applications.  The industry hasn't given up on client-side hypervisors and assume performance and adoption will improve in the not-too-distant future.

     VDI *WITHOUT* Client-side Hypervisor

 As a result, the dominant VDI solutions do not allow for offline use... and basically run everything in the datacenter.  VMs are accessed via remoting protocols.  There are pluses and minuses to that approach.  Want a GPU in your VM?  Doesn't matter that your local desktop or laptop has one, the server has to have one.  Originally there was a 1-to-1 ratio between GPU and GPU-user but that has gotten better with multi-GPU cards and drivers GPUs across multiple VMs.  The most successful product currently on the market is VMware Horizon... but it is very expensive.  Because of licensing costs, VDI does not save money over physical machines... but cost models can almost always be manipulated to say whatever you want.

    VDI and DaaS (Desktop as a Service)

Imagine being able to use a thin-client device, a desktop, laptop, or mobile device to stream one or more VMs over a local area network, WAN, or broadband connection regardless of where you are. A number of remote desktop protocols have been created / enhanced to provide as close to a "local machine" experience as possible. These include:

    Citrix's ICA with the HDX extension
    VMware's PCoverIP
    Microsoft's RDP with RemoteFX (requires physical GPUs)
    Red Hat's SPICE
    nComputing's UXP
    Virtual Bridge's VERDE
    No Machine's NX (v3 Linux-only server, v4 for Linux, Win, Mac)
    x2go (a fork of NX v3)
    Wayland has RDP built-in (almost)

Of course regular desktop computers can run remote desktop protocols as well as thin-client software. One such is VDI Blaster by Devon IT.
It remains to be seen how well VDI will work out and if it is truly the future of the desktop computing platform.
Will VDI and DaaS be cheaper than traditional desktops?  Brian Madden has written quite a bit about how cost models can be easily manipulated to make them say whatever you want. The consensus seems to be (regardless of what the product vendors claim) that currently, self-hosted VDI (over fast LANs) is more expensive mainly because server hardware is more costly than commodity desktop / laptop systems... along with the considerable licensing costs for commercial VDI solutions.   Large providers like Amazon may be able to provide budget pricing but how well will it work over existing network connections when a large number of desktops are are being streamed?
Unfortunately the bulk of the OS code has been written assuming a local, physical machine with high performance components and LAN resources at higher speeds.  A lot of the performance issues and the requirements for bolt-on products to provide functions like persistent storage of user customization, data and documents, access to USB devices, printing, etc... may be solved if and when OS makers enhance their offerings with VDI / DaaS targeted features.
Lastly there is also a vision of the future where a device the size of a smartphone can be used to completely replace desktop and laptop systems by docking the smaller devices to traditional screens, keyboard and mouse.  There is also the possibility of new input device technology that mimics the functionality of larger screens, keyboard and mouse but with a much smaller form factor.  We'll just have to wait and see how it all pans out.
In 2014 a number of commercial DaaS sprang up.  VMware has an offering as does Amazon.
}}
}}
