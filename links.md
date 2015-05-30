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
You can not hard link directories.
Go [here](inode.md) to learn more about inodes and data blocks.

#Examples
###Creating Links
Before we get to the fun stuff lets first go over how to make a link.
We can make hard links simply with the `ln` command and soft links with an optional `-s` flag.
The format is 

```
ln [optional flags] file1 link1
```

or

```
ln [optional flags] /path/to/file1 /path/to/link1
```

Simple right?

###Syncing Entire Folders to Dropbox
Dropbox and other cloud storage are great at keeping backups of our important files.
The problem is they can only sync what is in their folders.
This is where symbolic links are useful.

####How?

```
ln -s ~/Doccuments/essays ~/Dropbox
```

Here we are creating a soft link of the folder called essays into the dropbox folder. 
If the cloud provider you are using does not suppert symbolic links simply do.

```
cd ~
mv Documents/essays Dropbox
ln -s Dropbox/essays Documents
```

Instead of syncing the smbolic link to the file, we sync the actual file and we have a symbolic link our documents folder.

####Why?
Using this method has numerious advantages over just copying the files you want to sync over.
First off, it allows us to keep the changes we make in that folder up to date so we wouldn't have to keep recopying the contents. 
It will keep our folder structure. 
In our essays folder, we can seperate the essays by class and dropbox will copy the structure for us.
We can backup important files without where our files are on our computer.

###Accessing files in a different partition
Switching using linux in general requires lots of backing up and it is far more time effecient to keep files on a different partition.

####How?
First created a new partition and move over any file that is important.
Learn about partitioning here:
[Windows](https://technet.microsoft.com/en-us/magazine/gg309170.aspx) 
[Linux](http://computernetworkingnotes.com/file-system-administration/how-to-create-partition-using-fdisk.html) 
[Mac](https://support.apple.com/en-us/HT204009).
Now lets link our files to our home folder

```
ln -fsn /Data/Documents ~/
ln -fsn /Data/Pictures ~/
ln -fsn /Data/Videos ~/
```

###Fixing Compatability issues

###Organization with Links

#Intresting Cases
###Why Can We not Dard Link Directories and What Happends When We Try?
