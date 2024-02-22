# 
## basic
a short course from [Introduction to the Linux shell](https://genomeinfo.github.io/2024-02-22-QIMR-Berghofer/)

pwd: where you are
* `ls --help|less`
* `ls -F`
* `ls -R`
* `ls -l -h`: long with human readable 
* `rm \rm a`: delete file a
* `cp a b`: copy file a to b and rename
* `mv a b`: move file a to b, rename if they are in the same folder 
* `rm -r a/` recursively delete folder a
* `mkdir a/b/c`: a b must exist
* `mkdir a/b/c`
* `rmdir -p a/b/c` a and b must not contain other files

nano a: (create and) edit file a
touch a: create file a 

## Piples and Filters
* `wc a.txt`: word count
* `wc -l *.pdb`
* `wc -l *pdb > length.txt`: create a `length.txt` to store wc information
