# 🚀 Yong Wang's Tech Blog

王勇的个人技术博客，基于Hexo + NexT主题构建，专注于全栈开发经验分享与技术洞察。

## ✨ 博客特色

- 📝 **技术分享**: 深入的技术文章和项目实战经验
- 🎨 **现代设计**: 使用NexT主题，简洁美观的界面
- 📱 **响应式布局**: 完美适配桌面和移动设备
- 🔍 **SEO优化**: 搜索引擎友好的配置
- 💬 **社交集成**: 集成LinkedIn等社交平台链接

## 🛠️ 技术栈

- **静态站点生成器**: [Hexo](https://hexo.io/)
- **主题**: [NexT](https://theme-next.js.org/)
- **部署**: GitHub Pages
- **版本控制**: Git + GitHub

## 📚 博客内容

### 技术分享
- 全栈开发经验和最佳实践
- 项目架构设计和技术选型
- 开源项目开发心得
- 新技术学习和应用

### 项目实战
- Markdown + Mermaid 预览服务
- 端口监控工具开发
- 游戏开发经验分享
- 更多实战项目...

## 🚀 本地开发

### 环境要求
- Node.js >= 14.0.0
- npm 或 yarn

### 安装依赖
```bash
# 克隆项目
git clone https://github.com/wangyong-chengdu/tech-blog.git
cd tech-blog

# 安装依赖
npm install
```

### 本地预览
```bash
# 生成静态文件
hexo generate

# 启动本地服务器
hexo server

# 访问 http://localhost:4000/tech-blog/
```

### 创建新文章
```bash
# 创建新文章
hexo new post "文章标题"

# 创建新页面
hexo new page "页面名称"
```

## 📦 部署

### GitHub Pages 部署

1. 安装部署插件
```bash
npm install hexo-deployer-git --save
```

2. 配置 `_config.yml`
```yaml
deploy:
  type: git
  repo: https://github.com/wangyong-chengdu/tech-blog.git
  branch: gh-pages
```

3. 部署到GitHub Pages
```bash
hexo clean && hexo generate && hexo deploy
```

## 📁 项目结构

```
tech-blog/
├── _config.yml          # Hexo配置文件
├── package.json         # 项目依赖
├── scaffolds/           # 文章模板
├── source/              # 源文件目录
│   ├── _posts/         # 博客文章
│   └── about/          # 关于页面
├── themes/              # 主题目录
│   └── next/           # NexT主题
└── public/              # 生成的静态文件
```

## ⚙️ 配置说明

### 站点配置
- **标题**: Yong Wang's Tech Blog
- **副标题**: 技术分享 | 开源项目 | 个人成长
- **语言**: 中文 (zh-CN)
- **时区**: Asia/Shanghai

### 主题配置
- **主题**: NexT v8.23.2
- **布局**: 简洁现代的设计
- **功能**: 代码高亮、搜索、评论等

## 🔗 相关链接

- **博客地址**: [https://wangyong-chengdu.github.io/tech-blog/](https://wangyong-chengdu.github.io/tech-blog/)
- **GitHub仓库**: [https://github.com/wangyong-chengdu/tech-blog](https://github.com/wangyong-chengdu/tech-blog)
- **个人LinkedIn**: [Yong Wang](https://www.linkedin.com/in/yong-wang-019783359/)
- **开源项目**: [markdown-mermaid-preview](https://github.com/wangyong-chengdu/markdown-mermaid-preview)

## 📞 联系方式

如果你对博客内容有任何问题或建议，欢迎通过以下方式联系我：

- 💼 **LinkedIn**: [Yong Wang](https://www.linkedin.com/in/yong-wang-019783359/)
- 🐙 **GitHub**: [wangyong-chengdu](https://github.com/wangyong-chengdu)
- 📧 **技术交流**: 欢迎在LinkedIn上联系讨论技术问题

## 📄 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

---

**感谢访问我的技术博客！** 🎉

希望我的分享能对你的技术成长有所帮助。如果你觉得内容有价值，欢迎Star⭐这个项目！