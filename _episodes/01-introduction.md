---
title: "Introduction"
teaching: 5
exercises: 0
questions:
- "What is pshell"
objectives:
- "Understand the key pshell commands"
- "Understand that Pawsey uses Mediaflux for storage management."
keypoints:
- "Pawsey Supercomputing Centre manages very large storage facilities for researchers"
- "These facilities have specialised access tools"
- "pshell is a tool (written in Python 2.7) for interacting with the storage system"
- "Pawsey also maintains web based access for light workloads and data sharing"
---
Pshell is a python command line client that implements a subset of the standard SFTP commands.

*Remote filesystem commands [pawsey]:*
- cd (Change the current remote folder)
- ls (List files stored on the remote server)         
- pwd (Display the current remote folder)
- mkdir (Create a remote folder)
- rmdir (Remove a remote folder)

*Local filesystem commands [your computer]:*
- lcd (Change local folder)
- lls (List files stored on the local server)
- lpwd (Display the current local folder)

*Transfer commands:*
- get (Download remote files to the current local folder)
- put (Upload local files or folders to the current folder on the remote server)

---

For further information type 'help' for a list of commands and then type help <topic>

~~~
cd       delegate  get     lcd    logout  mkdir      put   rm    
compare  exit      help    lls    lpwd    processes  pwd   rmdir 
debug    file      import  login  ls      publish    quit  whoami
~~~

e.g. pawsey:/projects> help compare

Compares a local and a remote folder and reports any differences
The local and remote folders must have the same name and appear in the current local and remote working directories

Usage: compare [folder name]


