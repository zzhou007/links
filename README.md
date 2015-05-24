# Links
##What are Links and Why Should I Care?
Without links Inode are associated with one directory entry at a time.
With links, you can access the same inode with more than one entry.
Why whould someone want to do this?
Lets say your root partition is running out of space and you really want to instsall Libre office.
You link a root folder to your home folder in another partition and install Libre Office in your home folder. 

#code 
##creating links
So how whould I go about making these wonderful links?
You can make hard links simply with the ln command.
The format is 

>ln file1 link1

or

>ln /path/to/file1 /path/to/link1

Just make sure the file exists and the link does not exits.
The command creates a hard link to file1.

Soft links are exactly the same except with a '-s' flag.

>ln -s file link

or

>ln -s /path/to/file1 /path/to/link1

Soft links can link across file systems and to directories.
##removing links
Say you typed 'ln file1 lnik' instead of 'ln file1 link1'.
To delete links, you can use

>rm lnik

or 

>unlink lnik 

Because files are directory entries associated with a Inode, you can use unlink to delete files.
So whats the difference between the two?
![alt text](https://i.imgur.com/gsgJbDa.png?1)
Notice how unlink is slightly faster than rm.
That is because unlink has less fetures than rm.
unlink:
*is not recursive
*cannt remove directories
*cannt handle less than one element ie 'unlink file1 file2' will not work
*has less sanity checking

