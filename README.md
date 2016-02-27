# goto
---
## Instruction

goto is a group login scripts on Linux system. User can configure servername login command, account, host, port, even password into config file. Then user can use goto servername to login into remote system.

Now It only support ssh login.

## config file

Config file is installed under /etc/, name is goto.conf, config format

	[root@123 ~]# cat /etc/goto.conf
	myserver ssh 192.168.0.2 root 22 xxxx

- the first column is servername
- the second column is login command
- the third column is remote server host
- the forth column is remote server port
- the fifth column is remote server login password. for safety, this column could be ingored

one line for each server

## install

This command should install with root, use install command as followed:

- Linux

		tar xzf goto.tar.gz
		cd goto
		./install

- Mac OS

		tar xzf goto.tar.gz
		cd goto
		chmod 755 ./install
		sudo ./install

- command will be installed under /usr/bin/ in Linux, under /usr/local/bin/ in Mac OS
- config file will be installed under /etc/
- login script will be installed under /etc/goto.conf.d/

## Usage

- goto

	Usage: goto hostname

- upload

	Usage: upload [-r] hostname localfile [remotefile]

- download

	Usage: download [-r] hostname remotefile [localfile]

parameter instruction

- hostname: hostname is first column in config file
- -r: if you upload or download a directory, you should add -r option
- localfile: local file name, you can use absolute path like /root/aa, otherwise, command will set file location dir with pwd instead
- remotefile: remote file name, you can use absolute path like /root/aa, otherwise, command will set file location dir with ~/ instead

In upload, if you don't set remotefile, upload will set filename same with local file name, and set remote location dir with ~/

In download, if you don't set localfile, download will set filename same with remote file name, and set local location dir with pwd

## TODO

download cover protection
