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

hostname is first column in config file

## TODO

- upload

	upload file to remote server

- download

	download file from remote server
