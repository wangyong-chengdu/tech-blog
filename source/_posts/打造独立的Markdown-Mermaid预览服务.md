---
title: 打造独立的Markdown+Mermaid预览服务
date: 2025-08-04 11:01:13
tags: [Node.js, Express, Markdown, Mermaid, 开源项目]
categories: [技术分享, 项目实战]
description: 从零开始构建一个功能完整的Markdown预览服务，支持Mermaid图表渲染、目录扫描和文件上传
---

## 项目背景

在日常开发工作中，经常需要预览Markdown文档，特别是包含Mermaid图表的技术文档。虽然市面上有很多Markdown编辑器，但大多数要么功能过于复杂，要么缺乏对Mermaid图表的良好支持。因此，我决定开发一个轻量级、专注的Markdown预览服务。

## 技术选型

### 后端技术栈
- **Node.js + Express**: 轻量级Web框架，快速搭建服务
- **Marked**: 高性能Markdown解析器
- **Multer**: 处理文件上传的中间件
- **fs-extra**: 增强的文件系统操作库

### 前端技术栈
- **原生HTML/CSS/JavaScript**: 保持轻量，避免框架依赖
- **Mermaid.js**: 强大的图表渲染引擎
- **响应式设计**: 支持移动端访问

## 核心功能实现

### 1. 本地目录扫描

```javascript
function scanDirectory(dirPath) {
    const files = [];
    
    function scan(currentPath) {
        const items = fs.readdirSync(currentPath);
        
        items.forEach(item => {
            const fullPath = path.join(currentPath, item);
            const stat = fs.statSync(fullPath);
            
            if (stat.isDirectory()) {
                scan(fullPath); // 递归扫描子目录
            } else if (path.extname(item).toLowerCase() === '.md') {
                files.push({
                    name: item,
                    path: fullPath,
                    size: stat.size,
                    modified: stat.mtime
                });
            }
        });
    }
    
    scan(dirPath);
    return files;
}
```

### 2. Mermaid图表渲染

前端集成Mermaid.js，实现图表的实时渲染：

```javascript
// 初始化Mermaid配置
mermaid.initialize({
    startOnLoad: true,
    theme: 'default',
    securityLevel: 'loose',
    fontFamily: 'Arial, sans-serif'
});

// 渲染Markdown内容
function renderMarkdown(content) {
    const html = marked(content);
    document.getElementById('preview').innerHTML = html;
    
    // 重新渲染Mermaid图表
    mermaid.init(undefined, document.querySelectorAll('.language-mermaid'));
}
```

### 3. 文件上传处理

使用Multer中间件处理文件上传：

```javascript
const upload = multer({
    dest: 'uploads/',
    fileFilter: (req, file, cb) => {
        const allowedTypes = ['.md', '.markdown'];
        const ext = path.extname(file.originalname).toLowerCase();
        cb(null, allowedTypes.includes(ext));
    },
    limits: {
        fileSize: 10 * 1024 * 1024 // 10MB限制
    }
});

app.post('/api/upload', upload.array('files'), (req, res) => {
    const uploadedFiles = req.files.map(file => ({
        originalName: file.originalname,
        filename: file.filename,
        path: file.path,
        size: file.size
    }));
    
    res.json({ success: true, files: uploadedFiles });
});
```

## 项目亮点

### 🎯 用户体验优化
1. **直观的界面设计**: 清晰的功能分区，操作简单明了
2. **实时预览**: 无需刷新页面，即时查看渲染效果
3. **响应式布局**: 完美适配桌面和移动设备
4. **错误处理**: 友好的错误提示和异常处理

### ⚡ 性能优化
1. **静态资源缓存**: 合理设置缓存策略
2. **文件大小限制**: 防止大文件影响性能
3. **异步处理**: 非阻塞的文件操作

### 🔒 安全考虑
1. **路径验证**: 防止目录遍历攻击
2. **文件类型检查**: 只允许Markdown文件上传
3. **输入验证**: 严格的参数校验

## 部署与使用

### 本地运行
```bash
# 克隆项目
git clone https://github.com/wangyong-chengdu/markdown-mermaid-preview.git
cd markdown-mermaid-preview

# 安装依赖
npm install

# 启动服务
npm start
```

### 功能演示
1. **目录扫描**: 输入本地路径，一键扫描所有Markdown文件
2. **文件上传**: 支持批量上传，自动生成预览链接
3. **图表渲染**: 完美支持各种Mermaid图表类型

## 技术收获

通过这个项目，我深入学习了：

1. **Node.js生态**: 熟练使用Express框架和相关中间件
2. **文件系统操作**: 掌握了文件读写、目录遍历等核心技能
3. **前后端交互**: 实现了完整的API设计和前端调用
4. **用户体验设计**: 注重界面友好性和操作便利性
5. **项目工程化**: 从开发到部署的完整流程

## 未来规划

- [ ] 添加主题切换功能
- [ ] 支持更多图表类型
- [ ] 集成代码高亮
- [ ] 添加文档搜索功能
- [ ] 支持在线编辑

## 项目链接

- **GitHub仓库**: [markdown-mermaid-preview](https://github.com/wangyong-chengdu/markdown-mermaid-preview)
- **在线演示**: 本地运行 `http://localhost:3003`
- **技术交流**: [LinkedIn](https://www.linkedin.com/in/yong-wang-019783359/)

---

这个项目不仅解决了我的实际需求，也是一次很好的技术实践。通过开源分享，希望能帮助到更多有类似需求的开发者。如果你对项目有任何建议或想法，欢迎通过GitHub Issues或LinkedIn与我交流！
