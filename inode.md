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
Inodes are around 128 bytes of data.
###Example
![Alt text](pictures/inode_ex.jpg?raw=true)
add explnation here~!!

#Data Blocks
Data blocks in unix are 1024 bytes.
Data block as you can figure out stores data.
If you want to store data less than or equal to 1024 bytes it takes up one block.
The amount of blocks it takes up is the amount of data you want to store divided by 1024 bytes rounded to the nearest block.
so if you want to store 1025 bytes you use 2 blocks.
###Fragmentation
Storing data in block can cause fragmenttation. 
![Alt test](pictures/frag_1.jpg?raw=true)
As you can see there is a green file, a blue file and a red file. now the user wants to delete the blue file and store a pink file

![Alt test](pictures/frag_2.jpg?raw=true)
The pink file takes up more than one block so it stores the data 
in the space of the delete blue block a pink block is store but there is not enough room so the system appends the rest of the blocks at the end,
This is known as fragmentation.
with a revolving platter hard  drive, the magnetic needle has to move to the place the block is stored slowing data transfer leading to fragmentation.

![Alt test](pictures/frag_3.jpg?raw=true)
To fix this the system regularly degragments grouping the data blocks of the same files together speding up reading.
Because SSDs don't have moving parts you do not need to defrag them.

#Practical Uses
So now that you have this knowlage how can you use it?
###Restoring deleted files
Because the `rm` command does not overwrite any data and just deletes the node, 
we can restore data deleted.



