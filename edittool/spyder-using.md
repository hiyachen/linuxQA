# 1:安装spyder2:
## 安装包：
```
root@linux:/var/cache/apt/archives# ls -l | grep spyder
-rw-r--r-- 1 root root   484730 10月 20  2014 python-spyderlib_2.3.1+dfsg-1_all.deb
-rw-r--r-- 1 root root   854996 10月 20  2014 python-spyderlib-doc_2.3.1+dfsg-1_all.deb
-rw-r--r-- 1 root root    56238 10月 20  2014 spyder_2.3.1+dfsg-1_all.deb
-rw-r--r-- 1 root root   509056 10月 20  2014 spyder-common_2.3.1+dfsg-1_all.deb
```

## 安装后：
```
root@linux:/var/cache/apt/archives# aptitude search spyder
i A python-spyderlib                     - Python IDE for scientists (Python 2 modules)                                                                             
i A python-spyderlib-doc                 - Python IDE for scientists (Documentation)                                                                                
v   python2.7-spyderlib                 -                                                                                                                          
p   python3-spyderlib                  - Python IDE for scientists (Python 3 modules)                                                                             
i   spyder                              - Python IDE for scientists (Python 2)                                                                                     
i A spyder-common                       - Python IDE for scientists (common files)                                                                                 
p   spyder3                            - Python IDE for scientists (Python 3) 
```

## 帮助
```
root@linx:/var/cache/apt/archives# spyder -help
Usage: spyder [options] files

Options:
  -h, --help            show this help message and exit
  -l, --light           Light version (all add-ons are disabled)
  --new-instance        Run a new instance of Spyder, even if the single instance mode has been turned on (default)
  --session=STARTUP_SESSION   Startup session
  --defaults            Reset configuration settings to defaults
  --reset               Remove all configuration files!
  --optimize            Optimize Spyder bytecode (this may require administrative privileges)
  -w WORKING_DIRECTORY, --workdir=WORKING_DIRECTORY Default working directory
  --show-console        Do not hide parent console window (Windows)
  --multithread         Internal console is executed in another thread  (separate from main application thread)
  --profile             Profile mode (internal test, not related with Python    profiling)
```

# mongo连接
## 安装mongodb
```
root@linx:/home/rocky# aptitude install mongodb mongodb-server mongodb-clients mongodb-dev python-pymongo
0 个软件包被升级，新安装 18 个，0 个将被删除， 同时 156 个将不升级。
需要获取 45.0 MB 的存档。解包后将要使用 234 MB。

root@linx:/home/rocky# mongo --version
MongoDB shell version: 2.4.10

安装python连接mongodb的库文件pymongo
`# wget http://pypi.python.org/packages/source/p/pymongo/pymongo-1.11.tar.gz
`# tar zxvf pymongo-1.11.tar.gz
`# cd pymongo-1.11
`# python setup.py install
```
