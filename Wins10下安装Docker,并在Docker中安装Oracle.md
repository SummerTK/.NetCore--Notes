# Wins10下安装Docker,并在Docker中安装Oracle

下载并安装Docker for Windows Installer.exe

```
 https://download.docker.com/win/stable/Docker%20for%20Windows%20Installer.exe 
```

------

安装完成后登录Docker（**没有Docker账号根据提示到官网注册**）

------

打开PowerShell

------

输入

```
docker login
```

命令，按照提示输入用户名密码（**用户名名是Docker网站的UserName，不是邮箱账号**），等待登录成功（未登陆后面操作会提示错误：unauthorized: incorrect username or password）

------

输入

```
docker search oracle
```

命令，查找oracle镜像

------

输入

```
docker pull wnameless/oracle-xe-11g
```

命令，拉取镜像，等待下载完成

------

输入

```
docker images
```

命令，查看本地镜像

------

输入

```
docker run -d -p 1522:22 -p 1521:1521 wnameless/oracle-xe-11g
```

命令，启动oracle（将主机的1522端口映射到容器的22端口,将主机的1521端口映射到容器的1521），等待启动完成

------

输入

```
docker ps
```

命令，查看oracle相关进程

------

利用plsql连接oracle

tnsnames.ora文件配置

```
xe = 
(DESCRIPTION = 
    (ADDRESS = (PROTOCOL = TCP)(HOST = localhost)(PORT = 1521)) 
    (CONNECT_DATA = 
      (SERVICE_NAME = XE) 
    ) 
) 
```

