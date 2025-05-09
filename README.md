## Python:


### For CentOS 7:

To install **Python 3 on CentOS 7**, which only ships with **Python 2.7 by default**, you need to enable additional repositories or build from source.

- Python 2.7.5 is installed by default. That version has reached its EOL years ago.
- Python 3.6.8 is the latest version available in the CentOS 7 repos. 3.6 reached its EOL in Dec 2021.



### Enable EPEL repositories: 

```
yum install -y epel-release
```


```
yum list available | grep python3
```


```
yum install -y python3
```


```
python3 -V

Python 3.6.8
```


### Enable IUS repositories: 


```
yum install -y https://repo.ius.io/ius-release-el7.rpm
```


Sometimes the IUS version is named differently, like:
- python39
- ython38u
- python36u


If you find a version you want (say `python39`), install like:


```
yum install -y python36
```


```
yum install -y python39 python39-pip python39-devel
```


Install Python 3.10 (or latest available in IUS):

```
yum install -y python310 python310-pip python310-devel
```




### For CentOS-8:

To install Python on CentOS/Rocky Linux/RHEL systems These instructions are valid for CentOS 8, Rocky Linux 8/9, and similar RHEL-based distros.

- Python isn’t installed by default.
- Python 3.9.6 is the latest version available in the CentOS 8 repos. The EOL of Python 3.9.6 is Oct 2025, so you can use that version.


#### Install Python 3 from DNF (default repo):

This installs the default version provided by the OS (often Python 3.6 or 3.9, depending on the OS version).

```
dnf install -y python3
```


```
python3 -V

Python 3.6.8
```




#### Install a Specific Python Version: 

_Enable EPEL and software collections:_

```
dnf install -y epel-release
dnf install -y dnf-utils
```


_To check `AppStream` repository and enable it:_

```
dnf repolist all

repo id                   repo name                               status
appstream                 Rocky Linux 8 - AppStream               enabled
```


```
dnf config-manager --set-enabled appstream
```


_Enable AppStream module for newer Python (on Rocky 8/9):_

```
dnf module list
```


```
dnf module list | grep python

libselinux-python    2.8             common                                   Python 2 bindings for libselinux 
python27             2.7 [d]         common [d]                               Python programming language, version 2.7 
python36             3.6 [d][e]      build, common [d]                        Python programming language, version 3.6 
python38             3.8 [d]         build, common [d]                        Python programming language, version 3.8 
python39             3.9 [d][e]      build, common [d]                        Python programming language, version 3.9
```


```
dnf module list python*


Rocky Linux 8 - AppStream
Name                        Stream                       Profiles                            Summary
python27                    2.7 [d]                      common [d]                          Python programming language, version 2.7
python36                    3.6 [d][e]                   build, common [d]                   Python programming language, version 3.6
python38                    3.8 [d]                      build, common [d]                   Python programming language, version 3.8
python39                    3.9 [d][e]                   build, common [d]                   Python programming language, version 3.9

Hint: [d]efault, [e]nabled, [x]disabled, [i]nstalled
```


```
dnf module enable -y python38:3.8
```


```
dnf module disable -y python38:3.8
dnf module reset -y python38:3.8
```



_Install v3.9:_

```
dnf install -y python39
```


```
python3 -V

Python 3.9.20
```




### For Ubuntu:

There are several methods for installing Python on Ubuntu:

- Via `APT`. Install the latest version available in the **default Ubuntu repository**.
- Via `PPA`. Install Python from the Deadsnakes PPA, a **third-party repository** designed for Ubuntu.
- From **source code**. Install the latest version from the official Python website.
- default Version:
    - **Ubuntu 20.04** LTS, the python included in the base system is Python `3.8`.
    - **Ubuntu 22.04** defaults to Python `3.10`. This version is pre-installed.


```
apt install -y python3 python3-venv
```


```
apt install -y python3-pip
```


```
python3 -V

Python 3.8.10
```


```
pip3 -V

pip 20.0.2 from /usr/lib/python3/dist-packages/pip (python 3.8)
```


### Install a specific version: (Python 3.10)


```
apt install software-properties-common -y
```


_Add the `deadsnakes` PPA:_

```
add-apt-repository ppa:deadsnakes/ppa

apt update
```


```
apt install -y python3.10 python3.10-venv python3.10-dev python3.10-distutils 
```


_If install `python3.12`:_
```
apt install python3.12
```


```
python3.10 -V

Python 3.10.17
```


#### Install PIP for Python 3.10:


```
python3.10 -m venv app-env
```


```
curl -sS https://bootstrap.pypa.io/get-pip.py | python3.10
```


```
python3.10 -m pip --version
```


```
pip3.10 --version
```





### Links:
- [Install Python](https://linuxstans.com/how-to-install-python-centos/)
- [Install Python 3 on Ubuntu](https://phoenixnap.com/kb/how-to-install-python-3-ubuntu)


