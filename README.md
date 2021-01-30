# 01/22/2021
## Exercises Day 02

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

* 4. Execute pwd command & start a log of commands with a header for today's date in README.md github logfile in local workspace
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
# 01/27/2021                                                                                                                      
## Homework Day 02 (continuation of Exercise 02) 
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
920444      main       sh kconf001  R      01:25      1 coreV2-25-072
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

# 01/27/2021
## Homework Day 03

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
less (head) new script
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

* 4. Run renamer_advbioinf.py script in fastq folter using renamingtable_complete.txt as practice & verify output to screen by hand.
```sh
lyka@LAPTOP-GFGCMDB6 MINGW64 ~                                                                                                             
$ ssh kconf001@turing.hpc.odu.edu  
kconf001@turing.hpc.odu.edu's password:                                                                         
Last login: Wed Jan 27 15:37:12 2021 from ip70-160-48-140.hr.hr.cox.net
[kconf001@turing1 ~]$ cd /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/fastq/
[kconf001@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/fastq
[kconf001@turing1 fastq]$ ../../scripts/renamer_advbioinf.py renamingtable_complete.txt
mv HADB01-A_S17_L002_R1_001.fastq VA_W_01_14.fastq
mv HADB01-B_S18_L002_R1_001.fastq VA_B_01_14.fastq
mv HADB01-C_S19_L002_R1_001.fastq RI_W_01_14.fastq
mv HADB01-D_S20_L002_R1_001.fastq RI_B_01_14.fastq
mv HADB01-E_S21_L002_R1_001.fastq VA_W_01_22.fastq
mv HADB01-F_S22_L002_R1_001.fastq VA_B_01_22.fastq
mv HADB01-G_S23_L002_R1_001.fastq RI_W_01_22.fastq
mv HADB01-H_S24_L002_R1_001.fastq RI_B_01_22.fastq
mv HADB01-I_S25_L002_R1_001.fastq VA_W_01_18.fastq
mv HADB01-J_S26_L002_R1_001.fastq VA_B_01_18.fastq
mv HADB01-K_S27_L002_R1_001.fastq RI_W_01_18.fastq
mv HADB01-L_S28_L002_R1_001.fastq RI_B_01_18.fastq
mv HADB01-M_S29_L002_R1_001.fastq VA_W_08_SNP.fastq
mv HADB01-N_S30_L002_R1_001.fastq VA_B_09_SNP.fastq
mv HADB01-O_S31_L002_R1_001.fastq RI_W_08_SNP.fastq
mv HADB01-P_S32_L002_R1_001.fastq RI_B_08_SNP.fastq
mv HADB02-A_S33_L003_R1_001.fastq VA_W_02_14.fastq
mv HADB02-B_S34_L003_R1_001.fastq VA_B_02_14.fastq
mv HADB02-C_S35_L003_R1_001.fastq RI_W_02_14.fastq
mv HADB02-D_S36_L003_R1_001.fastq RI_B_02_14.fastq
mv HADB02-E_S37_L003_R1_001.fastq VA_W_02_22.fastq
mv HADB02-F_S38_L003_R1_001.fastq VA_B_02_22.fastq
mv HADB02-G_S39_L003_R1_001.fastq RI_W_02_22.fastq
mv HADB02-H_S40_L003_R1_001.fastq RI_B_02_22.fastq
mv HADB02-I_S41_L003_R1_001.fastq VA_W_02_18.fastq
mv HADB02-J_S42_L003_R1_001.fastq VA_B_02_18.fastq
mv HADB02-K_S43_L003_R1_001.fastq RI_W_02_18.fastq
mv HADB02-L_S44_L003_R1_001.fastq RI_B_02_18.fastq
mv HADB02-M_S45_L003_R1_001.fastq VA_W_09_SNP.fastq
mv HADB02-N_S46_L003_R1_001.fastq VA_B_08_SNP.fastq
mv HADB02-O_S47_L003_R1_001.fastq RI_W_09_SNP.fastq
mv HADB02-P_S48_L003_R1_001.fastq RI_B_09_SNP.fastq
mv HADB03-A_S49_L004_R1_001.fastq VA_W_03_14.fastq
mv HADB03-B_S50_L004_R1_001.fastq VA_B_03_14.fastq
mv HADB03-C_S51_L004_R1_001.fastq RI_W_03_14.fastq
mv HADB03-D_S52_L004_R1_001.fastq RI_B_03_14.fastq
mv HADB03-E_S53_L004_R1_001.fastq VA_W_03_22.fastq
mv HADB03-F_S54_L004_R1_001.fastq VA_B_03_22.fastq
mv HADB03-G_S55_L004_R1_001.fastq RI_W_03_22.fastq
mv HADB03-H_S56_L004_R1_001.fastq RI_B_03_22.fastq
mv HADB03-I_S57_L004_R1_001.fastq VA_W_03_18.fastq
mv HADB03-J_S58_L004_R1_001.fastq VA_B_03_18.fastq
mv HADB03-K_S59_L004_R1_001.fastq RI_W_03_18.fastq
mv HADB03-L_S60_L004_R1_001.fastq RI_B_03_18.fastq
mv HADB03-M_S61_L004_R1_001.fastq VA_W_10_SNP.fastq
mv HADB03-N_S62_L004_R1_001.fastq VA_B_10_SNP.fastq
mv HADB03-O_S63_L004_R1_001.fastq RI_W_10_SNP.fastq
mv HADB03-P_S64_L004_R1_001.fastq RI_B_10_SNP.fastq
mv HADB04-A_S65_L005_R1_001.fastq VA_W_04_14.fastq
mv HADB04-B_S66_L005_R1_001.fastq VA_B_04_14.fastq
mv HADB04-C_S67_L005_R1_001.fastq RI_W_04_14.fastq
mv HADB04-D_S68_L005_R1_001.fastq RI_B_04_14.fastq
mv HADB04-E_S69_L005_R1_001.fastq VA_W_04_22.fastq
mv HADB04-F_S70_L005_R1_001.fastq VA_B_04_22.fastq
mv HADB04-G_S71_L005_R1_001.fastq RI_W_04_22.fastq
mv HADB04-H_S72_L005_R1_001.fastq RI_B_04_22.fastq
mv HADB04-I_S73_L005_R1_001.fastq VA_W_04_18.fastq
mv HADB04-J_S74_L005_R1_001.fastq VA_B_04_18.fastq
mv HADB04-K_S75_L005_R1_001.fastq RI_W_04_18.fastq
mv HADB04-L_S76_L005_R1_001.fastq RI_B_04_18.fastq
mv HADB04-M_S77_L005_R1_001.fastq VA_W_05_14.fastq
mv HADB04-N_S78_L005_R1_001.fastq VA_B_05_14.fastq
mv HADB04-O_S79_L005_R1_001.fastq RI_W_05_14.fastq
mv HADB04-P_S80_L005_R1_001.fastq RI_B_05_14.fastq
mv HADB05-A_S81_L006_R1_001.fastq VA_W_05_22.fastq
mv HADB05-B_S82_L006_R1_001.fastq VA_B_05_22.fastq
mv HADB05-C_S83_L006_R1_001.fastq RI_W_05_22.fastq
mv HADB05-D_S84_L006_R1_001.fastq RI_B_05_22.fastq
mv HADB05-E_S85_L006_R1_001.fastq VA_W_05_18.fastq
mv HADB05-F_S86_L006_R1_001.fastq VA_B_05_18.fastq
mv HADB05-G_S87_L006_R1_001.fastq RI_W_05_18.fastq
mv HADB05-H_S88_L006_R1_001.fastq RI_B_05_18.fastq
mv HADB05-I_S89_L006_R1_001.fastq VA_W_06_14.fastq
mv HADB05-J_S90_L006_R1_001.fastq VA_B_06_14.fastq
mv HADB05-K_S91_L006_R1_001.fastq RI_W_06_14.fastq
mv HADB05-L_S92_L006_R1_001.fastq RI_B_06_14.fastq
mv HADB05-M_S93_L006_R1_001.fastq VA_W_06_22.fastq
mv HADB05-N_S94_L006_R1_001.fastq VA_B_06_22.fastq
mv HADB05-O_S95_L006_R1_001.fastq RI_W_06_22.fastq
mv HADB05-P_S96_L006_R1_001.fastq RI_B_06_22.fastq
mv HADB06-A_S97_L007_R1_001.fastq VA_W_06_18.fastq
mv HADB06-B_S98_L007_R1_001.fastq VA_B_06_18.fastq
mv HADB06-C_S99_L007_R1_001.fastq RI_W_06_18.fastq
mv HADB06-D_S100_L007_R1_001.fastq RI_B_06_18.fastq
mv HADB06-E_S101_L007_R1_001.fastq VA_W_07_14.fastq
mv HADB06-F_S102_L007_R1_001.fastq VA_B_07_14.fastq
mv HADB06-G_S103_L007_R1_001.fastq RI_W_07_14.fastq
mv HADB06-H_S104_L007_R1_001.fastq RI_B_07_14.fastq
mv HADB06-I_S105_L007_R1_001.fastq VA_W_07_22.fastq
mv HADB06-J_S106_L007_R1_001.fastq VA_B_07_22.fastq
mv HADB06-K_S107_L007_R1_001.fastq RI_W_07_22.fastq
mv HADB06-L_S108_L007_R1_001.fastq RI_B_07_22.fastq
mv HADB06-M_S109_L007_R1_001.fastq VA_W_07_18.fastq
mv HADB06-N_S110_L007_R1_001.fastq VA_B_07_18.fastq
mv HADB06-O_S111_L007_R1_001.fastq RI_W_07_18.fastq
mv HADB06-P_S112_L007_R1_001.fastq RI_B_07_18.fastq
```

* 5. Uncomment (remove the #) in renaming python script thaht starts with os.open and comment out the print line
```sh
[kconf001@turing1 fastq]$ pwd 
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/fastq
[kconf001@turing1 fastq]$ nano ../../scripts/renamer_advbioinf.py
#!/usr/bin/env python
####usage renamer.py renamingtable
#### this script take the entries in the first column of table and renames (mv's) them to files with the names in the second column
import sys
import os
linecount+=1
if linecount>=2:
cols=line.rstrip().split('\t')
#print 'mv %s %s' %(cols[0], cols[1])
os.popen('mv %s %s' %(cols[0], cols[1]))
```

* 6. Write sbatch script & submit it to rename all the .fastq files according to renaming table using renamer python script
```sh
[kconf001@turing1 fastq]$ nano KristinaCRenamer.sh
[kconf001@turing1 fastq]$ ls
HADB01-A_S17_L002_R1_001.fastq  HADB01-D_S20_L002_R1_001.fastq  HADB01-G_S23_L002_R1_001.fastq  HADB01-J_S26_L002_R1_001.fastq  HADB01-M_S29_L002_R1_001.fastq  HADB01-P_S32_L002_R1_001.fastq
HADB01-B_S18_L002_R1_001.fastq  HADB01-E_S21_L002_R1_001.fastq  HADB01-H_S24_L002_R1_001.fastq  HADB01-K_S27_L002_R1_001.fastq  HADB01-N_S30_L002_R1_001.fastq  KristinaCRenamer.sh
HADB01-C_S19_L002_R1_001.fastq  HADB01-F_S22_L002_R1_001.fastq  HADB01-I_S25_L002_R1_001.fastq  HADB01-L_S28_L002_R1_001.fastq  HADB01-O_S31_L002_R1_001.fastq  renamingtable_complete.txt
[kconf001@turing1 fastq]$ salloc
salloc: Pending job allocation 9270528
salloc: job 9270528 queued and waiting for resources 
salloc: job 9270528 has been allocated resources 
salloc: Granted job allocation 9270528
[kconf001@coreV2-25-072 fastq]$ cat KristinaCRenamer.sh 
#!/bin/bash -l 
#SBATCH -o KristinaCRenamer.txt
#SBATCH -n 1
#SBATCH --mail-user=kconf001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KristinaCRenamerFastq
[kconf001@coreV2-25-072 fastq]$ sbatch ./KristinaCRenamer.sh
Submitted batch job 9270529
[kconf001@coreV2-25-072 fastq]$ squeue -u kconf001
JOBID   PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
9270529      main Kristina kconf001 PD       0:00      1 (Priority)
9270528      main       sh kconf001  R       0:29      1 coreV2-25-072
Once job is done running: checking to see if renaming is completed. 
[kconf001@coreV2-25-072 fastq]$ ls -alh
total 79G
drwxrwxrwx 2 kconf001 users  667 Jan 27 16:02 .
drwxrwxrwx 4 kconf001 users  212 Jan 27 14:59 ..
-rwxrwxrwx 1 kconf001 users  226 Jan 27 16:00 KristinaCRenamer.sh
-rwxrwxrwx 1 kconf001 users  11K Jan 27 16:02 KristinaCRenamer.txt
-rwxr-xr-x 1 kconf001 users 4.6K Jan 27 15:00 renamingtable_complete.txt
-rw-r--r-- 1 kconf001 users 1.2G Jan 27 13:30 RI_B_01_14.fastq
-rw-r--r-- 1 kconf001 users 4.0G Jan 27 13:37 RI_B_01_18.fastq
-rw-r--r-- 1 kconf001 users 4.0G Jan 27 13:32 RI_B_01_22.fastq
-rw-r--r-- 1 kconf001 users 3.6G Jan 27 13:40 RI_B_08_SNP.fastq
-rw-r--r-- 1 kconf001 users 981M Jan 27 13:30 RI_W_01_14.fastq
-rw-r--r-- 1 kconf001 users 4.0G Jan 27 13:37 RI_W_01_18.fastq 
-rw-r--r-- 1 kconf001 users 3.6G Jan 27 13:31 RI_W_01_22.fastq
-rw-r--r-- 1 kconf001 users 6.7G Jan 27 13:40 RI_W_08_SNP.fastq
-rw-r--r-- 1 kconf001 users 3.4G Jan 27 13:30 VA_B_01_14.fastq
-rw-r--r-- 1 kconf001 users 3.6G Jan 27 13:35 VA_B_01_18.fastq
-rw-r--r-- 1 kconf001 users 4.7G Jan 27 13:30 VA_B_01_22.fastq
-rw-r--r-- 1 kconf001 users 4.4G Jan 27 13:39 VA_B_09_SNP.fastq
-rw-r--r-- 1 kconf001 users 2.6G Jan 27 13:29 VA_W_01_14.fastq
-rw-r--r-- 1 kconf001 users 4.6G Jan 27 13:34 VA_W_01_18.fastq
-rw-r--r-- 1 kconf001 users  13M Jan 27 13:30 VA_W_01_22.fastq
-rw-r--r-- 1 kconf001 users 4.4G Jan 27 13:38 VA_W_08_SNP.fastq      
```

* 7. Update github (see #13 on Exercises Day 02 for similar workflow)
```sh
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis/21SpKristinaCAdvancedGenomicsLog (main)
$ git add README.md
warning: LF will be replaced by CRLF in README.md.
The file will have its original line endings in your working directory
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis/21SpKristinaCAdvancedGenomicsLog (main)
$ git commit -m 'updating readme'
[main 964b72c] updating readme
1 file changed, 235 insertions(+), 2 deletions(-)
lyka@LAPTOP-GFGCMDB6 MINGW64 ~/Desktop/Files/ODU/ODUSPRING2021/AdvanceGenomicsAnalysis/21SpKristinaCAdvancedGenomicsLog (main)
$ git push -u origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done. 
Writing objects: 100% (3/3), 2.99 KiB | 2.99 MiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/kconf001/21SpKristinaCAdvancedGenomicsLog.git  
b869eb3..964b72c  main -> main 
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

* 8. Naming convention:
* SOURCEPOPULATION_SYMBIOTICSTATE_GENOTYPE_TEMPERATURE.fastq
* There are 2 sources: Virginia and Rhode Island
* There are 2 symbiotic states: Brown and White

* 9. Start process of adapter clipping & quality trimming all the renamed .fastq files in batches, by lane.

* 10. cp script /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Trimclipfilterstatsbatch_advbioinf.py into your scripts directory.

```sh
[kconf001@coreV2-25-072 fastq]$ exit
logout
salloc: Relinquishing job allocation 9270528
[kconf001@turing1 fastq]$ cd ../../
[kconf001@turing1 KristinaC]$ ls
data  day03  groundrules.txt  KristinaC_Exercise1.txt  scripts
[kconf001@turing1 KristinaC]$ cd scripts/
[kconf001@turing1 scripts]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/scripts
[kconf001@turing1 scripts]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Trimclipfilterstatsbatch_advbioinf.py /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/scripts
avg_cov_len_fasta_advbioinf.py  renamer_advbioinf.py  Trimclipfilterstatsbatch_advbioinf.py
```

* 11. less/head new script & check the usage statement
```sh
[kconf001@turing1 scripts]$ ls
avg_cov_len_fasta_advbioinf.py  renamer_advbioinf.py  Trimclipfilterstatsbatch_advbioinf.py
[kconf001@turing1 scripts]$ head Trimclipfilterstatsbatch_advbioinf.py
#!/usr/bin/env python
# Written by Dan Barshis
import sys, os
########### Usage #############
# Trimclipfilterstatsbatch.py barcodefile.txt anynumberoffastqfiles
# This should be run from within the folder with all of your original .fastqstrim
# Will quality trim multiple SINGLE-END fastq files
# Things to customize for your particular platform:
[kconf001@turing1 scripts]$  
```

* 12. cp /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03/adapterlist_advbioinf.txt into the working directory with your fastq files
```sh
[kconf001@turing1 scripts]$ cd ../
[kconf001@turing1 KristinaC]$ cd data/
[kconf001@turing1 data]$ cd fastq/
[kconf001@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/fastq
[kconf001@turing1 fastq]$ cp /cm/shared/courses/dbarshis/21AdvGenomics/assignments_exercises/day03/adapterlist_advbioinf.txt /cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/fastq
[kconf001@turing1 fastq]$ ls 
adapterlist_advbioinf.txt   RI_B_01_18.fastq   RI_W_01_22.fastq   VA_B_09_SNP.fastq
KristinaCRenamer.sh         RI_B_01_22.fastq   RI_W_08_SNP.fastq  VA_W_01_14.fastq
KristinaCRenamer.txt        RI_B_08_SNP.fastq  VA_B_01_14.fastq   VA_W_01_18.fastq
renamingtable_complete.txt  RI_W_01_14.fastq   VA_B_01_18.fastq   VA_W_01_22.fastq
RI_B_01_14.fastq            RI_W_01_18.fastq   VA_B_01_22.fastq   VA_W_08_SNP.fastq
```
* 13. Make sbatch script for Trimclipfilter, then script & run on fastq files

```sh

[kconf001@turing1 fastq]$ nano KristinaCTestTrimClip.sh
[kconf001@turing1 fastq]$ cat KristinaCTestTrimClip.sh

#!/bin/bash -l

#SBATCH -o KristinaCTestTrimClip.txt
#SBATCH -n 1
#SBATCH --mail-user=kconf001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KristinaCTestTrimClip
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/scripts/Trimclipfilterstatsbatch_advbioinf.py adapterlist_advbioinf.txt *.fastq

[kconf001@turing1 fastq]$ salloc
salloc: Pending job allocation 9270528 
salloc: job 9270528 queued and waiting for resources
salloc: job 9270528 has been allocated resources
salloc: Granted job allocation 9270542
[kconf001@coreV2-25-072 fastq]$ sbatch KristinaCTestTrimClip.sh
Submitted batch job 9270546
[kconf001@coreV2-25-072 fastq]$ squeue -u kconf001
JOBID   PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
9270542      main       sh kconf001  R      10:03      1 coreV2-25-072
9270546      main Kristina kconf001  R       0:03      1 coreV2-25-005
[kconf001@coreV2-25-072 fastq]$ ls -alh 
drwxrwxrwx 2 kconf001 users  872 Jan 27 17:35 . 
drwxrwxrwx 4 kconf001 users  212 Jan 27 14:59 .. 
-rwxr-xr-x 1 kconf001 users 7.7K Jan 27 16:46 adapterlist_advbioinf.txt
-rwxrwxrwx 1 kconf001 users  226 Jan 27 16:00 KristinaCRenamer.sh 
-rwxrwxrwx 1 kconf001 users  18K Jan 27 16:32 KristinaCRenamer.txt
-rwxrwxrwx 1 kconf001 users  310 Jan 27 17:26 KristinaCTestTrimClip.sh
-rwxrwxrwx 1 kconf001 users  123 Jan 27 17:22 KristinaCTestTrimClip.txt
-rwxr-xr-x 1 kconf001 users 4.6K Jan 27 15:00 renamingtable_complete.txt
-rwxrwxrwx 1 kconf001 users 959M Jan 27 17:35 RI_B_01_14_clipped.fastq 
-rw-r--r-- 1 kconf001 users 1.2G Jan 27 13:30 RI_B_01_14.fastq 
-rw-r--r-- 1 kconf001 users 4.0G Jan 27 13:37 RI_B_01_18.fastq
-rw-r--r-- 1 kconf001 users 4.0G Jan 27 13:32 RI_B_01_22.fastq 
-rw-r--r-- 1 kconf001 users 3.6G Jan 27 13:40 RI_B_08_SNP.fastq
-rw-r--r-- 1 kconf001 users 981M Jan 27 13:30 RI_W_01_14.fastq
-rw-r--r-- 1 kconf001 users 4.0G Jan 27 13:37 RI_W_01_18.fastq
-rw-r--r-- 1 kconf001 users 3.6G Jan 27 13:31 RI_W_01_22.fastq
-rw-r--r-- 1 kconf001 users 6.7G Jan 27 13:40 RI_W_08_SNP.fastq
-rwxrwxrwx 1 kconf001 users   45 Jan 27 17:27 trimclipstats.txt 
-rw-r--r-- 1 kconf001 users 3.4G Jan 27 13:30 VA_B_01_14.fastq 
-rw-r--r-- 1 kconf001 users 3.6G Jan 27 13:35 VA_B_01_18.fastq
-rw-r--r-- 1 kconf001 users 4.7G Jan 27 13:30 VA_B_01_22.fastq
-rw-r--r-- 1 kconf001 users 4.4G Jan 27 13:39 VA_B_09_SNP.fastq
-rw-r--r-- 1 kconf001 users 2.6G Jan 27 13:29 VA_W_01_14.fastq 
-rw-r--r-- 1 kconf001 users 4.6G Jan 27 13:34 VA_W_01_18.fastq
-rw-r--r-- 1 kconf001 users  13M Jan 27 13:30 VA_W_01_22.fastq
-rw-r--r-- 1 kconf001 users 4.4G Jan 27 13:38 VA_W_08_SNP.fastq 
```

* 14. Job has finished
```sh
[kconf001@turing1 fastq]$ ls -alh                                                                                                                                                                                      
total 584K                                                                                                                                                                                                             
drwxrwxrwx 5 kconf001 users  294 Jan 28 01:59 .
drwxrwxrwx 4 kconf001 users  212 Jan 27 14:59 ..
drwxrwxrwx 2 kconf001 users 2.2K Jan 28 01:59 filteringstats
-rwxrwxrwx 1 kconf001 users  226 Jan 27 16:00 KristinaCRenamer.sh
-rwxrwxrwx 1 kconf001 users  18K Jan 27 16:32 KristinaCRenamer.txt
-rwxrwxrwx 1 kconf001 users  310 Jan 27 17:26 KristinaCTestTrimClip.sh
-rwxrwxrwx 1 kconf001 users 3.8K Jan 28 01:59 KristinaCTestTrimClip.txt
drwxrwxrwx 2 kconf001 users  591 Jan 28 01:59 originalfastqs
drwxrwxrwx 2 kconf001 users  788 Jan 28 01:59 QCFastqs
-rwxr-xr-x 1 kconf001 users 4.6K Jan 27 15:00 renamingtable_complete.txt
```
* 15. Updated Github & README.md (See #7 on Homework Day 03 for similar workflow)

# 01/29/2021
## Homework Day 04

* 1. Add trimclipstats.txt output to full class datafile /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/Fulltrimclipstatstable.txt using the following steps
* 1a. Run /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py -h to examine usage

```sh
[kconf001@turing1 fastq]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py -h
Written by Peter Schafran pscha005@odu.edu 5-Oct-2015
This script takes a stats output file from fastx_clipper and converts it into a table.
Usage: Schafran_trimstatstable.py [-c, -v, -h] inputfile.txt outputfile.txt
Options (-c and -v must be listed separately to run together):
-h      Display this help message
-c      Use comma delimiter instead of tabs
-v      Verbose mode (print steps to stdout)
[kconf001@turing1 fastq]$ pwd
/cm/shared/courses/dbarshis/21AdvGenomics/sandboxes/KristinaC/data/fastq
```
* 1b. Run script on data with outputfilename YOURNAME_trimclipstatsout.txt
* Had to switch to filteringstats directory because this is where the trimclipstats.txt is located.
```sh
[kconf001@turing1 fastq]$ cd filteringstats/ 
[kconf001@turing1 filteringstats]$ /cm/shared/courses/dbarshis/21AdvGenomics/scripts/Schafran_trimstatstable_advbioinf_clippedtrimmed.py trimclipstats.txt KristinaC_trimclipstatsout.txt 
[kconf001@turing1 filteringstats]$ ls  
KristinaC_trimclipstatsout.txt        RI_B_08_SNP_clipped_trimmed_stats.txt  RI_W_01_22_nucdist.png                 VA_B_01_18_nucdist.png                 VA_W_01_14_qualbox.png 
RI_B_01_14_clipped_trimmed_stats.txt  RI_B_08_SNP_nucdist.png                RI_W_01_22_qualbox.png                 VA_B_01_18_qualbox.png                 VA_W_01_18_clipped_trimmed_stats.txt 
RI_B_01_14_nucdist.png                RI_B_08_SNP_qualbox.png                RI_W_08_SNP_clipped_trimmed_stats.txt  VA_B_01_22_clipped_trimmed_stats.txt   VA_W_01_18_nucdist.png 
RI_B_01_14_qualbox.png                RI_W_01_14_clipped_trimmed_stats.txt   RI_W_08_SNP_nucdist.png                VA_B_01_22_nucdist.png                 VA_W_01_18_qualbox.png 
RI_B_01_18_clipped_trimmed_stats.txt  RI_W_01_14_nucdist.png                 RI_W_08_SNP_qualbox.png                VA_B_01_22_qualbox.png                 VA_W_01_22_clipped_trimmed_stats.txt 
RI_B_01_18_nucdist.png                RI_W_01_14_qualbox.png                 trimclipstats.txt                      VA_B_09_SNP_clipped_trimmed_stats.txt  VA_W_01_22_nucdist.png 
RI_B_01_18_qualbox.png                RI_W_01_18_clipped_trimmed_stats.txt   VA_B_01_14_clipped_trimmed_stats.txt   VA_B_09_SNP_nucdist.png                VA_W_01_22_qualbox.png         
RI_B_01_22_clipped_trimmed_stats.txt  RI_W_01_18_nucdist.png                 VA_B_01_14_nucdist.png                 VA_B_09_SNP_qualbox.png                VA_W_08_SNP_clipped_trimmed_stats.txt 
RI_B_01_22_nucdist.png                RI_W_01_18_qualbox.png                 VA_B_01_14_qualbox.png                 VA_W_01_14_clipped_trimmed_stats.txt   VA_W_08_SNP_nucdist.png 
RI_B_01_22_qualbox.png                RI_W_01_22_clipped_trimmed_stats.txt   VA_B_01_18_clipped_trimmed_stats.txt   VA_W_01_14_nucdist.png                 VA_W_08_SNP_qualbox.png 
```
* 1c. Add KristinaC_trimclipstatsout.txt to the class file (Fulltrimclipstatstable.txt).
* check to make sure things are in the correct directory first!

```sh
[kconf001@turing1 filteringstats]$ cd /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/
[kconf001@turing1 Astrangia_poculata]$ ls -alh 
total 320K
drwxrwxrwx 4 dbarshis users  105 Jan 29 01:17 .
drwxrwxrwx 3 dbarshis users   36 Jan 21 23:36 ..
-rwxr-xr-x 1 dbarshis users  29K Jan 29 01:18 Fulltrimclipstatstable.txt 
drwxrwxrwx 2 dbarshis users 4.8K Jan 21 23:37 originalfastqs 
drwxrwxrwx 2 dbarshis users  337 Jan 29 00:52 refassembly 
[kconf001@turing1 Astrangia_poculata]$ cd /cm/shared/courses//dbarshis/21AdvGenomics/sandboxes/KristinaC/data/fastq/filteringstats/
[kconf001@turing1 filteringstats]$ salloc
salloc: Pending job allocation 9271098
salloc: job 9271098 queued and waiting for resources
salloc: job 9271098 has been allocated resources
salloc: Granted job allocation 9271098 
[kconf001@coreV2-25-072 filteringstats]$ tail -n +2 KristinaC_trimclipstatsout.txt >> /cm/shared/courses/dbarshis/21AdvGenomics/classdata/Astrangia_poculata/Fulltrimclipstatstable.txt

```
* 2. Map reads back to assembly using Bowtie2 alignment algorithm
* 3. Write sbatch (in QCFastqs directory) script to do Bowtie2/2.4 on _clippedtrimmedfiltered.fastq data files from data in personal sandbox

```sh
[kconf001@coreV2-25-072 filteringstats]$ cd ../
[kconf001@coreV2-25-072 fastq]$ cd QCFastqs/
[kconf001@coreV2-25-072 QCFastqs]$ nano KristinaCBowtieln.sh
[kconf001@coreV2-25-072 QCFastqs]$ cat KristinaCBowtieln.sh

#!/bin/bash -l

#SBATCH -o KristinaCbowtieln.txt
#SBATCH -n 1
#SBATCH --mail-user=kconf001@odu.edu
#SBATCH --mail-type=END
#SBATCH --job-name=KristinaCBowtieln

module load bowtie2/2.4
for i in *_clippedtrimmed.fastq; do bowtie2 --rg-id ${i%_clippedtrimmed.fastq} \
--rg SM:${i%_clippedtrimmed.fastq} \
--very-sensitive -x /cm/shared/courses/dbarshis/18AdvBioinf/classdata/Astrangia_poculata/refassembly/ast_hostsym -U $i \
> ${i%_clippedtrimmedfilterd.fastq}.sam; done

[kconf001@coreV2-25-072 QCFastqs]$ sbatch KristinaCBowtieln.sh 
Submitted batch job 9271110 
[kconf001@coreV2-25-072 QCFastqs]$ squeue -u kconf001 
             JOBID PARTITION     NAME     USER ST       TIME  NODES NODELIST(REASON)
           9271110      main Kristina kconf001  R       0:01      1 coreV2-25-007
           9271098      main       sh kconf001  R      35:31      1 coreV2-25-072 
```
* Job is complete; should get _clippedtrimmed.fastq.sam files
```sh
[kconf001@turing1 QCFastqs]$ ls -alh
total 184G
drwxrwxrwx 2 kconf001 users 1.7K Jan 29 21:18 .
drwxrwxrwx 5 kconf001 users  294 Jan 28 01:59 ..
-rwxrwxrwx 1 kconf001 users  470 Jan 29 15:15 KristinaCBowtieln.sh 
-rwxrwxrwx 1 kconf001 users 3.5K Jan 29 21:48 KristinaCbowtieln.txt
-rwxrwxrwx 1 kconf001 users 3.5K Jan 29 21:48 KristinaCbowtieln.txt
-rwxrwxrwx 1 kconf001 users 1.1G Jan 28 00:45 RI_B_01_14_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 1.8G Jan 29 15:25 RI_B_01_14_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 3.5G Jan 28 00:47 RI_B_01_18_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 5.7G Jan 29 15:54 RI_B_01_18_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 3.5G Jan 28 00:50 RI_B_01_22_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 5.7G Jan 29 16:23 RI_B_01_22_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 3.2G Jan 28 00:52 RI_B_08_SNP_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 5.2G Jan 29 16:51 RI_B_08_SNP_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 886M Jan 28 00:53 RI_W_01_14_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 1.4G Jan 29 16:59 RI_W_01_14_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 3.6G Jan 28 00:56 RI_W_01_18_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 5.9G Jan 29 17:29 RI_W_01_18_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 3.0G Jan 28 00:58 RI_W_01_22_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 4.9G Jan 29 17:53 RI_W_01_22_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 5.9G Jan 28 01:02 RI_W_08_SNP_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 9.7G Jan 29 18:41 RI_W_08_SNP_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 3.0G Jan 28 01:05 VA_B_01_14_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 4.9G Jan 29 19:04 VA_B_01_14_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 3.3G Jan 28 01:07 VA_B_01_18_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 5.1G Jan 29 19:25 VA_B_01_18_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 4.2G Jan 28 01:10 VA_B_01_22_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 6.9G Jan 29 19:58 VA_B_01_22_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 3.9G Jan 28 01:13 VA_B_09_SNP_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 6.5G Jan 29 20:29 VA_B_09_SNP_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 2.3G Jan 28 01:15 VA_W_01_14_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 3.7G Jan 29 20:46 VA_W_01_14_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 4.1G Jan 28 01:18 VA_W_01_18_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 6.7G Jan 29 21:18 VA_W_01_18_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users  11M Jan 28 01:18 VA_W_01_22_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users  22M Jan 29 21:18 VA_W_01_22_clippedtrimmed.fastq.sam
-rwxrwxrwx 1 kconf001 users 3.9G Jan 28 01:21 VA_W_08_SNP_clippedtrimmed.fastq
-rwxrwxrwx 1 kconf001 users 6.4G Jan 29 21:48 VA_W_08_SNP_clippedtrimmed.fastq.sam
```
* 4. Updated README.md & github (See #7 on Homework Day 03 for similar workflow)

