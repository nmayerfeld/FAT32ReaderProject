# FAT32ReaderProject
class project using Java to read data from a file that uses FAT32 credit @Professor Ben Wymore for the assignment 
This is a maven project made with IntelliJ.
Compile fat32_reader.java as you would any java file, and then run with the image file as a command line argument.
This program reads the bytes in the image file once for each entry, storing the relevant information in data structures described below. 
Using this method, instead of reading lazily on demand, assumes that accessing data structure fields from memory will be faster than re-reading the bytes from the image file each time upon demand (especially considering that many commands will often be run in the same directory, so locality will dictate that many of those data structure fields will already be in cache).  This method of solving the problem also assumes that space constraints are less important than speed.
My program is based on a TreeNode class which corresponds to a directory entity.  It stores a Directory object, a name, a list of TreeNodes that are its subdirectories, and a pointer to the TreeNode of its parent Directory.
Each directory object, in addition to a name and other relevant information, stores a list of Entry objects representing the files and directories contained within it.
Whenever each directory is first accessed when the program is run and commands are executed, the program calls a readEntries method, which reads the bytes representing each entry in the directory, interprets them correctly, creates and adds a corresponding entry to the directory, and, if the entry is itself a directory, a TreeNode is created for it and is added to the list of subdirectories of the current directory.
