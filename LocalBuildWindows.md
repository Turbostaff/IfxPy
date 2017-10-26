## Windows build
----------------
##### Prerequisite:
* [Python 2.7 or above](https://www.python.org/downloads/)
* [Python 3.4 or above](https://www.python.org/downloads/)
* clone the IfxPy repository
* Visual Studio 2008 or above (Windows Only)
* Informix client SDK 410xC2 or above
* Set environment variable **CSDK_HOME** and **MY_PY_DIR**

### Clone the source code
Let's assume **C:\work** is the location when we clone the IfxPy repository.  
(You may clone it at any location though; if so make adjustment for the instructions as well).

```bat
cd C:\work

git clone https://github.com/OpenInformix/IfxPy.git
```

##### Build Shell Environment 
Set **CSDK_HOME** and **MY_PY_DIR** environment variables.  
The environment **CSDK_HOME** points to the **Informix Client SDK**.   
The environment **MY_PY_DIR** points to the Python source code installation.  

```bat
# Open VS2008 (or latest) command windows
# set VS90COMNTOOLS if you are using latest vs, for eg, vs2015 then
SET VS90COMNTOOLS=%VS140COMNTOOLS%

SET CSDK_HOME=c:\informix
SET MY_PY_DIR=C:\Dev\Python27
```


FYI: 
While running setup.py for package build, Python 2.7 searches for an installed Visual Studio 2008. (The installation path of VS2008 is stored in the variable VS90COMNTOOLS). The general pattern for VS installation path is 
```bat 
VS<internal version number>COMNTOOLS.  
```
That means if you are using higher version of VS then you may map **VSxxCOMNTOOLS** for that VS to **VS90COMNTOOLS**.  

```bash
#For example:   
#If you are using Visual Studio 2010 (VS10):  
SET VS90COMNTOOLS=%VS100COMNTOOLS%
  
#If you are using Visual Studio 2012 (VS11):   
SET VS90COMNTOOLS=%VS110COMNTOOLS%
  
#If you are using Visual Studio 2013 (VS12):   
SET VS90COMNTOOLS=%VS120COMNTOOLS%
  
#If you are using Visual Studio 2015 (VS14):   
SET VS90COMNTOOLS=%VS140COMNTOOLS%
```

##### Starting the build
```bash
cd C:\work\IfxPy\IfxPy
python setup.py build > out.txt 2>&1
```

### Install
On successful build the Informix python package (**IfxPy.pyd**) should have built at  
C:\work\IfxPy\IfxPy\build\lib.win-amd64-2.7
For the time being, you may manually copy Informix python package (IfxPy.pyd) to your Python module directory.

```bat
COPY  C:\work\IfxPy\IfxPy\build\lib.win-amd64-2.7\IfxPy.pyd
```

Try a sample
```bash
cd C:\work\IfxPy\try
copy  C:\work\IfxPy\IfxPy\build\lib.win-amd64-2.7\IfxPy.pyd
copy Sample1.py Sample.py
set PATH=C:\Informix\bin;%PATH%

# Edit Sample.py connection information, and then run
python Sample.py
```
