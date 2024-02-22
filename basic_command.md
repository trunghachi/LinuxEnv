# Introduction to the Linux shell
## Working With Files and Directories
### How can I move around on my computer?
### How can I see what files and directories I have?
### How can I specify the location of a file or directory on my computer?
### How can I create, copy, and delete files and directories?
### How can I edit files?

a short course from [Introduction to the Linux shell](https://genomeinfo.github.io/2024-02-22-QIMR-Berghofer/)

* `Ctrl+R`: reverse search in history 
* `history`: history of all command lines
* `pwd`: where you are
* `>`: create or overwrite
* `>>': create or append
* `ls --help|less`: using with /search_word
* `ls -F`:
* `ls -R`:
* `ls -l -h`: long with human-readable 
* `rm \rm a`: delete file a
* `cp a b`: copy file a to b and rename
* `mv a b`: move file a to b, rename if they are in the same folder 
* `rm -r a/` recursively delete folder a
* `mkdir a/b/c`: a b must exist
* `mkdir a/b/c`
* `rmdir -p a/b/c` a and b must not contain other files

* `nano a`: (create and) edit file a
* `touch a`: create file a
* `vim a`: create file a
* `cat a`: show the content of file a

## Piples and Filters
* `wc a.txt`: word count
* `wc -l *.pdb`: count the words of all files with the extension .pdb
* `wc -l *pdb > length.txt`: create a `length.txt` to store wc information
* `sort length.txt`: sort (not numerical)
* `sort -n length.txt`: number sort
* `sort -n length.txt length.sort.txt`
* `echo hello`* 
* `echo hello > a_file.txt`
* `wc -l *.pdb | sort -n > sorted.txt`
* `head -n 1 sorted.txt`:
* `tail -n 3 sorted.txt`:
* `wc --total=never -l *.pdb |sort -n -r | head -1 >longest`

* `cut -d , -f 2 animals.csv`
* `cut -f 2 | -d animals.csv`
* `cut  -d , -f 2 animals.csv`
* `head -4 animals.csv | tail -1`
* `sed -n '4p' animals.csv`
* `cut -f 2 animals.csv | sort | uniq`
* `cut -d \t -f 2 animals.csv | sort | uniq`


* `head -n 5 *`
* `for filename in basilisk.dat unicorn.dat minotaur.dat; echo $filename; do head -n 2 | tail -n 1; done`
* `for t in 0 1 2 3 4 5 6 7 8 9; do echo $t; done`
* `for t in {0..9}; do echo $t; done`

