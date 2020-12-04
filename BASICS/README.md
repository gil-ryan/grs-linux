# Basics to Fundamentals

## Utilizing basic commands

### pwd

Most users are familiar with utilizing a GUI, or _Graphical User Interface_. Made up of icons that allow you to click through and navigate through a computer, it tends to be easier for many. While utilizing the CLI, it's not always apparent what directory you are working in.

> pwd

```OUTPUT
burt@grs-beta ~ % pwd
/Users/burt
```

### whoami

Simply check what user account you're logged in with. It sounds simplistic, but you'd be surprised at how often you actually end up using this command:

> whoami

```OUTPUT
burt@grs-beta ~ % whoami
burt
```

### cd

__cd__ is used to change the current directory you're in

> cd 

```OUPUT
burt@grs-beta ~ % pwd
/Users/burt
burt@grs-beta ~ % cd /etc
burt@grs-beta /etc % pwd
/etc
```

You can use _.._ to move up a level, or _.. .._ to move up two levels, for example:

> cd ../..

```OUTPUT
burt@grs-beta ~ % pwd
/Users/burt
burt@grs-beta ~ % cd ../..
burt@grs-beta / % pwd
/
```

Pretty straight forward for now.

### ls

_ls_ is utilized to list the files and subdirectories in a directory, so basically the contents of a folder.

> ls

```OUTPUT
burt@grs-beta / % ls
Applications	Volumes		duplicates.txt	private		var
Library		bin		etc		sbin
System		cores		home		tmp
Users		dev		opt		usr
```

### Man pages, flags, and dashes

Utilizing the _man_ command will generally provide a manual page for any command you reference.

> man pwd

```OUTPUT
burt@grs-beta / % man pwd


PWD(1)                    BSD General Commands Manual                   PWD(1)

NAME
     pwd -- return working directory name

SYNOPSIS
     pwd [-L | -P]

DESCRIPTION
     The pwd utility writes the absolute pathname of the current working direc-
     tory to the standard output.

```

While utilizing commands, most often you will be adding parameters. Parameters are done using dashes, generally two dashes are reserved for full words, and singles dashes are for a char.

> ls -l

```OUTPUT
burt@grs-beta / % ls -l
total 16
drwxrwxr-x+ 55 root  admin  1760 Dec  1 14:47 Applications
drwxr-xr-x  69 root  wheel  2208 Oct 12 01:35 Library
drwxr-xr-x@  8 root  wheel   256 Apr  6  2020 System
drwxr-xr-x   7 root  admin   224 Apr  6  2020 Users
drwxr-xr-x   3 root  wheel    96 Dec  2 23:03 Volumes
drwxr-xr-x@ 38 root  wheel  1216 Oct 12 01:30 bin
drwxr-xr-x   2 root  wheel    64 Feb 29  2020 cores
dr-xr-xr-x   3 root  wheel  8034 Dec  2 00:48 dev
-rw-r--r--   1 burt  admin     0 Dec 26  2017 duplicates.txt
lrwxr-xr-x@  1 root  admin    11 Apr 22  2020 etc -> private/etc
lrwxr-xr-x   1 root  wheel    25 Dec  2 00:48 home -> /System/Volumes/Data/home
drwxr-xr-x   4 root  wheel   128 Apr 23  2020 opt
drwxr-xr-x   6 root  wheel   192 Oct 12 01:32 private
drwxr-xr-x@ 63 root  wheel  2016 Oct 12 01:30 sbin
lrwxr-xr-x@  1 root  admin    11 Apr 22  2020 tmp -> private/tmp
drwxr-xr-x@ 11 root  wheel   352 Apr 22  2020 usr
lrwxr-xr-x@  1 root  admin    11 Apr 22  2020 var -> private/var
```

> nmap --help

## Finding Things

Finding things can become a great challenge at first when learning Linux. Luckily, we hae some resources to do just that. Keep in mind that each tool has pro and con aspects. So it will be up to you to decide which command will provide the best fit.

### locate

The keyword _locate_ followed by another keyword denoting what you'd like to find will go through your entire filesystem and locate evere occurance of that word.

> locate [KEYWORD]

You will most likely get too many entries when using _locate_. Also, _locate_ uses a database that it only sycnhronized once a day. So you likely won't find new files from that day.

### whereis

If you're looking for a _binary_ file, you can use the _whereis_ command to locate it. This command returns the location of the binary, its source, and it's _man_ page.
If you're looking for a _binary_ file, you can use the _whereis_ command to locate it. This command returns the location of the binary, its source, and it's _man_ page when available.

> whereis [PARAMETER]

### which

The _which_ command is even more specific, it will return the location of the binaries in the PATH variable in Linux. 
The PATH holds the directories in which the OS looks for the commands you execute at the command line. 

## More powerful searches with find

The _find_ command is considered the most powerful and flexible of the search utilities. It is capable of beginning as search in any designated directory  and looking for any number of different parameters:

* file name
* date or creation
* date of modification
* owner
* group
* size
* permissions

So basically, any characteristic of a directory. [1] First state the directory, [2] second, specify the type of file to search for, [3] Lastly, you give the name of the file being searched for.

> burt@grs-beta / % find /[1] f[2] -name Discord[3]

The _find_ command started at the top of the filesystem (/), wentt through every directory looking for Discord in the filename, and then listed all instances found. Remember that _find_ displays only __exact name__ matches.