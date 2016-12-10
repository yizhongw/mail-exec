# mail-exec
A command utility that runs your job and sends email to you when it's done.

### Install Guide

1. Install ssmtp to send email:
	
	```
	sudo apt-get install ssmtp
	```

2. Configure ssmtp at `/etc/ssmtp/ssmtp.conf`:

	```
	root=username@gmail.com
	mailhub=smtp.gmail.com:465
	rewriteDomain=gmail.com
	AuthUser=username
	AuthPass=password
	FromLineOverride=YES
	UseTLS=YES
	```
	
	For other email service like qq or 163, the comfiguration is similar.

3. Clone this reposity and cd in:

	```
	git clone https://github.com/EastonWang/mail-exec.git
	cd mail_exec
	``` 

4. Install `mail-exec`:
	
	```
	sudo install -m 755 mail-exec /usr/bin/mail-exec
	```

5. Configure `mail-exec.rc` file, otherwise `mail-exec` will ask you about send_from email and send_to email every time you execute it.
	```
	copy mail-exec.rc.example ~/.mail-exec.rc
	```
	or 
	```
	copy mail-exec.rc.example etc/mail-exec.rc
	```

	**Note: ** The send_from email address must be same as your authorization email address configured at `/etc/ssmtp/ssmtp.conf`

### Usage
Now you can execute your command with mail-exec as prefix:
```
mail-exec python3 test.py
```

You can also run your command on backgroud with [nohub](https://www.cyberciti.biz/tips/nohup-execute-commands-after-you-exit-from-a-shell-prompt.html) :
```
nohub mail-exec python3 test.py > nohub.out &
```

You will receive a success email if your program is done successfully:
![](https://github.com/EastonWang/mail-exec/blob/master/success.png) 

Of course, you will get a fail message if your program fails:
![](https://github.com/EastonWang/mail-exec/blob/master/fail.png) 

-----
### Have fun and welcome pr!