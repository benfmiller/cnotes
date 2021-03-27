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

# Commands used {{

mimeopen {filename}
//opens file with prefered program, -a asks which program, -d asks and sets default

hexdump
//pipe echo into it and get hex chars

## System {{

ps -edf
// shows details of running processes

ss -tupln
// shows listening ports, may require sudo

ufw allow {port}/{protocol}
// allows port through firewall, may require sudo

ping {ip-address} -t
// -t pings only
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

chmod +xs {filename}
//set setgit bit

which {command}
// prints aliases, functions, or destination of executable

id {user, optional}
prints details about current user or details about user given

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

}}
# Services {{
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

select * from {table}
//display everything in table

\# CREATE TABLE demo(t text);
\# COPY demo from '[FILENAME]';
\# SELECT * FROM demo;
\# DROP TABLE demo;


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
}}
