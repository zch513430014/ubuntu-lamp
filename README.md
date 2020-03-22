# # ubuntu-lamp
最近疫情期间,闲来无趣,想着研究PHP源码来着,所以想试着在ubuntu系统中编译安装php...
## 第一步
去docker-hub 找到官方ubuntu镜像
[ubuntu 官方镜像](https://hub.docker.com/_/ubuntu?tab=description&page=1 "ubuntu 官方镜像")
### 1.1 版本很多,挑选一个可以用阿里云加速的版本
> [阿里云加速 source.list](https://developer.aliyun.com/mirror/ubuntu?spm=a2c6h.13651102.0.0.3e221b11FYgPps "阿里云加速 source.list")
> UBUNTU_VERSION=18.04

### 1.2 版本写到.env中
UBUNTU_VERSION=18.04
### 1.3 添加一个加速文件aliyunsource.list文件 替换 ubuntu内部source.list
### 1.4 下载php源文件并且设置PHP版本
由于[PHP官网](https://www.php.net/downloads "PHP官网")太卡,国内可选择从
[搜狐php下载](http://mirrors.sohu.com/php/ "搜狐php下载")
>PHP_VERSION=7.4.2

### 1.5 编译PHP
需要安装gcc版本
