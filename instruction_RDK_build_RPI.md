# Host Machine prepation 

```c
sudo apt install gawk wget git diffstat unzip texinfo gcc-multilib g++-multilib build-essential chrpath socat bison curl cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1 libsdl1.2-dev pylint xterm
```
## Configure bash as default command interpreter for shell scripts
```c
sudo dpkg-reconfigure dash // Select “No”
To choose bash, when the prompt asks if you want to use dash as the default system shell - select “No”
```
##  Configure Git
```c
// configure user name and email address
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com

//configure git cookies. Needed for Gerrit to only contact the LDAP backend once.
git config --global http.cookieFile /tmp/gitcookie.txt
git config --global http.saveCookies true
```
##  Configure repo
In order to use Yocto build system, first you need to make sure that repo is properly installed on the machine:
```c
//create a bin directory
mkdir ~/bin
export PATH=~/bin:$PATH

//Download the repo tool and ensure that it is executable
curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

## Credential configuration
Note: it is also recommended to put credentials in .netrc when interacting with the repo.
Note >> .netrc file should be under ~/ home dirctory 
A sample .netrc file is illustrated below
```c
machine code.rdkcentral.com

    login <YOUR_USERNAME>

    password <YOUR_PASSWORD>
```
## Downloading Source Code & Building
```c
repo init -u https://code.rdkcentral.com/r/manifests -m rdkb.xml -b master

repo sync --no-clone-bundle
```


