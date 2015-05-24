# Links
##What are Links and Why Should I Care?
Without links Inode are associated with one directory entry at a time.
With links, you can access the same inode with more than one entry.
Why whould someone want to do this?
Lets say your root partition is running out of space and you really want to instsall Libre office.
You link a root folder to your home folder in another partition and install Libre Office in your home folder. 

#code 
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
