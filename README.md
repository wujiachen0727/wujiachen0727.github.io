# 晨知夜行 - 后端技术深度实践博客

基于 Hugo 和 PaperMod 主题构建的个人技术博客，专注于后端技术深度实践与分享。

## 🎯 博客定位

深耕Go语言生态，构建高性能分布式系统，探索云原生架构与AI工程化实践。

## 📚 内容系列

- **Go语言深度系列**：语言特性、并发编程、性能优化
- **分布式系统系列**：微服务架构、服务治理、一致性算法  
- **云原生技术系列**：Kubernetes、Docker、DevOps实践
- **AI工程化系列**：模型部署、MLOps、智能系统构建
- **技术管理系列**：团队协作、技术决策、工程效率

## 🛠️ 技术栈

- **静态站点生成器**：Hugo v0.149.0+
- **主题**：PaperMod
- **部署平台**：GitHub Pages
- **CI/CD**：GitHub Actions

## 🚀 本地开发

```bash
# 克隆仓库
git clone https://github.com/wujiachen0727/wujiachen0727.github.io.git

# 进入目录
cd wujiachen0727.github.io

# 初始化主题子模块
git submodule update --init --recursive

# 启动开发服务器
hugo server -D

# 构建生产版本
hugo --minify
```

## 📝 写作规范

- **实战导向**：基于真实项目经验
- **深度优先**：深入技术原理和最佳实践
- **代码完整**：提供可运行的示例代码
- **持续更新**：跟随技术发展不断迭代

## 🔧 自动化部署

使用 GitHub Actions 实现自动化构建和部署：

- 推送到 `main` 分支自动触发构建
- Hugo 构建静态文件
- 自动部署到 GitHub Pages

## 📄 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件
