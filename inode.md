#Inodes
###What are Inodes?
Files do not directly linked to data block. 
Instead they link to inodes.
Inodes or index nodes is a file structior of a file system 
Every unix system uses inodes except Solaris.
Thses inodes contain info about the corresponding file such as:
mode/permissioni,
owner id group id, 
size of file,
number of hard links to the file,
time last accessed and modified,
the time the inode was last modified,
the data block number,
and the inode number. 
Inodes are around 128 bytes of data
![Alt text](pictures/inode_ex.jpg?raw=true)

#Data Blocks
(next slide)
data blocks in unix are around 1024 bytes
when you type ls -l it displays the total block used. 

(next side)
data block as you can figure out stores data.
if you want to store data less than or equal to 1024 bytes it takes up one block.

(next slide)
the amount of blocks it takes up is the amount of data you want to store divided by 1024 bytes rounded to the nearest block
so if you want to store 1025 bytes you use 2 blocks.

(next slide)
storing data in block can cause fragmenttation. 
as you can see there is a green file, a blue file and a red file. now the user wants to delete the blue file and store a pink file

(next slide)
the pink file takes up more than one block so it stores the data 
in the space of the delete blue block a pink block is store but there is not enough room so the system appends the rest of the blocks at the end,
This is known as fragmentation.
with a revolving platter hard  drive, the magnetic needle has to move to the place the block is stored slowing data transfer leading to fragmentation.

(next slide)
to fix this the system regularly degragments grouping the data blocks of the same files together speding up readind
with the introduction of solid state drives with no moving parts, you no longer need to degrag

(next slide)
lets have a final example of inodes. 
in this picture, a test file foo.txt is pointing to indo 1234 which is in turn pointing to the data block containing the string hello word.
cs100 is a directory and it also has a inode numbered 2345
inode 2356 contains a file bar.txt pointing to  inode 3456
and indoe 3456 is pointing to a data block containg the string goodbye world.

(end recording)

