# MSSC 8005 端口部署说明

## 第一次部署

```bash
cd /opt
git clone https://github.com/t47tyfb8rm-arch/MSSC.git MSSC
cd MSSC
```

检查端口：

```bash
ss -lntp | grep 8005
```

没有输出说明端口可用。

启动：

```bash
nohup python3 -m http.server 8005 > server.log 2>&1 &
```

检查：

```bash
curl -I http://127.0.0.1:8005/
ss -lntp | grep 8005
tail -100 server.log
```

浏览器访问：

```text
http://服务器IP:8005/
```

## 更新部署

```bash
cd /opt/MSSC
git -c http.version=HTTP/1.1 pull
fuser -k 8005/tcp
nohup python3 -m http.server 8005 > server.log 2>&1 &
curl -I http://127.0.0.1:8005/
```

## 防火墙

如果服务器本机 curl 正常，但公网打不开：

```bash
firewall-cmd --query-port=8005/tcp
firewall-cmd --add-port=8005/tcp --permanent
firewall-cmd --reload
```

同时确认云服务器安全组已放行 `8005/tcp`。

## 数据说明

当前是纯前端静态版本，数据保存在访问设备当前浏览器的 `localStorage` 中。换手机、换浏览器或清缓存后数据不会自动同步。
