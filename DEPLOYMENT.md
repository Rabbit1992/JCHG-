# 工资表系统部署指南

本文档提供了将工资表生成系统部署到不同平台的详细指南。

## 🚀 部署选项

### 1. Streamlit Cloud（推荐）

**优点：**
- 免费且易于使用
- 与 GitHub 无缝集成
- 自动部署和更新

**步骤：**

1. **准备 GitHub 仓库**
   ```bash
   git init
   git add .
   git commit -m "Initial commit: 工资表生成系统"
   git branch -M main
   git remote add origin https://github.com/yourusername/salarysheet_maker.git
   git push -u origin main
   ```

2. **部署到 Streamlit Cloud**
   - 访问 [share.streamlit.io](https://share.streamlit.io)
   - 使用 GitHub 账号登录
   - 点击 "New app"
   - 选择你的仓库和分支
   - 主文件路径：`salary_generator.py`
   - 点击 "Deploy"

3. **访问应用**
   - 部署完成后，你将获得一个 `https://yourapp.streamlit.app` 的 URL

### 2. Vercel 部署

**注意：** Streamlit 在 Vercel 上有一些限制，建议用于简单应用。

**步骤：**

1. **安装 Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **部署**
   ```bash
   vercel
   ```

3. **配置**
   - 框架预设：Other
   - 构建命令：`pip install -r requirements.txt`
   - 输出目录：留空
   - 安装命令：`pip install -r requirements.txt`

### 3. Heroku 部署

**步骤：**

1. **安装 Heroku CLI**
   - 下载并安装 [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)

2. **创建 Heroku 应用**
   ```bash
   heroku create your-app-name
   ```

3. **部署**
   ```bash
   git push heroku main
   ```

4. **打开应用**
   ```bash
   heroku open
   ```

## 📋 部署前检查清单

- [ ] 确保所有依赖都在 `requirements.txt` 中
- [ ] 测试应用在本地正常运行
- [ ] 检查文件路径是否正确
- [ ] 确保模板文件已包含在仓库中
- [ ] 验证 `.gitignore` 文件正确配置

## 🔧 环境变量

如果需要设置环境变量，可以在各平台的设置中添加：

- `PYTHONPATH=.`（Vercel 已在 vercel.json 中配置）

## 🌐 自定义域名

### Streamlit Cloud
- 不支持自定义域名
- 只能使用 `*.streamlit.app` 子域名

### Vercel
- 支持自定义域名
- 在 Vercel 控制台中添加域名

### Heroku
- 支持自定义域名（付费功能）
- 使用 `heroku domains:add yourdomain.com`

## 🇨🇳 国内访问建议

由于网络环境限制，建议国内用户：

1. **首选方案：** 使用国内云平台（阿里云、腾讯云等）
2. **备选方案：** Vercel（相对稳定）
3. **避免：** Streamlit Cloud（可能访问不稳定）

## 🐛 故障排除

### 常见问题

1. **模块导入错误**
   - 检查 `requirements.txt` 是否包含所有依赖
   - 确保 Python 版本兼容

2. **文件路径错误**
   - 使用相对路径
   - 确保文件存在于仓库中

3. **内存限制**
   - Vercel 有内存限制，大文件处理可能失败
   - 考虑优化数据处理逻辑

### 日志查看

- **Streamlit Cloud：** 在应用页面查看日志
- **Vercel：** 使用 `vercel logs` 命令
- **Heroku：** 使用 `heroku logs --tail` 命令

## 🔄 更新应用

所有平台都支持通过 Git 推送自动更新：

```bash
git add .
git commit -m "更新描述"
git push origin main
```

## 📞 技术支持

如果遇到部署问题，请检查：
1. 平台官方文档
2. 错误日志
3. 社区论坛

---

**注意：** 本指南基于当前版本编写，部署平台的功能和限制可能会发生变化，请参考官方最新文档。