# 弹性搜索服务器iptables访问设置


```shell
## 其他任何机器不能访问，允许本机访问
iptables  -P INPUT DROP;iptables -A INPUT -s 本机外网出口ip地址 -p tcp -j  ACCEPT

## 允许正式服务器
iptables -A INPUT -s 101.200.199.239 -p tcp -j  ACCEPT;iptables -A INPUT -s 10.44.161.214 -p tcp -j  ACCEPT
iptables -A INPUT -s 101.200.80.107 -p tcp -j  ACCEPT;iptables -A INPUT -s 10.173.156.40 -p tcp -j  ACCEPT
iptables -A INPUT -s 182.92.196.79 -p tcp -j  ACCEPT;iptables -A INPUT -s 10.165.120.202 -p tcp -j  ACCEPT
iptables -A INPUT -s 123.57.212.126 -p tcp -j  ACCEPT;iptables -A INPUT -s 10.51.72.192 -p tcp -j  ACCEPT

## 允许测试服务器
iptables -A INPUT -s 139.129.20.141 -p tcp -j  ACCEPT
iptables -A INPUT -s 121.42.201.230 -p tcp -j  ACCEPT
iptables -A INPUT -s 115.28.23.93 -p tcp -j  ACCEPT

## 允许办公区区域网络访问

iptables -A INPUT -s 49.4.168.45 -p tcp -j  ACCEPT
iptables -A INPUT -s 49.4.168.44 -p tcp -j  ACCEPT
iptables -A INPUT -s 49.4.168.43 -p tcp -j  ACCEPT
iptables -A INPUT -s 49.4.168.42 -p tcp -j  ACCEPT
iptables -A INPUT -s 49.4.168.41 -p tcp -j  ACCEPT
iptables -A INPUT -s 49.4.168.40 -p tcp -j  ACCEPT
iptables -A INPUT -s 49.4.168.35 -p tcp -j  ACCEPT
```
