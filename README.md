# Links
##What are Links and Why Should I Care?
Without links Inode are associated with one directory entry at a time.
With links, you can access the same inode with more than one entry.
Why whould someone want to do this?
Lets say your root partition is running out of space and you really want to instsall Libre office.
You link a root folder to your home folder in another partition and install Libre Office in your home folder. 

##Whats the Difference Between Hard and Soft Links?
The main difference is soft links makes a new inode while hard links share the same inode.
Click [Here](www.youtube.com/watch?v=j_BgOf2Ti-s) to watch a video about inodes.
#Code 
Dont want to read pages of test?
Click [Here](https://www.youtube.com/watch?v=LPIMLR4simU) to watch a simplified video about the basics of links.
##Creating Links
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
##Removing Links
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
* is not recursive
* cannt remove directories
* cannt handle less than one element ie 'unlink file1 file2' will not work
* has less sanity checking

#Flags
##--backup -b

>ln --backup file1 file2

If file 2 exists the flag will 
* create a backup of file 2 named file2~.
* create a link for file1 called file2

##-d -F --directory
lets super user create a hard link to a dir 

>ln -d dir link

It almost never works just use soft links instead

##-f
Say you want to make a link of file called file2 and oh no!
`ln: failed to create hard link ‘file2’: File exists`
Instead of typing `rm file2` an entire 8 characters type `-f` instead.
`-f` is the force flag.

>ln -f file file2

Makes a link to file even if file2 exists.
If file2 exists removes file2.

##-n  
