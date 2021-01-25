## 01/22/2021
#Exercises Day 02

*1) Log into the Cluster
```sh
lyka@LAPTOP-GFGCMDB6 MINGW64 ~
$ ssh kconf001@turing.hpc.odu.edu
kconf001@turing.hpc.odu.edu's password:
Last login: Fri Jan 22 10:12:23 2021 from ip70-160-48-140.hr.hr.cox.net
```

*2) Make directory in course workspace called data
```sh
[kconf001@turing1 ~]$ cd /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC
[kconf001@turing1 KristinaC]$ ls
groundrules.txt  KristinaC_Exercise1.txt  scripts
[kconf001@turing1 KristinaC]$ mkdir data
[kconf001@turing1 KristinaC]$ ls
data  groundrules.txt  KristinaC_Exercise1.txt  scripts
```
 
*3) Make directory called exercises in data directory
```sh
[kconf001@turing1 KristinaC]$ cd data/
[kconf001@turing1 data]$ mkdir exercises
[kconf001@turing1 data]$ ls
exercises 
[kconf001@turing1 exercises]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/exercises  
```

*4) Execute pwd command & start a log of commands 
with a header for today's date in README.md github logfile in local workspace
```sh
lyka@LAPTOP-GFGCMDB6 MINGW64 ~
$ pwd        
/c/Users/lyka
lyka@LAPTOP-GFGCMDB6 MINGW64 ~
$ cd Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis/
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis (main)
$ ls                                                                                                                             
21sp_advgenomics/
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis (main)
$ pwd 
/c/Users/lyka/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis 
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis (main)
$ mkdir 21SpKristinaCAdvancedGenomicsLog
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis
$ ls
21sp_advgenomics/  21SpKristinaCAdvancedGenomicsLog/
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis
$ cd ./21SpKristinaCAdvancedGenomicsLog
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis/21SpKristinaCAdvancedGenomicsLog (main)
$ nano     
```

*With nano command, README.md file is created with Exercise 02 Header & logfile.
Logfile is filled at the end of each part of the exercises completed.

*5) Copy the Exercise2.fasta.gz and Exercise2.fastq.tar.gz files into your course exercises directory 
from the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day02 directory
```sh
[kconf001@turing1 exercises]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day02/Exercise2.fast* ./
[kconf001@turing1 exercises]$ ls
Exercise2.fasta.gz  Exercise2.fastq.tar.gz
[kconf001@turing1 exercises]$ ls -alh
total 13M 
drwxrwxrwx 2 kconf001 users   76 Jan 22 14:25 .
drwxrwxrwx 3 kconf001 users   27 Jan 22 13:25 ..
-rwxr-xr-x 1 kconf001 users 4.3M Jan 22 14:25 Exercise2.fasta.gz
-rwxr-xr-x 1 kconf001 users 4.3M Jan 22 14:25 Exercise2.fastq.tar.gz 
```

*6) Unzip & untar the files
```sh
[kconf001@turing1 exercises]$ gunzip -c Exercise2.fasta.gz > Exercise2.fasta
[kconf001@turing1 exercises]$ ls
Exercise2.fasta  Exercise2.fasta.gz  Exercise2.fastq.tar.g
[kconf001@turing1 exercises]$ ls -alh
total 37M
drwxrwxrwx 2 kconf001 users  109 Jan 22 14:26 .
drwxrwxrwx 3 kconf001 users   27 Jan 22 13:25 ..
-rwxrwxrwx 1 kconf001 users  17M Jan 22 14:26 Exercise2.fasta
-rwxr-xr-x 1 kconf001 users 4.3M Jan 22 14:25 Exercise2.fasta.gz
-rwxr-xr-x 1 kconf001 users 4.3M Jan 22 14:25 Exercise2.fastq.tar.gz
[kconf001@turing1 exercises]$ tar -zxvf Exercise2.fastq.tar.gz
Exercise2.fastq
[kconf001@turing1 exercises]$ ls -alh
total 62M
drwxrwxrwx 2 kconf001 users  109 Jan 22 14:26 .                                                                   
drwxrwxrwx 3 kconf001 users   27 Jan 22 13:25 .. 
-rwxrwxrwx 1 kconf001 users  17M Jan 22 14:26 Exercise2.fasta                                                     
-rwxr-xr-x 1 kconf001 users 4.3M Jan 22 14:25 Exercise2.fasta.gz
-rw-r--r-- 1 kconf001 users  18M Sep  2  2015 Exercise2.fastq                                                 
-rwxr-xr-x 1 kconf001 users 4.3M Jan 22 14:25 Exercise2.fastq.tar.gz 
[kconf001@turing1 exercises]$ pwd 
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/exercises                    
[kconf001@turing1 exercises]$ ls                      
Exercise2.fasta  Exercise2.fasta.gz  Exercise2.fastq  Exercise2.fastq.tar.gz
```

*7) Add commands to notebook file (see above)

*8) Calculate how many sequences are in each file
Fasta file: Sequences start with '>'
Fastq file: Sequences start with '@'; Each fastq read includes 4 lines.
First line- Identifier
Second line- Sequence
Third line- Blank line (starts with +, sometimes have the same description as first line)
Fourth line- Quality for each base in Sequence (Second line)
grep -c = Used to find patterns (find a string in a file or string)
Can also divide total lines by 4 to find total sequence reads

```sh 
[kconf001@turing1 exercises]$ head -1 Exercise2.fasta
>scaffold10078|size20675
[kconf001@turing1 exercises]$ grep -c '>' Exercise2.fasta
138
[kconf001@turing1 exercises]$ head -1 Exercise2.fastq
@HS3:541:HAYTUADXX:1:1101:1297:1938 1:N:0:AGTTCC
[kconf001@turing1 exercises]$ grep -c '@HS3' Exercise2.fastq
61304
[kconf001@turing1 exercises]$ wc Exercise2.fastq
245216   306520 18459769 Exercise2.fastq
[kconf001@turing1 exercises]$ echo 245216/4 | bc -l
61304.00000000000000000000  
```

*9) Copy the python file from the /cm/shared/courses/dbarshis/21AdvGenomics/scripts directory 
into the class scripts directory
```sh
[kconf001@turing1 exercises]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/avg_cov_len_fasta_advbioinf.py ../../scripts/
[kconf001@turing1 exercises]$ cd ../
[kconf001@turing1 data]$ cd ../
[kconf001@turing1 KristinaC]$ cd scripts/
[kconf001@turing1 scripts]$ ls
avg_cov_len_fasta_advbioinf.py
```

*10) Start interactive compute session and re-navigate to exercises directory
```sh
[kconf001@turing1 scripts]$ cd ../
[kconf001@turing1 KristinaC]$ cd data/
[kconf001@turing1 data]$ cd exercises/
[kconf001@turing1 exercises]$ salloc
salloc: Pending job allocation 9269144
salloc: job 9269144 queued and waiting for resources
salloc: job 9269144 has been allocated resources
salloc: Granted job allocation 9269517
This session will be terminated in 7 days. If your application requires
a longer excution time, please use command "salloc -t N-0" where N is the
number of days that you need.
[kconf001@coreV1-22-016 exercises]$
```

*11) Run the python script on the Exercise2.fasta file 
by typing the path to the script followed by the Exercise2.fasta file name
```sh
[kconf001@coreV1-22-016 exercises]$ ../../scripts/avg_cov_len_fasta_advbioinf.py Exercise2.fasta
The total number of sequences is 138
The average sequence length is 126640
The total number of bases is 17476447
The minimum sequence length is 1122
The maximum sequence length is 562680
The N50 is 187037
Median Length = 92612
contigs < 150bp = 0
contigs >= 500bp = 138
contigs >= 1000bp = 138
contigs >= 2000bp = 135
[kconf001@coreV1-22-016 exercises]$ exit
logout
salloc: Relinquishing job allocation 9269517
```

*12) Add all parts to notebook README.md file including the results of the script
See above

*13) Push notebook file to github page
```sh
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis/21SpKristinaCAdvancedGenomicsLog (main)                                                                                                                  
$ git add README.md
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis/21SpKristinaCAdvancedGenomicsLog (main)
$ git commit -m 'updating readme'
[main c32c255] updating readme
1 file changed, 161 insertions(+), 4 deletions(-)
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis/21SpKristinaCAdvancedGenomicsLog (main)
$ git push -u origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 2.11 KiB | 2.11 MiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/kconf001/21SpKristinaCAdvancedGenomicsLog.git
d677019..c32c255  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```
