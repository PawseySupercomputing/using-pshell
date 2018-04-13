---
title: "Moving and managing data on the command line"
teaching: 5
exercises: 10
questions:
- "How do I move data around?"
objectives:
- "Understand how to download, upload and delete data."
keypoints:
- "get is the command used to download data from Pawsey Data Storage to your local machine"
- "put is the command used to upload data from your local machine to Pawsey Data Storage"
---

**Exercise 1 - pshell with Pawsey account**

Perform the following:

run pshell and login to the mediaflux server,
query what your logged in identity is,
display your current working directory on the server,
display your local working directory
list the contents of the remote directory on the server.

**Solution to Exercise 1**
```
iblis:~> ./pshell
Reading default config from bundle...
 === pshell: type 'help' for a list of commands ===
pawsey:offline>login
Username: sean
Password:
pawsey:/projects>
```

```
pawsey:/projects>whoami
actor = ivec:sean
  role = ivec
  role = user
```
```
pawsey:/projects>pwd
Remote: /projects
```
```
pawsey:/projects>lpwd
Local: /Users/sean
pawsey:/projects>ls
2 items, 29 items per page, remote folder: /projects
[Folder] DMF-TEST
[Folder] Data Team
```
---
**Exercise 2 - downloading data**

Perform the following:

Navigate to the /projects/Data Team folder,
download the testfiles folder to your local machine,
check the download by listing the files locally.

**Solution to exercise 2**
```
pawsey:/projects>cd Data Team/
Remote: /projects/Data Team
pawsey:/projects/Data Team>get testfiles
Total files=31, transferring ...
Progress=100%, rate=0.5 MB/s  Completed.
```
```
pawsey:/projects/Data Team>lls testfiles
Local folder: /Users/sean/testfiles
 17.02 KB | i000765.jpg
 17.59 KB | i000766.jpg
 17.21 KB | i000767.jpg
 19.09 KB | i000768.jpg
etc
```
---
**Exercise 3 - uploading data**

Perform the following:

Navigate to the /projects/Demo folder
create a unique new folder (eg your Pawsey account name)
change into this unique folder and confirm it is your current working directory
upload the files you downloaded in the previous exercise
check the upload by listing the remote files.

**Solution to exercise 3**
```
iblis:~> ./pshell
Reading config [/Users/sean/.mf_config]
 === pshell: type 'help' for a list of commands ===
pawsey:/projects>cd Demo/
Remote: /projects/Demo
pawsey:/projects/Demo>mkdir sean
pawsey:/projects/Demo>cd sean
Remote: /projects/Demo/sean
pawsey:/projects/Demo/sean>lcd testfiles
Local: /Users/sean/testfiles
pawsey:/projects/Demo/sean>put *
Total files=31, transferring...
Progress: 100% at 0.5 MB/s  Completed.
```
```
pawsey:/projects/Demo/sean>ls
31 items, 29 items per page, remote folder: /projects/Demo/sean
 69776130   | online  |  17.69 KB | i000771.jpg
 69776131   | online  |  17.02 KB | i000765.jpg
 69776132   | online  |  17.21 KB | i000767.jpg
etc
```
---
**Exercise 4 - deleting data**

Perform the following:

Navigate to the folder where you uploaded files in the previous exercise,
use a filter to display files with 077 in the filename,
delete files that match that pattern.

**Solution exercise 4**
```
iblis:~> python pshell
Reading config [/Users/sean/.mf_config]
 === pshell: type 'help' for a list of commands ===
pawsey:/projects>cd Demo/sean/
Remote: /projects/Demo/sean
pawsey:/projects/Demo/sean>ls *077*
4 items, 29 items per page, remote folder: /projects/Demo/sean
 69776130   | online  |  17.69 KB | i000771.jpg
 69776135   | online  |  18.96 KB | i000770.jpg
 69776136   | online  |  17.58 KB | i000772.jpg
 69776138   | online  |  16.62 KB | i000773.jpg
Page 1 of 1, file filter ['*077*']: q
pawsey:/projects/Demo/sean>rm *077*
Remove 4 files: (y/n) y
```

-----

**Using pshell on Pawsey HPC**

The following link provides examples of pshell scripting to run on Pawsey HPC.  For example, creating a slurm script 
for submitting a data transfer job using pshell on magnus 

```[pshell scripting](https://support.pawsey.org.au/documentation/display/US/pshell+scripting+and+HPC)```
