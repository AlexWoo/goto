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

Commands should be installed with root, use install command as followed:

- Linux

		yum install expect
		tar xzf goto.tar.gz
		cd goto
		./install

- Mac OS

		tar xzf goto.tar.gz
		cd goto
		chmod 755 ./install
		sudo ./install

- command will be installed under /usr/bin/ in Linux, under /usr/local/bin/ in MacOS
- config file will be installed under /etc/
- login script will be installed under /etc/goto.conf.d/

## Usage

- goto

	Usage: goto hostname

		login to remote server

		- hostname: hostname is first column in config file

- gocd

	Usage: gocd hostname -l localdir
	Usage: gocd hostname -r remotedir
	Usage: gocd hostname -l localdir -r remotedir

		set /etc/goto.conf.d/gocd.conf for upload and download

		- -l: set localdir, now localdir not use in upload nor download
		- -r: set remotedir, if remotefile in upload or download is not an absolute path, remotedir will set as default dir for remotefile, if remotedir does not set, ~/ will set as default dir for remotefile

		if localdir or remotedir is not an absolute path, it will be set with ~/ as default

- upload

	Usage: upload [-r] hostname localfile [remotefile]
	
		upload file to remote server, if you don't set remotefile, upload will set filename same with local file name, and set remote location dir with remotedir config in /etc/goto.conf.d/gocd.conf or ~/

		- hostname: hostname is first column in config file
		- -r: if you upload or download a directory, you should add -r option
		- localfile: local file name, you can use absolute path like /root/aa, otherwise, command will set file location dir with pwd instead
		- remotefile: remote file name, you can use absolute path like /root/aa, otherwise, command will set file location dir with remotedir config in /etc/goto.conf.d/gocd.conf or with ~/ instead

- download

	Usage: download [-r] hostname remotefile [localfile]
	
		download file to remote server, if you don't set localfile, download will set filename same with remote file name, and set local location dir with pwd

		- hostname: hostname is first column in config file
		- -r: if you upload or download a directory, you should add -r option
		- localfile: local file name, you can use absolute path like /root/aa, otherwise, command will set file location dir with pwd instead
		- remotefile: remote file name, you can use absolute path like /root/aa, otherwise, command will set file location dir with remotedir config in /etc/goto.conf.d/gocd.conf or with ~/ instead


## TODO

download cover protection
