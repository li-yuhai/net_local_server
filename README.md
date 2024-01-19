### 内网穿透服务

推荐使用基于go的，python我琢磨很久优化，响应时间还是太慢了。

运行go程序

```shell
# 公网服务端，8000是用来给使用公网的，2333是用来连接客户端（本地）
go run server.go -localPort 8000 -remotePort 2333    

# 客户端（本地），8080是本地项目部署端口， 2333是和公网服务器的端口 
go run client.go -host xx.xx.xx.xx -localPort 8080 -remotePort 2333
```

已经编译好可执行程序：windows、mac、linux

```shell
./server -localPort 8000 -remotePort 2333

./client -localPort 8000 -remotePort 2333

 # 后台运行方式
nohup ./server   
# 杀死端口8000的程序
ps -ef | grep 8000 | grep -v grep | cut -c 9-15 | xargs kill -9    
```



### 基于Linux快速安装go开发环境：

https://blog.csdn.net/wltsysterm/article/details/119383406 感谢作者提供的博客。

```shell
# 安装wget
yum install -y wget

# 下载国内的go
wget https://studygolang.com/dl/golang/go1.16.6.linux-amd64.tar.gz

# 安装
tar -C /usr/local -zxvf go1.16.6.linux-amd64.tar.gz

# 环境变量， 在/etc/profile最后一行添加 export信息
vi /etc/profile
export GOROOT=/usr/local/go
export PATH=$PATH:$GOROOT/bin

# 加载环境变量
source /etc/profile
```



### 感谢原作者

https://gitee.com/wapai/projects 感谢作者提供的代码。





