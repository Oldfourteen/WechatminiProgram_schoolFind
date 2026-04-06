# 失物招领微信小程序 (Lost and Found WeChat Mini Program)

[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)
[![Platform: WeChat](https://img.shields.io/badge/Platform-WeChat-07C160.svg)](https://mp.weixin.qq.com/)

一个基于微信小程序的失物招领平台，集成了失物招领、论坛交流、即时通讯、AI聊天、OCR识别以及个人成就系统。本项目采用前后端分离架构，前端使用原生小程序开发，后端基于 Node.js Express 框架，数据库采用 MySQL。

## 核心功能

### 1. 失物招领 (Lost & Found)

- **发布信息**：支持发布寻物启事（Lost）和招领启事（Found），包含图片、标题、描述、分类、地点、时间及联系方式。
- **地理位置**：集成腾讯地图，支持拾取/丢失地点精准选择。
- **分类搜索**：提供证件类、电子产品、首饰饰品、服装鞋帽、箱包背包、文具用品、食品饮料等多种分类。
- **紧急标记**：支持将贴子标记为“紧急”，提高曝光率。
- **OCR识别**：集成 OCR 服务，可自动提取证件/物品中的文本信息。

### 2. 社区论坛 (Forum & Community)

- **动态发布**：用户可以分享社区动态，支持多图上传。
- **互动交流**：支持点赞、评论、@提醒（Mentions）以及私密贴发布。
- **举报机制**：内置完善的举报处理流程，维护社区秩序。

### 3. 消息与通讯 (Messaging)

- **即时私信**：用户间一对一实时沟通。
- **AI 助手**：集成 AI 聊天功能，解答用户疑问。
- **系统通知**：自动推送评论、点赞及举报处理结果。

### 4. 个人系统 (User System)

- **成就系统**：包含等级体系（Level）、每日签到（Check-in）及积分奖励。
- **装扮中心**：支持更换精美的头像框（Avatar Frames）。
- **实名认证**：支持实名认证流程，确保信息发布的真实性。

### 5. 管理端功能 (Admin Features)

- **人员管理**：管理员可对违规用户进行封禁、禁言操作。
- **内容审核**：集成内容过滤（Content Filter）系统，自动拦截违规言论。
- **数据统计**：首页实时展示今日发布量、已解决数量及累计帮助次数。

## 技术栈

### 前端 (Frontend)

- **开发工具**：微信开发者工具
- **框架**：微信原生开发 (WXML, WXSS, JavaScript)
- **图标**：FontAwesome / SVG 图标库
- **API**：微信小程序原生 API (位置、相机、支付、登录等)

### 后端 (Backend)

- **运行环境**：Node.js
- **Web 框架**：Express
- **数据库**：MySQL (mysql2)
- **反向代理**：Nginx
- **服务托管**：Windows Server VPS

### 第三方服务 (Third-party Services)

- **图片存储**：ImgBB / OSS
- **AI/OCR**：第三方 OCR 与 AI 服务接口
- **地图服务**：腾讯地图 SDK

## 📁 项目结构

```text
.
├── custom-tab-bar/        # 自定义底部导航栏
├── image/                 # 项目静态图片资源
├── pages/                 # 前端核心页面
│   ├── index/             # 发布页
│   ├── lostAndFound/      # 首页
│   ├── comment/           # 论坛页
│   ├── message/           # 消息页
│   └── my/                # 个人中心
├── subpkg/                # 分包页面 (设置、聊天、详情、实名等)
├── vps-server/            # 后端 Express 代码
│   ├── config/            # 数据库与全局配置
│   ├── controllers/       # 业务逻辑控制层
│   ├── routes/            # 路由定义
│   ├── services/          # 第三方服务接入 (AI, OCR, ImgBB)
│   ├── utils/             # 工具函数 (内容过滤、等级计算)
│   └── app.js             # 服务入口文件
├── app.json               # 小程序全局配置
├── database_design.md     # 数据库设计文档
└── project.config.json    # 小程序项目配置文件
```

## 快速开始

### 1. 数据库配置

1. 安装 MySQL 8.0+ 数据库。
2. 根据 `database_design.md` 中的 SQL 脚本创建表结构并初始化分类数据。
3. 在 `vps-server/config/db.js` 中配置您的数据库连接信息。

### 2. 后端部署

1. 进入 `vps-server` 目录：`cd vps-server`
2. 安装依赖：`npm install`
3. 启动服务：`npm start`
4. （可选）配置 Nginx 进行反向代理，建议开启 HTTPS。

### 3. 前端运行

1. 使用“微信开发者工具”导入项目根目录。
2. 修改 `app.js` 或相关工具类中的 API 基准地址（Base URL）为您的后端服务器地址。
3. 在小程序后台配置服务器域名白名单。
4. 编译并预览。
