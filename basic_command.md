# Introduction to the Linux shell
## Working With Files and Directories
### How can I move around on my computer?
### How can I see what files and directories I have?
### How can I specify the location of a file or directory on my computer?
### How can I create, copy, and delete files and directories?
### How can I edit files?

a short course from [Introduction to the Linux shell](https://genomeinfo.github.io/2024-02-22-QIMR-Berghofer/)
* `./`: mean current directory, be careful with `rm` command and always put `./` before the directory name, especially when working on HPC.
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

Lệnh grep trong Linux là một công cụ hữu ích để tìm kiếm và thao tác với các mẫu chuỗi trong các file văn bản. Tên của nó được lấy từ lệnh ed (trình soạn thảo) g/re/p (tìm kiếm toàn cục theo biểu thức chính quy và in các dòng khớp), phản ánh chức năng cốt lõi của nó. Lệnh grep được sử dụng rộng rãi bởi các lập trình viên, quản trị viên hệ thống, và người dùng nhờ hiệu quả và đa dạng trong việc xử lý dữ liệu văn bản. Trong bài viết này, chúng tôi sẽ khám phá các khía cạnh khác nhau của lệnh grep.

Cú pháp cơ bản của lệnh grep là như sau:

`grep [options] pattern [files]`

Trong đó:

* [options]: Là các cờ dòng lệnh thay đổi hành vi của grep.
* [pattern]: Là biểu thức chính quy bạn muốn tìm kiếm.
* [files]: Là tên của các file bạn muốn tìm kiếm trong. Bạn có thể chỉ định nhiều file để tìm kiếm đồng thời.

Một số tùy chọn phổ biến của lệnh grep là:

* `-i`: Bỏ qua chữ hoa chữ thường khi tìm kiếm.
* `-v`: In ra tất cả các dòng không khớp với mẫu.
* `-n`: Hiển thị các dòng khớp và số dòng của chúng.
* `-c`: Chỉ in ra số lượng các dòng khớp với mẫu.
* `-l`: Chỉ hiển thị danh sách các tên file khớp với mẫu.
* `-w`: Chỉ khớp với các từ nguyên.
* `-o`: Chỉ in ra phần khớp của một dòng khớp, với mỗi phần trên một dòng đầu ra riêng biệt.
* `-A n`: In ra dòng khớp và n dòng sau kết quả.
* `-B n`: In ra dòng khớp và n dòng trước kết quả.
* `-C n`: In ra dòng khớp và n dòng trước và sau kết quả.
* `-E`: Xử lý mẫu như một biểu thức chính quy mở rộng (ERE).
* `-e exp`: Chỉ định biểu thức với tùy chọn này. Có thể sử dụng nhiều lần.
* `-f file`: Lấy các mẫu từ file, mỗi mẫu trên một dòng.
* `-r`: Tìm kiếm đệ quy trong thư mục.
