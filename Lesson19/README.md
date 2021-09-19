# 建立私有网段的服务器 - For MySQL

=============================

## 知识点

* 修改私有网段安全组，增加 Port:22 支持
* 在私有网段建立 EC2 实例
* 通过公有网段 web-ec2 实例连接到 db-ec2 实例

## 实战演习

### * 修改私有网段安全组，增加 Port:22 支持

* deeplearnaws-db-sg
* Port: 22

### 在私有网段建立 EC2 实例

* Name: deeplearnaws-db1

### 通过公有网段 web-ec2 实例连接到 db-ec2 实例

* 本地连接到 deeplearnaws-web1
* 拷贝本地连接私钥到** deeplearnaws-web1
* 通过 deeplearnaws-web1 连接到 deeplearnaws-db1
* deeplearnaws-db1测试

```bash
# @deeplearnaws-web1
$ ssh -i ./deeplearnaws-ssh-key.pem 172.16.20.10
# @deeplearnaws-db1
$ sudo yum update -y
# print out AWS LINUX INFO
$ cat /etc/os-release
# List packages available from AMAZON
$ sudo amazon-linux-extras list
# Install Docker
$ sudo amazon-linux-extras install -y docker
# 修改 docker 附加组给 ec2-user
$ sudo usermod -a -G docker ec2-user
# start Docker
$ sudo systemctl start docker
# confirm Docker running status
$ ps aux | grep docker
#  注册 Docker 服务 (用于每次Linxu启动后，Docker将会被启动)
$ sudo systemctl enable docker
#  install Docker-compose
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose
# 设置 docker-compose 的执行权限
$ sudo chmod +x /usr/bin/docker-compose
$ docker-compose version
#######################################
# Node.js
$ curl -sL https://rpm.nodesource.com/setup_12.x | sudo bash -
$ sudo yum install -y gcc-c++ make
$ sudo yum install -y nodejs
$ node -v
# git
$ sudo yum install -y git
$ git version
#nmap
$ sudo yum install -y nmap

# stop EC2 instance
$ sudo init 0

$ curl https://komavideo.com
```

## 小马部落(Discord)

https://discord.gg/VSKw72P

## 小马视频频道

http://komavideo.com

## 课程文件

https://github.com/komavideo/LearnAWS
