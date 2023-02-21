# Pre-req

Read [https://github.com/ezYakaEagle442/chocolatey/](https://github.com/ezYakaEagle442/chocolatey/)
Install Git Bash :

```sh
choco install git.install --Yes --confirm --accept-license
choco install gh --Yes --confirm --accept-license

```


## Create your SSH Keys

If your GIT repo URL starts with HTTPS (ex: "https://github.com/<!XXXyour-git-homeXXX!/spring-petclinic.git"), git CLI will always prompt for password. 
When MFA is enabled on GitHub and that you plan to use SSH Keys, you have to use: git clone git@github.com:your-git-home/spring-petclinic.git

```sh
eval `ssh-agent -s`
eval $(ssh-agent -s) 
sudo service ssh status
# sudo service ssh --full-restart
ssh-add /home/~username/.ssh/githubkey
ssh-keygen -l -E MD5 -f /home/~username/.ssh/githubkey
ssh -T git@github.com
```

# Allow your SSH Keys from GitHub

Go to [https://github.com/settings/keys](https://github.com/settings/keys) click on the button 'New SSH Key' then 'Add SSH Key'

# Git configuration

```sh
#https://stackoverflow.com/questions/17307154/git-bash-push-to-bitbucket-ignores-ssh-key
# which ssh gaves /bin/ssh ..... In the .bashrc profile we just added
# export GIT_SSH=/bin/ssh.exe
#

[user]
	name = bob.jojo
	email = bob.jojo@yourcorp.com
[core]
	editor = nano
	#sshCommand = ssh -i /c/Users/bob.jojo/.ssh/bob_rsa
	sshCommand = ssh -i /c/Users/bob.jojo/.ssh/id_rsa

[alias]
	hist = log --all --graph --decorate --oneline

[http]
	#proxy = http://gateway.yourcorp.zscaler.net:80
	sslVerify = true
	#sslCAInfo=/ssl/certs/ca-bundle.crt
	
# https://stackoverflow.com/questions/23885449/unable-to-resolve-unable-to-get-local-issuer-certificate-using-git-on-windows
# Since git 2.3.1, you can put https://your.domain inside an HTTP section to indicate the following certificate is only for this domain.
[http "https://git-pprd.apps.airliquide.com"]
	# Put the certificate at C:\Users\~YourUserName\AppData\Local\Programs\Git\mingw64\ssl\certs
	sslCAInfo=/ssl/certs/the_cert-tree.cer
	
[http "https://ec2-42-42-42-42.eu-west-1.compute.amazonaws.com"]
	# Put the certificate at C:\Users\~YourUserName\AppData\Local\Programs\Git\mingw64\ssl\certs
	sslCAInfo=/ssl/certs/Dummmy_cert-tree.cer
	#https://developers.whatismybrowser.com/useragents/explore/
	#userAgent=git/2.15.1.windows.2
	#Chrome Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/67.0.3396.99 Safari/537.36
    # IE11: User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; Trident/7.0; rv:11.0) like Gecko
	#Eclipse embedded browser: Mozilla/5.0 (Windows NT 10.0; Win64; x64; Trident/7.0; rv:11.0) like Gecko
	useragent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/67.0.3396.99 Safari/537.36
	sslVersion=tlsv1.2
	# cookieFile = /tmp/cookie.txt
[web]
	#browser = firefox
	browser = Chrome
[help]
	format = web

```


