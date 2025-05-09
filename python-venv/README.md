
## Python Virtual Environment:

To create a Python virtual environment on Rocky Linux, you can follow these steps:


```
python3.10 -V
```


```
pip3.10 -V
```


### Install `venv` module: 

#### Use `python3-venv` when:
- You're using **Python 3.3+** and want a simple, native way to create venvs.
- You're working in system-managed environments (e.g., RHEL/Rocky 8/9).


_System package (`dnf`):_

```
dnf install python3-venv

dnf install python3.10-venv
```


Or,


#### Use `virtualenv` when:
- You need support for multiple Python versions or Python 2.
- You're using advanced workflows or need more portability.
- `venv` isn't available or you need to create a venv for a non-default Python version.


_Python package (`pip`):_

```
pip3.10 install virtualenv
```



### Create the virtual environment: 

#### Method-1: (Using python3.10 and venv)

_Syntax:_

```
python3.10 -m venv [env_name]

source [env_name]/bin/activate
```


_To create a virtual environment named `app_env`:_

```
python3.10 -m venv app_env
```


```
ll app_env

drwxr-xr-x 2 root root 168 May  9 23:06 bin
drwxr-xr-x 2 root root   6 May  9 23:06 include
drwxr-xr-x 3 root root  24 May  9 23:06 lib
lrwxrwxrwx 1 root root   3 May  9 23:06 lib64 -> lib
-rw-r--r-- 1 root root  93 May  9 23:06 pyvenv.cfg
```


```
cd app_env
```



_Next, activate the virtual environment:_

```
//source app_env/bin/activate

source bin/activate
```


```
pip3.10 install --upgrade pip
```


```
pip3.10 install numpy
pip3.10 uninstall numpy
```


```
vim average.py

import numpy as np
def calculate_average(numbers):
    average = np.mean(numbers)
    return average
if __name__ == '__main__':
    numbers = [1, 3, 5, 7, 9]
    average = calculate_average(numbers)
    print(f"The average number of {numbers} is : {average:.2f}")
```


```
python3.10 average.py
```



_To exit from the Python virtual environment:_

```
deactivate
```


#### Method-2: (using virtualenv)

```
python3.10 -m virtualenv app_env2
```


```
ll app_env2

drwxr-xr-x 2 root root 4096 May  9 23:00 bin
-rw-r--r-- 1 root root  194 May  9 23:00 CACHEDIR.TAG
drwxr-xr-x 3 root root   24 May  9 23:00 lib
-rw-r--r-- 1 root root  302 May  9 23:00 pyvenv.cfg
```



```
cd app_env2/
```



```
source bin/activate
```


```
deactivate
```



