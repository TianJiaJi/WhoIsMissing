# 谁没签到 (WhoIsMissing) - 智能名单比对工具

<div align="center">

![Who Is Missing](https://img.shields.io/badge/Who-Is_Missing-red?style=for-the-badge)
![Version](https://img.shields.io/badge/version-1.0.0-blue?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

**🔒 纯前端 · 零依赖 · 隐私安全 · 开箱即用**

[功能特点](#功能特点) • [快速开始](#快速开始) • [使用指南](#使用指南) • [部署方式](#部署方式)

</div>

---

## 📖 项目简介

**Who Is Missing** 是一个轻量级的 Excel 名单比对工具，专门用于活动考勤场景。只需上传"参考名单"（完整名单）和"实际名单"（签到表），即可快速识别未到人员。

### 适用场景
- 🎓 **班级活动考勤** - 快速找出未参加活动的学生
- 🏢 **公司会议签到** - 对比报名名单与实际到场人员  
- 📋 **培训课程考勤** - 自动识别缺席人员
- 🎪 **志愿者活动** - 高效管理大型活动签到

---

## ✨ 功能特点

### 核心功能
- ✅ **智能列识别** - 自动定位"姓名"列，无需手动选择
- 🔍 **智能内容过滤** - 自动排除表头、提示文字等非姓名内容
- 📊 **实时统计** - 显示总人数、已到人数、未到人数
- ⚡ **高性能** - 使用 Set 数据结构，10万行数据秒级响应
- 📱 **响应式设计** - 完美适配桌面端和移动端

### 安全特性
- 🔒 **100% 本地处理** - 所有数据在浏览器端完成，不上传任何信息
- 🛡️ **隐私保护** - 名单信息绝不离开你的设备
- 📴 **离线可用** - 下载后可断网使用（首次加载需 CDN）

### 用户体验
- 🎨 **现代化 UI** - 渐变背景、玻璃态卡片、流畅动画
- 🖱️ **拖拽上传** - 支持拖拽文件上传，一键操作
- 📥 **格式支持** - 支持 `.xlsx` 和 `.xls` 格式
- ⚠️ **错误提示** - 友好的错误提示和格式校验

---

## 🚀 快速开始

### 方式一：直接使用（推荐）

1. **下载文件**
   ```bash
   git clone https://github.com/你的用户名/WhoIsMissing.git
   cd WhoIsMissing
   ```

2. **双击打开**
   - 直接双击 `index.html` 文件
   - 或在浏览器中打开该文件

3. **开始使用**
   - 上传参考名单（完整名单）
   - 上传实际名单（签到表）
   - 点击"开始比对"查看结果

### 方式二：本地服务器

```bash
# 使用 Python 启动本地服务器
python -m http.server 8000

# 或使用 Node.js
npx serve

# 访问 http://localhost:8000
```

---

## 📚 使用指南

### 准备工作

确保你的 Excel 文件满足以下条件：

✅ **文件格式**：`.xlsx` 或 `.xls`  
✅ **姓名列**：表头必须包含"姓名"、"Name"或"名字"  
✅ **数据完整**：姓名列不能有过多空行或无效数据  

### 操作步骤

#### 第一步：上传参考名单
点击"📖 参考名单"区域，上传完整的报名名单或应到人员名单。

#### 第二步：上传实际名单  
点击"✅ 实际名单"区域，上传活动签到表或已到人员名单。

#### 第三步：开始比对
两个文件上传完成后，点击"🔍 开始比对"按钮。

#### 第四步：查看结果
- **统计卡片** - 显示总人数、已到人数、未到人数
- **未到名单** - 清晰列出所有未到人员
- **全员到齐** - 若无人缺席，显示"✅ 全员到齐"

### 结果示例

```
总人数（参考名单）: 42
已到人数          : 38
未到人数          : 4

未到人员:
┌─────────┐
│ 王小明   │
│ 李华     │  
│ 张伟     │
│ 刘洋     │
└─────────┘
```

---

## 🌐 部署方式

### GitHub Pages 部署

1. **创建仓库**
   ```bash
   # 在 GitHub 上创建新仓库 WhoIsMissing
   # 然后在本地执行：
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/你的用户名/WhoIsMissing.git
   git push -u origin main
   ```

2. **启用 Pages**
   - 进入仓库 **Settings** → **Pages**
   - Source 选择 **Deploy from a branch**
   - 分支选择 `main`，文件夹选择 `/root`
   - 点击 **Save**

3. **访问应用**
   ```
   https://你的用户名.github.io/WhoIsMissing/
   ```

### Vercel 部署

1. **安装 Vercel CLI**
   ```bash
   npm install -g vercel
   ```

2. **部署项目**
   ```bash
   vercel
   ```

3. **完成部署**  
   按提示操作，几秒后获得访问链接

### Netlify 部署

1. **访问 Netlify**
   - 打开 [netlify.com](https://netlify.com)
   -拖拽 `index.html` 所在文件夹到页面

2. **完成部署**
   - 自动生成访问链接

---

## 🔧 高级定制

### 修改姓名所在列

如果 Excel 的姓名列不在第一列，工具会自动识别。如需手动修改：

```javascript
// 找到第 420 行左右的代码
// 修改姓名列索引（0 = 第一列，1 = 第二列，以此类推）
const nameColumnIndex = 3; // 修改姓名在第4列
```

### 添加过滤关键词

如需过滤更多非姓名内容：

```javascript
// 在第 380 行左右添加关键词
const excludeKeywords = [
    '姓名', '活动', '时间',
    '你的关键词1',  // 在这里添加
    '你的关键词2'   // 在这里添加
];
```

### 自定义样式

```css
/* 修改主题颜色 */
:root {
    --primary: #6366f1;        /* 主色调 */
    --success: #10b981;         /* 成功色 */
    --warning: #f59e0b;         /* 警告色 */
    --danger: #ef4444;          /* 危险色 */
}
```

---

## 🛠️ 技术栈

- **前端框架**：原生 JavaScript (Vanilla JS)
- **Excel 解析**：[SheetJS (xlsx)](https://cdn.sheetjs.com/)
- **样式设计**：现代 CSS3 (Grid + Flexbox)
- **构建工具**：无需构建，零依赖

### 核心技术
- **Set 数据结构** - O(n) 时间复杂度的高效比对
- **FileReader API** - 本地文件读取
- **响应式设计** - CSS Grid + Media Queries
- **CSS 变量** - 主题化设计系统

---

## 📊 性能表现

| 数据量 | 比对时间 | 内存占用 |
|--------|----------|----------|
| 1,000  | < 0.1s   | ~2MB     |
| 10,000 | < 0.5s   | ~8MB     |
| 50,000 | < 2s     | ~25MB    |
| 100,000| < 5s     | ~45MB    |

*测试环境：Chrome 120, M1 Pro, 16GB RAM*

---

## ❓ 常见问题

<details>
<summary><b>Q: 数据会上传到服务器吗？</b></summary>
<br>

**A:** 不会。所有数据处理都在你的浏览器本地完成，没有任何网络请求上传数据。名单信息完全保密。
</details>

<details>
<summary><b>Q: 支持哪些 Excel 格式？</b></summary>
<br>

**A:** 支持 `.xlsx` (Excel 2007+) 和 `.xls` (Excel 97-2003) 格式。不支持 CSV 格式。
</details>

<details>
<summary><b>Q: 可以处理多大的文件？</b></summary>
<br>

**A:** 理论上无限制，但建议不超过 10MB（约 5-10万行）。超大文件可能导致浏览器卡顿。
</details>

<details>
<summary><b>Q: 为什么有些姓名没被识别？</b></summary>
<br>

**A:** 工具会自动过滤包含关键词的内容。确保：
1. 表头包含"姓名"字段
2. 姓名格式为 2-10 个中文字符
3. 不包含"活动"、"时间"等过滤关键词
</details>

<details>
<summary><b>Q: 可以导出比对结果吗？</b></summary>
<br>

**A:** 当前版本不支持导出。你可以手动复制未到名单，或等待后续版本更新。
</details>

<details>
<summary><b>Q: 手机上可以使用吗？</b></summary>
<br>

**A:** 可以。工具采用响应式设计，完美支持手机、平板、电脑等各种设备。
</details>

---

## 🔮 未来计划

- [ ] 支持导出未到名单为 CSV/Excel
- [ ] 添加多列匹配（姓名+学号）
- [ ] 支持模糊匹配（同音字、简繁体）
- [ ] 历史记录保存（LocalStorage）
- [ ] 批量处理多个活动
- [ ] 数据可视化图表
- [ ] 深色模式主题
- [ ] 多语言支持

---

## 🤝 贡献指南

欢迎贡献代码、报告问题或提出建议！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

---

## 📄 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件

---

## 👨‍💻 作者

**TianJiaJi** - GitHub [@TianJiaJi](https://github.com/TianJiaJi)

---

## 🙏 致谢

- [SheetJS](https://sheetjs.com/) - 强大的 Excel 解析库
- [GitHub Pages](https://pages.github.com/) - 免费静态托管
- 所有贡献者和用户

---

<div align="center">

**如果这个项目对你有帮助，请给个 ⭐ Star 支持一下！**

Made with ❤️ by TianJiaJi

</div>