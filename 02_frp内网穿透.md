
## frp介绍：
```
frp:Fast Reverse Proxy
内网穿透:将内网服务暴露给外网访问
```


### 客户端配置
frpc.ini
```
[common]
server_addr = 119.3.43.237
server_port = 7000
token = xxxx

[http]
local_ip = 127.0.0.1
local_port = 9999
remote_port = 16880

[shadowsocks]
type = tcp
local_ip = 127.0.0.1
local_port = 80960
remote_port = 7030

其中common字段下的三项即为服务端的设置。
“server_addr”为服务端IP地址，填入即可。
“server_port”为服务器端口，填入你设置的端口号即可，如果未改变就是7000
“token”是你在服务器上设置的连接口令，原样填入即可
```