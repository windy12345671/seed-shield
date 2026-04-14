# 🛡️ 种盾 Seed Shield

> **开源的植物新品种权智能保护平台** · Built with 💚 for the seed industry

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Platform: WeChat Mini Program](https://img.shields.io/badge/Platform-WeChat%20Mini%20Program-07C160)](https://developers.weixin.qq.com/miniprogram/dev/index.html)
[![Language: Chinese](https://img.shields.io/badge/Language-简体中文-blue.svg)](README.md)
[![GitHub Stars](https://img.shields.io/github/stars/your-org/seed-shield?style=social)](https://github.com/your-org/seed-shield/stargazers)

---

## 🌱 项目简介

**种盾** 是面向植物新品种权保护的开源技术平台。

我国作为世界最大的农业生产国，植物新品种权侵权现象日益严重，但维权成本高、证据固定难、品种鉴定专业性强——种盾应运而生。

平台整合 **AI 表型比对**、**区块链存证**、**品种权管理** 三大核心能力，帮助育种企业快速发现侵权、固定证据、高效维权。

> 🔗 **在线体验主页**: https://your-org.github.io/seed-shield
> 📱 **小程序码**: [扫码体验](#) （开发中）

---

## ✨ 核心功能

| 模块 | 功能描述 | 技术亮点 |
|------|----------|----------|
| 🔬 **AI 表型比对** | 上传疑似侵权作物图片，自动提取叶形/花色/穗型等表型特征，与品种数据库比对 | CNN 深度学习，30+ 作物品种识别 |
| ⛓ **区块链存证** | 拍摄即存证，图片 + GPS + 时间戳打包上链，生成不可篡改哈希 | Hyperledger Fabric 联盟链，司法有效 |
| 📋 **品种权管理** | 名下品种权列表、状态监控、年费到期提醒 | 全生命周期管理 |
| 📡 **侵权动态监控** | 多渠道信息监测，分级预警推送 | NLP + 关键词引擎 |
| ⚖️ **维权辅助** | 侵权分析报告自动生成，对接专业律师 | 证据链整理，维权方案建议 |
| 📖 **政策数据库** | 法规、司法判例、政策文件检索 | 全文检索 + 分类浏览 |

---

## 🏗️ 技术架构

```
┌─────────────────────────────────────────────────────┐
│                   用户层                             │
│            微信小程序 (原生开发)                      │
└──────────────────────┬──────────────────────────────┘
                       │ HTTPS / WSS
┌──────────────────────▼──────────────────────────────┐
│                  API 网关层                           │
│         Kong / Nginx (鉴权 + 路由 + 限流)             │
└──────┬──────────┬──────────────┬──────────────┬──────┘
       │          │              │              │
┌──────▼──┐ ┌─────▼──┐  ┌───────▼───┐  ┌──────▼──────┐
│ AI 服务  │ │ 存证服务 │  │ 品种权服务 │  │  用户服务   │
│ PyTorch  │ │  Go      │  │  Node.js   │  │  Node.js    │
└──────┬──┘ └─────┬──┘  └───────┬───┘  └──────┬──────┘
       │          │              │              │
┌──────▼──────────▼──────────────▼──────────────▼──────┐
│                    数据 / 基础设施层                    │
│   MySQL   Redis   MinIO   Hyperledger Fabric   S3    │
└────────────────────────────────────────────────────────┘
```

### 技术栈

| 层级 | 技术选型 |
|------|----------|
| 前端 | 微信小程序原生开发（WXML / WXSS / JS） |
| 后端 | Node.js (API) + Go (存证核心) |
| AI | Python 3.10 + PyTorch + OpenCV |
| 区块链 | Hyperledger Fabric 2.x |
| 数据库 | MySQL 8.0 + Redis 7.x |
| 存储 | MinIO (对象存储) |
| 部署 | Docker + Kubernetes |
| 监控 | Prometheus + Grafana |
| 云 | 腾讯云 / 阿里云 |

---

## 🚀 快速开始

### 前置依赖

- Node.js ≥ 18.x
- Python ≥ 3.10
- Docker & Docker Compose
- 微信开发者工具

### 1. 克隆项目

```bash
git clone https://github.com/your-org/seed-shield.git
cd seed-shield
```

### 2. 一键启动（Docker）

```bash
docker-compose up -d
```

### 3. 前端小程序

```bash
# 导入微信开发者工具
# 打开 zhongdun-miniprogram/ 目录
# 修改 app.js 中的 API_BASE_URL 为你的后端地址
```

### 4. 后端 API

```bash
cd server
cp .env.example .env
# 编辑 .env 配置数据库等信息
npm install
npm run dev
```

### 5. AI 服务

```bash
cd ai-service
pip install -r requirements.txt
python app.py
```

---

## 📁 项目结构

```
seed-shield/
├── zhongdun-miniprogram/     # 微信小程序前端
│   ├── pages/
│   │   ├── index/            # 首页
│   │   ├── evidence/         # 区块链取证
│   │   ├── variety/         # 品种权管理
│   │   ├── compare/          # AI 比对
│   │   └── profile/          # 个人中心
│   ├── assets/               # 静态资源
│   ├── utils/                # 工具函数
│   └── app.*                 # 全局配置
├── server/                   # 后端 API 服务 (Node.js)
│   ├── src/
│   │   ├── routes/           # 路由
│   │   ├── controllers/     # 控制器
│   │   ├── services/         # 业务逻辑
│   │   └── models/            # 数据模型
│   └── package.json
├── ai-service/               # AI 算法服务 (Python)
│   ├── models/               # 训练好的模型
│   ├── api/                  # FastAPI 接口
│   └── train/                # 训练脚本
├── blockchain/                # 区块链合约
│   └── fabric/               # Hyperledger Fabric 链码
├── docs/                     # 项目文档
├── assets/                   # 网站静态资源
└── README.md
```

---

## 🤝 参与贡献

我们欢迎所有形式的贡献！请查阅 [CONTRIBUTING.md](CONTRIBUTING.md) 了解详情。

### 如何贡献

1. **Fork** 本仓库
2. 创建你的特性分支 (`git checkout -b feature/amazing-feature`)
3. 提交更改 (`git commit -m 'Add some amazing feature'`)
4. 推送到分支 (`git push origin feature/amazing-feature`)
5. 创建 **Pull Request**

### 贡献者名单

<a href="https://github.com/your-org/seed-shield/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=your-org/seed-shield" width="120" />
</a>

---

## 🗺️ 发展路线

| 版本 | 状态 | 主要内容 |
|------|------|----------|
| v1.0 | ✅ 已完成 | MVP：AI 比对 + 区块链存证 + 品种权管理 |
| v2.0 | 🔄 开发中 | 侵权监控自动化 + 批量比对 + 维权报告 + 律师对接 |
| v3.0 | 📋 规划中 | 开放 API + 司法链跨链 + 多端 App + 品种权交易 |

---

## 📄 开源协议

本项目基于 **MIT License** 开源，您可以自由使用、修改和分发本项目代码，但需保留版权声明。

详见 [LICENSE](LICENSE) 文件。

---

## 🙏 致谢

- 感谢所有为种盾贡献代码和想法的开发者
- 感谢农业科学院专家团队的技术咨询
- 感谢微信团队提供的小程序开发框架
- 感谢所有 Star 和 Fork 本项目的朋友

---

<p align="center">
  <strong>用科技守护每一颗创新种子 🛡️🌱</strong>
</p>
