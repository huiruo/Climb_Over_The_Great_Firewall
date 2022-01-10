
## frp介绍：
```
frp:Fast Reverse Proxy
内网穿透:将内网服务暴露给外网访问
```
### 客户端frpc的配置，c就是client
```
在frp服务内网穿透中，有两种角色：
  服务器：具有公网IP，运行服务端。比如可以用各类云服务器。
  客户端：内网计算机，运行客户端。

frps ：服务端程序
fprs.ini ：服务端配置文件
frps_full.ini：服务端配置文件，附带大量示例配置项。

frpc：客户端程序
frpc.ini ：客户端配置文件
frpc_full.ini：客户端配置文件，附带大量示例配置项
```

### 安装版本
```
windows_amd64.zip
linux_amd64.tar.gz
```


## frp客户端配置
frpc.ini
```
[common]
server_addr = <服务端公网ip>
server_port = <服务端bind_port端口>
token = <自定义口令>

[http]
local_ip = 127.0.0.1
local_port = 9999
remote_port = 16880

[shadowsocks]
type = tcp
local_ip = 127.0.0.1
local_port = 80960
remote_port = 7030
```

## frp服务端配置 在具有公网ip的Linux frps.init 配置
```
服务端配置：
bind_port = <绑定端口>
dashboard_port = <面板页面端口>
token = <口令>
dashboard_user = <面板页面帐号>
dashboard_pwd = <面板页面密码>
```

### Linux设置和启动frp服务
```
sudo mkdir -p /etc/frp
sudo cp frps.ini /etc/frp
sudo cp frps /usr/bin
sudo cp systemd/frps.service /usr/lib/systemd/system/
sudo systemctl enable frps
sudo systemctl start frps

#启动测试
systemctl start frps.service
#查看服务状态
systemctl status frps.service
```

## 验证
```
此时，在浏览器中打开服务器端ip:7500，提示输入账号密码，输入对应dashboard中的账号密码，即可看到frp管理WEB UI

公网ip:9980
这个时候，外网就可以通过frp服务器的自定义端口9980，访问到内网的win10机器上的9999了。
```