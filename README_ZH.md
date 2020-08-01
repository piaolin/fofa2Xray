# fofa2Xray

一款联合fofa与xray的自动化批量扫描工具

使用Golang编写，适用于windows与linux

## 文档

- [English](https://github.com/piaolin/fofa2Xray/blob/master/README.md)

- [中文文档](https://github.com/piaolin/fofa2Xray/blob/master/README_ZH.md)

## 原理

使用fofa api批量获取指定数据，然后使用xray进行主动扫描

## 示例

![image20200729095201091.png](http://img.static.plat.wgpsec.org/knowledge/215807dc29ed4543a4e81591432e8492.png)

## 快速使用

###### 1.    移动xray可执行程序到fofa2Xray同一目录(自带xray版本为1.1.0)

![image20200729093958904.png](http://img.static.plat.wgpsec.org/knowledge/fe71794cf7b84642b9733dfb08ead530.png)

###### 2.    修改配置文件

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
#  - .hbue.edu.cn
#  - .wust.edu.cn

xray:
 #path没有用，必须把xray可执行文件放在脚本同一目录
 path: D:\CyberSecurityTools\xray_windows_amd64\xray_windows_amd64.exe
 
 #fofa2Xray相同目录下xray的全名
 name: xray_windows_amd64.exe

 #同时运行xray的最大数
 thread: 10
~~~

###### 3.    启动fofa2Xray

~~~shell
./fofa2Xray
nohup ./fofa2Xray & // 持久化
~~~

###### 4.    结果审核

fofa2Xray会自动为每个目标创建结果文件夹

![image20200729095822453.png](http://img.static.plat.wgpsec.org/knowledge/c6cde4d2a3664104a670553427acf257.png)

## 下载地址

https://github.com/piaolin/fofa2Xray/releases