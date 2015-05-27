# Links
###What is This?
This is a page all about links.
###What are Links and Why Should I Care?
Without links Inode are associated with one directory entry at a time.
With links, you can access the same inode with more than one entry.
Why whould someone want to do this?
It allows organization of the filesystem in amazing ways.

###Whats the Difference Between Hard and Soft Links?
Simply hard links share the same inode while soft links have sepperate inodes.
You can create soft links across filesystems.
Hard links can only be created in the same filesystem.
Go [here](url_for_inodes.md) to learn more about inodes and data blocks.

#Examples
###Creating Links
Before we get to the fun stuff lets first go over how to make a link.
We can make hard links simply with the `ln` command and soft links with an optional `-s` flag.
The format is 

> ln [optional flags] file1 link1

or

> ln [optional flags] /path/to/file1 /path/to/link1
Simple right?



