# Keep Green Day 🌱

[English](#english) | [中文](#chinese)

---

<a name="english"></a>
## English

### 🎯 About

> A commit a day keeps your girlfriend away and keep building! 💚

This repository helps you maintain a green GitHub contribution graph automatically using GitHub Actions. It creates daily commits to ensure your contribution streak never breaks, keeping your profile looking active and consistent.

Inspired by [inmayday/inmayday2023](https://github.com/inmayday/inmayday2023) - a project that humorously acknowledges the trade-off between maintaining a perfect GitHub streak and personal relationships.

### ✨ Features

- 🤖 **Automated Daily Commits**: Automatically creates commits at your specified time
- ⏰ **Customizable Schedule**: Set your preferred commit time using cron syntax
- 🔧 **Zero Maintenance**: Once set up, it runs completely hands-free
- 📊 **Perfect Green Graph**: Never miss a day of contributions
- 🚀 **GitHub Actions Powered**: Reliable and free automation

### 📋 Prerequisites

- A GitHub account
- A repository (this one or your own)
- Basic understanding of GitHub Actions (optional)

### 🚀 Quick Start

#### Option 1: Use This Repository

1. **Fork this repository** (Note: Commits to forked repos won't count as contributions!)
2. **Create your own repository** instead:
   ```bash
   git clone https://github.com/0xjayfi/keepgreenday.git
   cd keepgreenday
   rm -rf .git
   git init
   git add .
   git commit -m "Initial commit"
   ```
3. **Create a new repository on GitHub**
4. **Push to your repository**:
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```

#### Option 2: Add to Existing Repository

1. **Create workflow directory**:
   ```bash
   mkdir -p .github/workflows
   ```

2. **Create workflow file** `.github/workflows/auto-commit.yml`:
   ```yaml
   name: Auto Commit

   on:
     push:
       branches:
         - main
     schedule:
       # Runs at 00:00 UTC every day
       - cron: "0 0 * * *"

   jobs:
     autogreen:
       runs-on: ubuntu-latest

       permissions:
         contents: write

       steps:
         - name: Clone repository
           uses: actions/checkout@v3

         - name: Auto green
           run: |
             git config --local user.email "your-email@example.com"
             git config --local user.name "Your Name"
             git remote set-url origin https://${{ github.actor }}:${{ secrets.GITHUB_TOKEN }}@github.com/${{ github.repository }}
             git pull --rebase
             git commit --allow-empty -m "a commit a day keeps your girlfriend away and keep building"
             git push
   ```

3. **Customize the configuration**:
   - Change `your-email@example.com` to your GitHub email
   - Change `Your Name` to your GitHub username
   - Adjust the cron schedule if needed

4. **Push to GitHub**:
   ```bash
   git add .
   git commit -m "Add auto-commit workflow"
   git push
   ```

### ⚙️ Configuration

#### Scheduling (Cron Syntax)

The schedule uses cron syntax. Here are some examples:

- `"0 0 * * *"` - Every day at 00:00 UTC
- `"0 12 * * *"` - Every day at 12:00 UTC
- `"30 8 * * 1-5"` - Weekdays at 08:30 UTC
- `"0 9,18 * * *"` - Twice daily at 09:00 and 18:00 UTC

#### Timezone Calculation

GitHub Actions uses UTC time. To calculate your local time:
- **UTC+8 (Beijing/Singapore)**: 6:00 AM local = 22:00 UTC (previous day)
- **UTC-5 (EST)**: 6:00 AM local = 11:00 UTC
- **UTC+0 (London)**: 6:00 AM local = 6:00 UTC

### 📊 Monitoring

1. Go to your repository on GitHub
2. Click on the **Actions** tab
3. View workflow runs and their status
4. Check your contribution graph on your profile

### ⚠️ Important Notes

- **Don't Fork**: Forking won't count toward your contributions. Create your own repository instead.
- **Private Repos**: Commits to private repositories only show on your profile if you've enabled "Show private contributions"
- **GitHub Token**: The workflow uses the built-in `GITHUB_TOKEN` - no additional setup required
- **Rate Limits**: GitHub Actions has usage limits on the free tier (2000 minutes/month for private repos)

### 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest new features
- Submit pull requests

### 📜 License

This project is released under the MIT License. See [LICENSE](LICENSE) file for details.

### 🙏 Acknowledgments

- Inspired by [inmayday/inmayday2023](https://github.com/inmayday/inmayday2023)
- Thanks to all contributors who help maintain their green squares!

### ⚡ Fun Fact

> "Once maintained 200+ days of all green, but neglected my girlfriend" - Anonymous Developer

Remember: While maintaining a green contribution graph is satisfying, don't forget to maintain your relationships too! 💚

---

<a name="chinese"></a>
## 中文

### 🎯 关于

> 每天一提交，女友远离你，但代码不停歇！ 💚

这个仓库帮助你使用 GitHub Actions 自动保持绿色的 GitHub 贡献图。它每天创建提交，确保你的贡献连续性不会中断，让你的个人资料看起来始终活跃。

灵感来自 [inmayday/inmayday2023](https://github.com/inmayday/inmayday2023) - 一个幽默地承认了保持完美 GitHub 连续性和个人关系之间权衡的项目。

### ✨ 特性

- 🤖 **自动每日提交**：在指定时间自动创建提交
- ⏰ **可自定义时间**：使用 cron 语法设置你喜欢的提交时间
- 🔧 **零维护**：一次设置，永久运行
- 📊 **完美绿色图表**：永不错过一天的贡献
- 🚀 **GitHub Actions 驱动**：可靠且免费的自动化

### 📋 前置要求

- 一个 GitHub 账号
- 一个仓库（这个或你自己的）
- 对 GitHub Actions 的基本了解（可选）

### 🚀 快速开始

#### 方案 1：使用这个仓库

1. **Fork 这个仓库**（注意：Fork 的仓库提交不计入贡献！）
2. **创建你自己的仓库**：
   ```bash
   git clone https://github.com/0xjayfi/keepgreenday.git
   cd keepgreenday
   rm -rf .git
   git init
   git add .
   git commit -m "Initial commit"
   ```
3. **在 GitHub 上创建新仓库**
4. **推送到你的仓库**：
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```

#### 方案 2：添加到现有仓库

1. **创建工作流目录**：
   ```bash
   mkdir -p .github/workflows
   ```

2. **创建工作流文件** `.github/workflows/auto-commit.yml`：
   ```yaml
   name: Auto Commit

   on:
     push:
       branches:
         - main
     schedule:
       # 每天 UTC 00:00 运行
       - cron: "0 0 * * *"

   jobs:
     autogreen:
       runs-on: ubuntu-latest

       permissions:
         contents: write

       steps:
         - name: Clone repository
           uses: actions/checkout@v3

         - name: Auto green
           run: |
             git config --local user.email "your-email@example.com"
             git config --local user.name "Your Name"
             git remote set-url origin https://${{ github.actor }}:${{ secrets.GITHUB_TOKEN }}@github.com/${{ github.repository }}
             git pull --rebase
             git commit --allow-empty -m "a commit a day keeps your girlfriend away and keep building"
             git push
   ```

3. **自定义配置**：
   - 将 `your-email@example.com` 改为你的 GitHub 邮箱
   - 将 `Your Name` 改为你的 GitHub 用户名
   - 根据需要调整 cron 时间表

4. **推送到 GitHub**：
   ```bash
   git add .
   git commit -m "添加自动提交工作流"
   git push
   ```

### ⚙️ 配置

#### 时间调度（Cron 语法）

时间表使用 cron 语法。以下是一些示例：

- `"0 0 * * *"` - 每天 UTC 00:00
- `"0 12 * * *"` - 每天 UTC 12:00
- `"30 8 * * 1-5"` - 工作日 UTC 08:30
- `"0 9,18 * * *"` - 每天两次，UTC 09:00 和 18:00

#### 时区计算

GitHub Actions 使用 UTC 时间。计算你的本地时间：
- **UTC+8（北京/新加坡）**：本地早上 6:00 = UTC 22:00（前一天）
- **UTC-5（美东时间）**：本地早上 6:00 = UTC 11:00
- **UTC+0（伦敦）**：本地早上 6:00 = UTC 6:00

### 📊 监控

1. 前往你的 GitHub 仓库
2. 点击 **Actions** 标签
3. 查看工作流运行状态
4. 在你的个人资料页查看贡献图

### ⚠️ 重要提示

- **不要 Fork**：Fork 不会计入你的贡献。请创建你自己的仓库。
- **私有仓库**：私有仓库的提交只有在你启用"显示私有贡献"后才会显示在个人资料上
- **GitHub Token**：工作流使用内置的 `GITHUB_TOKEN` - 无需额外设置
- **速率限制**：GitHub Actions 免费层有使用限制（私有仓库每月 2000 分钟）

### 🤝 贡献

欢迎贡献！请随时：
- 报告错误
- 建议新功能
- 提交拉取请求

### 📜 许可证

本项目基于 MIT 许可证发布。详情请见 [LICENSE](LICENSE) 文件。

### 🙏 致谢

- 灵感来自 [inmayday/inmayday2023](https://github.com/inmayday/inmayday2023)
- 感谢所有帮助维持绿色方块的贡献者！

### ⚡ 趣事

> "曾经保持了 200 多天全绿，但是冷落了女朋友" - 匿名开发者

记住：虽然保持绿色贡献图很令人满意，但别忘了维护你的人际关系！ 💚

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=0xjayfi/keepgreenday&type=Date)](https://star-history.com/#0xjayfi/keepgreenday&Date)

---

*Made with 💚 by developers who commit every day*