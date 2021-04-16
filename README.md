# fofa2Xray

<p>
  <img src="https://img.shields.io/github/v/release/piaolin/fofa2Xray.svg" />
  <img src="https://img.shields.io/github/release-date/piaolin/fofa2Xray.svg?color=blue&label=update" />
  <a href="https://github.com/piaolin/fofa2Xray/blob/master/README.md/">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" target="_blank" />
  </a>
</p>

A tool that can combine <a href="https://fofa.so/">fofa</a> and <a href="https://github.com/chaitin/xray">xray</a> for automatic batch multithreading scanning.

Can also scan the IP/domain name list by using Xray.

Coding by golang, both for windows, linux and macOS.

[Download](https://github.com/piaolin/fofa2Xray/releases)

## Documentation

- [English](https://github.com/piaolin/fofa2Xray/blob/master/README.md)

- [中文文档](https://github.com/piaolin/fofa2Xray/blob/master/README_ZH.md)


## Introduction

Use fofa api to get target domain list,  then make webscan by xray.

## Demo

![image-20200729095201091](https://github.com/piaolin/fofa2Xray/blob/master/pics/image-20200729095201091.png?raw=true)

## File Mode Quick start

###### 1. Configure the xray executable file address and the number of threads in f2Xconfig.yaml

![image-20210416150831024](https://i.loli.net/2021/04/16/mchjnNeZOudHAia.png)

###### 2. Using "-t file" specify as file list scan mode(default is fofa mode), -f specify IP list file

~~~shell
./fofa2Xray -t file -f ipList.txt
~~~

###### 3. Perhaps it's a little strange, but for better scalability

## Fofa Mode Quick start

1. ##### Move xray to the directory where fofa2xray is located

   <img src="https://raw.githubusercontent.com/piaolin/fofa2Xray/master/pics/image-20200729093958904.png" alt="image-20200729093958904" style="zoom: 200%;" />

   

2. ##### Vi f2Xconfig.yaml

   ~~~yaml
   fofa:
     email: {fofa账户}
     key: {fofaKey}
   
     # 固定查询语句
     fixedQuerySyntexList:
       - status_code=200
       - country="CN"
   
     # 查询语法
     # 更多查询语法见https://fofa.so/
     querySyntax: host
   
     # 使用querySyntax查询语法分别查询target
     targetList:
       - .hubu.edu.cn
   #    - .hbue.edu.cn
   #    - .wust.edu.cn
   xray:
     #path没有用，必须把xray可执行文件放在脚本同一目录
     path: D:\CyberSecurityTools\xray_windows_amd64\xray_windows_amd64.exe
   
     #fofa2Xray相同目录下xray的全名
     name: xray_windows_amd64.exe
   
     #同时运行xray的最大数
     thread: 10
   ~~~

   

3. ##### Run fofa2Xray.

   ~~~yaml
   ./fofa2Xray
   nohup ./fofa2Xray &  // 持久化
   ~~~

4. ##### Check Result.

   Fofa2Xray will create result folder for every target.

   <img src="https://raw.githubusercontent.com/piaolin/fofa2Xray/master/pics/image-20200729095822453.png" alt="image-20200729095822453" style="zoom:200%;" />





