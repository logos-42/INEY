# 🪙 INEY 个人代币发行平台 - 静态网站版本

基于Base主网的个人代币发行平台静态前端版本，适用于GitHub Pages部署。

## 🌟 功能特性

- **🚀 一键创建代币** - 在Base主网创建个人代币，费用仅0.001 ETH
- **💰 极低手续费** - 基于Base L2，交易成本大幅降低
- **🔗 智能合约集成** - 直接与部署在Base主网的智能合约交互
- **📱 响应式设计** - 支持桌面和移动设备访问
- **🔐 安全可靠** - 前端直接连接MetaMask，无后端风险

## 📋 已部署合约信息

### Base 主网 (Chain ID: 8453)

| 合约名称 | 地址 | 功能 |
|---------|------|------|
| SimpleTokenFactory | `0x09F80281c90d574B4C5769cf2308ea4B70b4f468` | 代币工厂，处理创建请求 |
| PersonalToken | `0xd3F54d1e5909a8ae1E15DBf1e27825e716B26d0E` | 代币模板，1M初始供应量 |
| SimpleAMM | `0x8C53A213B97B52989BCCE04fE306464e6767BC75` | 自动做市商合约 |

## 🚀 部署到GitHub Pages

### 方法一：GitHub Web界面部署

1. **创建新仓库**
   ```
   仓库名：personal-token-platform
   类型：Public
   ```

2. **上传文件**
   - 将 `static-web` 文件夹中的所有文件上传到仓库根目录
   - 确保 `index.html` 在根目录

3. **启用GitHub Pages**
   - 进入仓库设置 → Pages
   - Source 选择 "Deploy from a branch"
   - Branch 选择 "main"
   - 文件夹选择 "/ (root)"
   - 点击 "Save"

4. **访问网站**
   - 等待几分钟部署完成
   - 访问 `https://你的用户名.github.io/personal-token-platform`

### 方法二：Git命令行部署

```bash
# 1. 创建本地仓库
git init
git add .
git commit -m "Initial commit: Personal Token Platform"

# 2. 连接到GitHub远程仓库
git remote add origin https://github.com/你的用户名/personal-token-platform.git

# 3. 推送到GitHub
git branch -M main
git push -u origin main

# 4. 在GitHub上启用Pages（Web界面操作）
```

### 方法三：GitHub Desktop部署

1. 打开GitHub Desktop
2. File → New Repository
3. 选择 `static-web` 文件夹作为本地路径
4. Publish to GitHub
5. 在GitHub网站启用Pages

## 🔧 自定义配置

### 修改合约地址

如果需要连接不同的合约，编辑每个HTML文件中的 `NETWORK_CONFIG` 对象：

```javascript
const NETWORK_CONFIG = {
    chainId: 8453,
    name: "Base Mainnet",
    rpcUrl: "https://mainnet.base.org",
    explorer: "https://basescan.org",
    contracts: {
        TokenFactory: "你的TokenFactory地址",
        PersonalToken: "你的PersonalToken地址",
        SimpleAMM: "你的SimpleAMM地址"
    }
};
```

### 更换网络

如果需要部署到其他网络（如测试网），修改配置：

```javascript
// Base Sepolia 测试网示例
const NETWORK_CONFIG = {
    chainId: 84532,
    name: "Base Sepolia",
    rpcUrl: "https://sepolia.base.org",
    explorer: "https://sepolia.basescan.org",
    contracts: {
        // 测试网合约地址
    }
};
```

## 📁 文件结构

```
static-web/
├── index.html          # 首页
├── create.html         # 创建代币页面
├── dashboard.html      # 仪表板页面
├── README.md          # 说明文档
└── .gitignore         # Git忽略文件
```

## 🛠️ 技术栈

- **前端框架**: 纯HTML/CSS/JavaScript
- **UI组件**: Bootstrap 5.1.3
- **图标**: Font Awesome 6.0.0
- **区块链**: ethers.js 5.7.2
- **网络**: Base Mainnet (L2)
- **钱包**: MetaMask

## 🔗 相关链接

- [Base网络官网](https://base.org)
- [BaseScan区块链浏览器](https://basescan.org)
- [MetaMask钱包](https://metamask.io)
- [ethers.js文档](https://docs.ethers.io/v5/)

## 📝 使用说明

1. **连接钱包** - 点击"连接钱包"按钮，确保MetaMask已安装
2. **切换网络** - 自动提示切换到Base主网
3. **创建代币** - 填写代币信息，支付0.001 ETH创建费用
4. **查看统计** - 在仪表板查看平台统计和合约信息

## ⚠️ 注意事项

- 这是**Base主网**环境，使用真实ETH
- 创建代币需要支付0.001 ETH费用
- 确保钱包有足够ETH支付gas费用
- 代币创建后无法撤销，请谨慎操作

## 🆘 问题排查

### 常见问题

1. **网站无法访问**
   - 检查GitHub Pages是否已启用
   - 确认仓库是Public类型
   - 等待部署完成（通常需要5-10分钟）

2. **钱包连接失败**
   - 确认已安装MetaMask
   - 检查网络是否为Base主网
   - 刷新页面重试

3. **交易失败**
   - 检查钱包ETH余额
   - 确认网络连接稳定
   - 查看错误消息详情

## 🔄 更新部署

当需要更新网站时：

```bash
# 修改文件后
git add .
git commit -m "Update: 描述更改内容"
git push origin main
```

GitHub Pages会自动重新部署。

---

## 🎯 从Flask到静态网站的主要变化

1. **移除Flask依赖** - 不再需要Python后端
2. **配置静态化** - 将Flask模板变量替换为JavaScript配置
3. **路径修正** - 将Flask路由改为相对HTML文件路径
4. **API移除** - 移除后端API调用，直接在前端处理
5. **独立部署** - 可以部署到任何静态网站托管服务

现在你的个人代币平台可以完全独立运行，无需服务器！ 