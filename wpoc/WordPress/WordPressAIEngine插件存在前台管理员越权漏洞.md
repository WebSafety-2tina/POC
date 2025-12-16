## WordPress 的 AI Engine 插件在所有版本（包括 3.1.3 及之前版本）中存在敏感信息泄露漏洞，通过 /mcp/v1/ REST API 端点在启用“无认证 URL”时会暴露“Bearer Token”值。这使得未认证的攻击者能够获取到 bearer token，从而获得有效会话的访问权限，并进行创建新管理员账户等多种操作，导致权限提升.

## fofa
```
"wp-content/plugins/ai-engine/"
```

## POC
```
https://github.com/Nxploited/CVE-2025-11749
```


