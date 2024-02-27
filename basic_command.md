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


# From Prakathi
#AWK , grep, sed, cat basics

#To remove a col and print op as tab delimited
`awk ‘BEGIN{OFS= “\t”}!($1=” ”)’ ip.txt > op.txt`   # ($1 is the col to be removed)

#To split a col into sub cols : 
`cat ip.txt | awk ‘{split($1,a,”_”); printf(“%s\t%s\t%s\t%s\t%s\t%s\n”, a[1],a[2],a[3],a[4],a[5], $2);}’ > op.txt`

#( before: 1_1234_C_T_ENS4000_4
#After: 1	1234	C	T	ENS4000	4	)

#To convert row to col (transpose)
`awk ‘{for (i=1;i<=NF;i++) print $i}’ ip > op`

#Or 
`awk ‘BEGIN{OFS= “\n”}{for (i=1;i<=NR;i++) print $i}’ ip > op`

#To paste 1,2column of a file to 3rdcol of same file
`awk 'BEGIN{FS="\t"; OFS="\t"} {$3=$1"\:"$2; print}' ip  | awk '!/#/ {print }' > op`

#To replace new line with space or tab:
`tr ‘\n’ ‘\t’ <ip > op  === (‘ ‘ for space)`

#To count lines in a file
`wc -l filename`

#To sort a file based on col1
`sort -u -k 1 ip > op`

#Sort decending order on col 3 (g considers exponential values while using n does not)
`sort -rg -t $'\t' -k3,3 ip > op`

#To insert line in 1st line of file
`sed -i '1i\first_line_text' ip`

#To delete 2nd and 3rd row in a file
`sed '2,3d' ip > op`

#To remove excess space bw cols
`sed -E ‘s /[ ][ ]+/\\t /g’ ip > op`

#To match words from f1 in f2
`grep -wFf f1 f2 > op`

#To print only SNPs from SV file
`awk ‘length($4)==1 && /rs/ {print } ip > op`

#(/**/ - To print all lines having the specifies text , Since indels are also named as rs###, column four (length of allele) is 1 for SNPs and can be filtered)

#To add ‘chr’ to col1 of a file
`sed ‘s/^/chr/’ ip > op`

#To replace rsID column with dot
`sed -i "/^[^#]/s/rs[0-9]\+/./g" ip > op`

#To add a column with the same value in all rows
`nawk '$1=(FNR FS $1)'  ip > op`      # FNR=22 to add 22 in all rows


#To print col1 if col 2 satisfies a criterion
`awk ‘$2 < 0.5 {print $1}’ ip > op`

#To print variants within a specified coordinate
`awk ‘$2>1000 && $2<2000 {print $3 }’ ip.vcf > SNP.txt`

#To replace a word in a file with another
 `sed -i ‘s/originalword/newword/g’ ip> op`

#To replace 3rd col in a file with file2-col1
`awk 'NR==FNR{a[NR]=$1;next} {$3=a[FNR]}1' OFS="\t" test2.txt test1.txt`

#To count no. of columns in a tab separated file
`awk -F'\t' '{print NF; exit}' ip`

#To add “ ” for every field separated by space
`awk '{for (i=1;i<=NF;i++) $i="\""$i"\""}1' FS=" " OFS=" " input > op`

#To add comma after each field
`awk '{for(i=1;i<NF;i++)if(i!=NF){$i=$i","}  }1' ip > op`

#To convert csv to tab delimited
 `sed 's/\,/\t/g' ip > op`

#Print lines If entry in a column is not equal to a non-numeric char
`awk '{if ($5!="\-") print }' ip> op`

#(if col 5 is  not eql to -)
`awk '$5!~"\-" {print }' ip > op`

#To download all files in a link
`wget -A gz -m -p -E -k -K -np link (-A accept file type of gz or jpg or pdf)`

#Awk with compressed files
`awk '{ ... }' <(gzip -dc ip.file.gz) | gzip > op.file.gz`
#or 
`zcat file.gz | awk '{...}' > op`

#To print ranges of consequitive positions in a list
`awk '   function output() { print start (prev == start ? "" : ","prev) }
	NR == 2 {start = prev = $2; next}
	$2 > prev+1 {output(); start = $2}
	{prev = $2}
	END {output()} ' tastemultiannochrpos.txt | awk '/,/ {print }' > consequitivepos.txt`

#To swap 1st 2 cols
`awk '{ t = $1; $1 = $2; $2 = t; print; }' ip > op`

#To remove first two columns in a file:
`cut -d " " -f 3- input_filename > output_filename`

#Extract .bz2 files
`bunzip2 ip`

#Extract tar.bz2
`Tar -xf ip`

#To delete 0bytes files
`Find -size 0 -type f -delete`
