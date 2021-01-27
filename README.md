## 01/22/2021
#Exercises Day 02

* 1. Log into the Cluster
```sh
lyka@LAPTOP-GFGCMDB6 MINGW64 ~
$ ssh kconf001@turing.hpc.odu.edu
kconf001@turing.hpc.odu.edu's password:
Last login: Fri Jan 22 10:12:23 2021 from ip70-160-48-140.hr.hr.cox.net
```

* 2. Make directory in course workspace called data
```sh
[kconf001@turing1 ~]$ cd /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC
[kconf001@turing1 KristinaC]$ ls
groundrules.txt  KristinaC_Exercise1.txt  scripts
[kconf001@turing1 KristinaC]$ mkdir data
[kconf001@turing1 KristinaC]$ ls
data  groundrules.txt  KristinaC_Exercise1.txt  scripts
```
 
* 3. Make directory called exercises in data directory
```sh
[kconf001@turing1 KristinaC]$ cd data/
[kconf001@turing1 data]$ mkdir exercises
[kconf001@turing1 data]$ ls
exercises 
[kconf001@turing1 exercises]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/exercises  
```

* 4. Execute pwd command & start a log of commands 
* with a header for today's date in README.md github logfile in local workspace
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

* With nano command, README.md file is created with Exercise 02 Header & logfile.
* Logfile is filled at the end of each part of the exercises completed.

* 5. Copy the Exercise2.fasta.gz and Exercise2.fastq.tar.gz files into your course exercises directory 
* from the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day02 directory
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

* 6. Unzip & untar the files
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

* 7. Add commands to notebook file (see above)

* 8. Calculate how many sequences are in each file
* Fasta file: Sequences start with '>'
* Fastq file: Sequences start with '@'; Each fastq read includes 4 lines.
* First line- Identifier
* Second line- Sequence
* Third line- Blank line (starts with +, sometimes have the same description as first line)
* Fourth line- Quality for each base in Sequence (Second line)
* grep -c = Used to find patterns (find a string in a file or string)
* Can also divide total lines by 4 to find total sequence reads

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

* 9. Copy the python file from the /cm/shared/courses/dbarshis/21AdvGenomics/scripts directory 
* into the class scripts directory
```sh
[kconf001@turing1 exercises]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/avg_cov_len_fasta_advbioinf.py ../../scripts/
[kconf001@turing1 exercises]$ cd ../
[kconf001@turing1 data]$ cd ../
[kconf001@turing1 KristinaC]$ cd scripts/
[kconf001@turing1 scripts]$ ls
avg_cov_len_fasta_advbioinf.py
```

* 10. Start interactive compute session and re-navigate to exercises directory
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

* 11. Run the python script on the Exercise2.fasta file 
* by typing the path to the script followed by the Exercise2.fasta file name
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

* 12. Add all parts to notebook README.md file including the results of the script
* See above

* 13. Push notebook file to github page
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
## 01/27/2021                                                                                                                      
# Homework Day 02 (continuation of Exercise 02) 
* 1. Make sure logged into turing node & in personal data directory. 
* Also input salloc command (see previous day for details).

* Write an sbatch script to cp the files 
* /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/originalfastqs/ 
* into your own data directory
* Can use nano or scp

```sh
#!/bin/bash -l
#SBATCH -o KristinaCCopylane01.txt
#SBATCH -n 1
#SBATCH --mail-user=kconf001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KristinaCCopylane01
cp /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/originalfastqs/HADB01*.fastq.gz /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/
```

* 2. Add sbatch script to data directory (see above)
```sh
nano method (in turing cluster)
[kconf001@coreV2-25-072 data] nano KristinaCCopy1.sh 
```

```sh
scp method (in local directory files)
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis 
$ nano KristinaCCopy1.sh
$ scp KristinaCCopylane01.sh kconf001@turing.hpc.odu.edu:/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/
kconf001@turing.hpc.odu.edu's password:
KristinaCCopylane01.sh                                                                           100%  341     8.7KB/s   00:00

Input sbatch script into .sh file
```

* 3. Submit slurm script (sbatch KristinaCCopyl.sh) and verify that it's working (squeue -u kconf001 and/or ls -alh)

```sh
[kconf001@coreV2-25-072 data] $ sbatch KristinaCCopy1.sh
Submitted batch job 9270444
[kconf001@coreV2-25-072 data] $ squeue -u kconf001
JOBID   PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)  
9270470      main Kristina kconf001  R      17:25      1 coreV2-25-072  
9270444      main       sh kconf001  R      01:25      1 coreV2-25-072
```
* 4. Document in README.md / github notebook (see #13 in previous day)

* 5. Write sbatch script to gunzip all the fastaq.gz files once copying is finished.
```sh
Nano method
#!/bin/bash -l
#SBATCH -o KristinaCCopylane01.txt
#SBATCH -n 1
#SBATCH --mail-user=kconf001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KristinaCGunZiplane01
gunzip ./*fastq.gz
```
* Verify that it is working
```sh
[kconf001@coreV2-25-072 data] $ squeue -u kconf001
JOBID   PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
9270470      main Kristina kconf001  R      17:25      1 coreV2-25-072                                                                                                                               
9270462      main       sh kconf001  R      25:25      1 coreV2-25-072

[kconf001@coreV2-25-072 data]$ ls -alh
total 58G 
drwxrwxrwx 3 kconf001 users  1017 Jan 27 14:37 . 
drwxrwxrwx 4 kconf001 users   121 Jan 22 11:31 .. 
drwxrwxrwx 2 kconf001 users   142 Jan 25 09:57 exercises
-rw-r--r-- 1 kconf001 users  2.6G Jan 27 13:29 HADB01-A_S17_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users  3.4G Jan 27 13:30 HADB01-B_S18_L002_R1_001.fastq  
-rw-r--r-- 1 kconf001 users  981M Jan 27 13:30 HADB01-C_S19_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users  1.2G Jan 27 13:30 HADB01-D_S20_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users   13M Jan 27 13:30 HADB01-E_S21_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users  4.7G Jan 27 13:30 HADB01-F_S22_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users  3.6G Jan 27 13:31 HADB01-G_S23_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users  4.0G Jan 27 13:32 HADB01-H_S24_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users  4.6G Jan 27 13:34 HADB01-I_S25_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users  3.6G Jan 27 13:35 HADB01-J_S26_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users  4.0G Jan 27 13:37 HADB01-K_S27_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users  4.0G Jan 27 13:37 HADB01-L_S28_L002_R1_001.fastq
-rw------- 1 kconf001 users  1.2G Jan 27 14:37 HADB01-M_S29_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users  657M Jan 27 13:38 HADB01-M_S29_L002_R1_001.fastq.gz 
-rw-r--r-- 1 kconf001 users  671M Jan 27 13:39 HADB01-N_S30_L002_R1_001.fastq.gz
-rw-r--r-- 1 kconf001 users 1000M Jan 27 13:40 HADB01-O_S31_L002_R1_001.fastq.gz
-rw-r--r-- 1 kconf001 users  538M Jan 27 13:40 HADB01-P_S32_L002_R1_001.fastq.gz
-rwxrwxrwx 1 kconf001 users     0 Jan 27 13:29 KristinaCCopylane01.txt
-rwxrwxrwx 1 kconf001 users   189 Jan 27 13:49 KristinaCGunZiplane01.sh
-rwxrwxrwx 1 kconf001 users     0 Jan 27 13:52 KristinaCGunZiplane01.txt
-rwxrwxrwx 1 kconf001 users   341 Jan 27 13:20 KristinaCLane01.sh
```

* 6. Push updated README.md log to github page (see #13 in previous day).

## 01/27/2021
# Day 03 Homework

* 1. cp the /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03 directory & files to personal sandbox
```sh
[kconf001@coreV2-25-072 data]$ cd ../
[kconf001@coreV2-25-072 KristinaC]$  cp -r /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03/ ./ ls
[kconf001@coreV2-25-072 KristinaC]$ ls
data  day03  groundrules.txt  KristinaC_Exercise1.txt  scripts
```

* 2. Make a new fastq directory (mkdir fastq) in directory and move (mv) all the .fastq files into the fastq directory
Make sure all files have finished gunzipping (ls -alh)
```sh
[kconf001@coreV2-25-072 KristinaC]$ cd data
[kconf001@coreV2-25-072 data]$ mkdir fastq
[kconf001@coreV2-25-072 data]$ pwd                                                                                   
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data
[kconf001@coreV2-25-072 data]$ ls -alh                                                                               
total 79G
drwxrwxrwx 4 kconf001 users  980 Jan 27 14:52 .
drwxrwxrwx 5 kconf001 users  144 Jan 27 14:49 ..
drwxrwxrwx 2 kconf001 users  142 Jan 25 09:57 exercises
drwxrwxrwx 2 kconf001 users    0 Jan 27 14:50 fastq
-rw-r--r-- 1 kconf001 users 2.6G Jan 27 13:29 HADB01-A_S17_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users 3.4G Jan 27 13:30 HADB01-B_S18_L002_R1_001.fastq
-rw-r--r-- 1 kconf001 users 981M Jan 27 13:30 HADB01-C_S19_L002_R1_001.fastq             
-rw-r--r-- 1 kconf001 users 1.2G Jan 27 13:30 HADB01-D_S20_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users  13M Jan 27 13:30 HADB01-E_S21_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 4.7G Jan 27 13:30 HADB01-F_S22_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 3.6G Jan 27 13:31 HADB01-G_S23_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 4.0G Jan 27 13:32 HADB01-H_S24_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 4.6G Jan 27 13:34 HADB01-I_S25_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 3.6G Jan 27 13:35 HADB01-J_S26_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 4.0G Jan 27 13:37 HADB01-K_S27_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 4.0G Jan 27 13:37 HADB01-L_S28_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 4.4G Jan 27 13:38 HADB01-M_S29_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 4.4G Jan 27 13:39 HADB01-N_S30_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 6.7G Jan 27 13:40 HADB01-O_S31_L002_R1_001.fastq                                         
-rw-r--r-- 1 kconf001 users 3.6G Jan 27 13:40 HADB01-P_S32_L002_R1_001.fastq                                         
-rwxrwxrwx 1 kconf001 users    0 Jan 27 13:29 KristinaCCopylane01.txt                                                
-rwxrwxrwx 1 kconf001 users  189 Jan 27 13:49 KristinaCGunZiplane01.sh                                               
-rwxrwxrwx 1 kconf001 users    0 Jan 27 13:52 KristinaCGunZiplane01.txt                                              
-rwxrwxrwx 1 kconf001 users  341 Jan 27 13:20 KristinaCLane01.sh   
[kconf001@coreV2-25-072 data]$ mv *.fastq ./fastq/
[kconf001@coreV2-25-072 data]$ ls
exercises  fastq  KristinaCCopylane01.txt  KristinaCGunZiplane01.sh  KristinaCGunZiplane01.txt  KristinaCLane01.sh
```

* 3. cp the renamingtable_complete.txt from the day03 directory into your fastq directory 
* and the /cm/shared/courses/dbarshis/21AdvGenomics/scripts/renamer_advbioinf.py script into your sandbox scripts folder 
* and less the new script and check out the usage statement.

```sh
cp the renamingtable_complete.txt from the day03 directory into your fastq directory 
[kconf001@coreV2-25-072 data]$ cp ../day03/renamingtable_complete.txt ./fastq/
[kconf001@coreV2-25-072 data]$ cd fastq/
[kconf001@coreV2-25-072 fastq]$ ls
HADB01-A_S17_L002_R1_001.fastq  HADB01-G_S23_L002_R1_001.fastq  HADB01-M_S29_L002_R1_001.fastq
HADB01-B_S18_L002_R1_001.fastq  HADB01-H_S24_L002_R1_001.fastq  HADB01-N_S30_L002_R1_001.fastq
HADB01-C_S19_L002_R1_001.fastq  HADB01-I_S25_L002_R1_001.fastq  HADB01-O_S31_L002_R1_001.fastq
HADB01-D_S20_L002_R1_001.fastq  HADB01-J_S26_L002_R1_001.fastq  HADB01-P_S32_L002_R1_001.fastq
HADB01-E_S21_L002_R1_001.fastq  HADB01-K_S27_L002_R1_001.fastq  renamingtable_complete.txt
HADB01-F_S22_L002_R1_001.fastq  HADB01-L_S28_L002_R1_001.fastq
```

```sh
cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/renamer_advbioinf.py script into your sandbox scripts folder
[kconf001@coreV2-25-072 data]$ cd ../../
[kconf001@coreV2-25-072 KristinaC]$ ls                                                                               
data  day03  groundrules.txt  KristinaC_Exercise1.txt  scripts                                                       
[kconf001@coreV2-25-072 KristinaC]$ cd scripts/
[kconf001@coreV2-25-072 scripts]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/renamer_advbioinf.py  /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/scripts/
[kconf001@coreV2-25-072 scripts]$ ls 
avg_cov_len_fasta_advbioinf.py  renamer_advbioinf.py
```

```sh
less new script (head) & read usage statement)
[kconf001@coreV2-25-072 scripts]$ head renamer_advbioinf.py 
#!/usr/bin/env python 
####usage renamer.py renamingtable 
#### this script take the entries in the first column of table and renames (mv's) them to files with the names in the second column 
import sys 
import os
fin=open(sys.argv[1],'r')
linecount=0
for line in fin:
linecount+=1
```
