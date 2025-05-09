
## Install Python from Source:

To install **Python 3.10** from source on **Rocky Linux 8**, follow these step-by-step instructions.


### Install Required Dependencies:


_For CentOS/RHEL:_

```
dnf groupinstall -y "Development Tools"

dnf install -y wget tar gcc make openssl-devel bzip2-devel libffi-devel zlib-devel readline-devel
```


```
dnf group list --installed | grep "Development Tools"
```


_For Ubuntu:_

```
apt install -y wget build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev 
```



```
openssl version

OpenSSL 1.1.1k  FIPS 25 Mar 2021
```



```
openssl version -a
openssl version -d
```




```
gcc --version
```


```
make --version
```


```
ldd --version
```



### Download Python:

```
cd /opt
wget https://www.python.org/ftp/python/3.10.8/Python-3.10.8.tgz

or,

wget https://www.python.org/ftp/python/3.10.8/Python-3.10.8.tar.xz
```


```
tar -xzf Python-3.10.8.tgz

mv Python-3.10.8 python-3.10.8
cd python-3.10.8
```


### Compile and install Python: 

Use `make altinstall` to avoid overwriting the system's default `python3`.


```
mkdir /opt/python-3.10.8/py-build
```


```
./configure --enable-optimizations

Or,

./configure --prefix=/opt/python-3.10.8/py-build --enable-optimizations
```


_Next, start the build process using the following command:_

```
make 

//make -j$(nproc)

//make -j 2
//nproc
```


_Finally, install Python 3.10 by running the following command:_

```
make altinstall
```


```
### Output:

Installing collected packages: setuptools, pip
  WARNING: The script pip3.10 is installed in '/opt/python-3.10.8/py-build/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.

Successfully installed pip-22.2.2 setuptools-63.2.0

WARNING: Running pip as the 'root' user can result in broken permissions and conflicting behaviour with the system package manager. It is recommended to use a virtual environment instead: https://pip.pypa.io/warnings/venv
```


#### Verify: 


```
/opt/python-3.10.8/py-build/bin/python3.10 -V


Python 3.10.8
```


```
/opt/python-3.10.8/py-build/bin/pip3.10 -V


pip 22.2.2 from /opt/python-3.10.8/py-build/lib/python3.10/site-packages/pip (python 3.10)
```



### Set Python Home:

```
vim python-310.sh

export PYTHON_HOME=/opt/python-3.10.8/py-build
export PATH=$PYTHON_HOME/bin:$PATH
```

```
cp python-310.sh /etc/profile.d
source /etc/profile.d/python-310.sh
```


```
python3.10 -V

pip3.10 -V
```


```
pip3.10 list
```



```
python3.10 -m pip install --upgrade pip

Or,

pip3.10 install --upgrade pip
```



```
which python3.10

/opt/python-3.10.8/py-build/bin/python3.10
```



### Links: 
- [Python FTP](https://www.python.org/ftp/python/3.10.8/)
- [Install Python 3.10](https://www.atlantic.net/vps-hosting/how-to-install-python-3-10-on-rocky-linux/)


