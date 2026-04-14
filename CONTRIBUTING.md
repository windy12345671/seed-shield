# 贡献指南

感谢您对种盾项目的关注！以下是参与贡献的指南。

## 🤝 行为准则

请阅读我们的 [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)，我们承诺维护一个友好、包容的开源社区。

## 🔀 Git 工作流

我们使用 GitHub Flow：

1. Fork 本仓库
2. 创建特性分支：`git checkout -b feature/your-feature`
3. 提交更改：`git commit -m 'Add: some feature'`
4. 推送到远程：`git push origin feature/your-feature`
5. 创建 Pull Request

## 📝 提交规范

我们遵循 [Conventional Commits](https://www.conventionalcommits.org/) 规范：

```
feat:     新功能
fix:      Bug 修复
docs:     文档更新
style:    代码格式（不影响功能）
refactor: 重构（不影响功能）
perf:     性能优化
test:     测试相关
chore:    构建/工具变更
```

示例：
```
feat(ai): 添加水稻品种识别模型
fix(evidence): 修复上链超时问题
docs(readme): 更新部署文档
```

## 🧪 开发规范

### 前端（微信小程序）

- 使用 WXML / WXSS / JavaScript 原生开发
- 遵循微信小程序开发规范
- 使用 ESLint 进行代码检查
- 所有页面需有对应的 `.js` / `.wxml` / `.wxss` / `.json`

### 后端

- Node.js：遵循 RESTful 规范设计 API
- Go：遵循 Go 官方代码规范
- 所有 API 接口需要有文档注释

### AI 模块

- Python 3.10+
- 使用 PyTorch 框架
- 模型文件单独存放，不提交到 Git
- 提供模型训练脚本和推理脚本

## 🐛 问题反馈

请使用 GitHub Issues 反馈问题：

- Bug 报告：使用 [Bug Report](.github/ISSUE_TEMPLATE/bug_report.yml) 模板
- 功能建议：使用 [Feature Request](.github/ISSUE_TEMPLATE/feature_request.yml) 模板
- 提问：打 `question` 标签

## ✅ PR 审核

- 所有 PR 需要至少 1 人审核
- CI 测试通过后方可合并
- 请保持提交历史整洁

## 📜 许可证

参与本项目即表示您同意您的贡献将基于 MIT 许可证开源。

---

再次感谢您的贡献！🙏
