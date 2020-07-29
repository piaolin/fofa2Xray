# fofa2Xray
<p>
  <img src="https://img.shields.io/github/v/release/piaolin/fofa2Xray.svg" />
  <img src="https://img.shields.io/github/release-date/pianlin/fofa2Xray.svg?color=blue&label=update" />
  <a href="https://github.com/piaolin/fofa2Xray/blob/master/README.md/">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" target="_blank" />
  </a>
</p>

A tool that can combine <a href="https://fofa.so/">fofa</a> and <a href="https://github.com/chaitin/xray">xray</a> for automatic batch scanning.

Coding by golang, both for windows and linux.

## Introduction

Use fofa api to get target domain list,  then make webscan by xray.

## Demo

![image-20200729095201091](https://github.com/piaolin/fofa2Xray/blob/master/pics/image-20200729095201091.png?raw=true)

## Quick start

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





