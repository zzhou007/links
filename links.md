# Links
###What is This?
This is a page all about links.
###What are Links and Why Should I Care?
Without links Inode are associated with one directory entry at a time.
With links, you can access the same inode with more than one entry.
Why whould someone want to do this?
It allows organization of the filesystem in amazing ways.

###Whats the Difference Between Hard and Soft Links?
Hard links share the same inode while soft links have sepperate inodes.
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
The problem is that these forms of storage can only sync what is in their folders.
This is where symbolic links are useful.

####How?

```
ln -s ~/Doccuments/essays ~/Dropbox
```

Here we are creating a soft link of the folder called essays into the dropbox folder. 
If the cloud provider you are using does not support symbolic links, simply type the following:

```
cd ~
mv Documents/essays Dropbox
ln -s Dropbox/essays Documents
```

Instead of syncing the symbolic link to the file, we can sync the actual file and we have a symbolic link to our documents folder.

####Why?
Using this method has numerious advantages over just copying the files you want to sync over.
First off, it allows us to keep the changes we make in that folder up to date so we wouldn't have to keep recopying the contents. 
It will keep our folder structure. 
In our essays folder, we can seperate the essays by class and dropbox will copy the structure for us.
We can backup important files without changing where our files are on our computer.

###Accessing files in a different partition
Using linux in general requires a lot of backing up and it is far more time effecient to keep files on a different partition.

####How?
Assuming you have a seperate partition with all of your important data and you named the partition Data, 
all you have to do is run the folling commands:

```
ln -fsn /media/Data/Documents ~/
ln -fsn /media/Data/Pictures ~/
ln -fsn /media/Data/Videos ~/
```

As long as you have your partition called data mounted in /media, you can created a link to the folder in your home directory.
This command replaces your Documents, Pictures and Videos folder in your directory with a soft link. 
You can access and change the files in the folders as long as the partition is mounted. 

####Why?
Why do all the extra work to access some files on another partition?
This allows you to keep all of your previous data from before you moved to linux so you wouldn't have to redownload all this data again. 
If you duo boot, you can access the same files from both OS's saving a large amount of space. 
If you break your linux install, you can simply reinstall linux without deleting all of your files. 

###Fixing Compatability issues
Not only can you link to files and folders but you can also link to executables and execute the executable with a link.

####How?
####Why?

###Organization with Links
Being able to access the same file in multiple files makes organization far easier. 

####How?
We will now be creating a hardlink of a picture for another directory

```
ln ../Family/12352162.png .
```

####Why?


#Intresting Facts
###Why Can We not Hard Link Directories and What Happens When We Try?
###How the mv and rm command works
Rm just unlinks the file but does not overwrite the data. 
As long as you are in the same filesystem, mv just creates a hard link and removes the previous directory entry. 
This allows for faster reorganization without actually changing the data at all. 


