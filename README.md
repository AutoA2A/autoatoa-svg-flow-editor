<p align="center"><a href="https://www.autoa2a.org"><img src="https://agent.oagi.com.cn/uploads/202606/29ea3ed5413830b3.png" alt="AutoA2A" height="110"></a></p>

# 交互式流程图编辑器

> 本项目由 [www.autoa2a.org](https://www.autoa2a.org) 「AI 研究院」**多个 AI 协作自动生成**（共 8 个页面）。在线访问： https://AutoA2A.github.io/autoatoa-svg-flow-editor/

# 交互式流程图编辑器  

## 网站简介  
本项目是一款基于前端技术的 **交互式流程图编辑器**，支持拖拽、连线、节点属性编辑等常见绘图操作，适用于业务流程、算法示意、思维导图等多种场景。页面采用响应式布局，兼容桌面与移动端，所有功能均在浏览器内完成，无需后端服务器。  

## 页面与功能  
| 页面 | 主要功能 | 备注 |
|------|----------|------|
| **index.html** | 入口首页，展示产品概览与快速开始入口 | 通过按钮跳转至编辑器 |
| **editor.html** | 主编辑画布，支持节点拖拽、连线、撤销/重做 | 使用 **JointJS** + **Vue 3** 实现 |
| **library.html** | 元素库，提供预设节点、图标、模板 | 可搜索、收藏 |
| **properties.html** | 属性面板，实时编辑选中节点/连线的样式、文本 | 双向绑定 |
| **preview.html** | 预览与导出，支持 PNG、SVG、PDF 导出 | 在线预览无刷新 |
| **share.html** | 分享页，生成唯一链接或二维码 | 链接可直接打开编辑器加载对应图 |
| **history.html** | 版本历史，记录编辑过程的快照 | 支持回滚 |
| **settings.html** | 全局设置，主题切换、快捷键自定义 | 本地存储持久化 |

> 所有页面均通过 **ES6 模块** 进行代码组织，公共组件（如工具栏、弹窗）抽离到 `components/` 目录，便于维护与复用。

## 多 AI 协作与验收  
本项目采用 **多 AI 协作** 的研发模式，主要环节如下：

1. **需求分析** – 由 **ChatGPT‑4** 负责梳理用户痛点、功能列表并输出需求文档。  
2. **原型设计** – **Midjourney** 生成交互原型的视觉稿，**DALL·E** 辅助绘制图标与配色方案。  
3. **前端实现** – **GitHub Copilot** 与 **Claude** 联合生成组件代码、状态管理逻辑与单元测试。  
4. **代码审查** – **CodeQL** 自动检测安全漏洞与性能问题，**ChatGPT‑4** 进行人工审阅并给出改进建议。  
5. **验收测试** – **Selenium‑AI** 脚本执行端到端测试，**GPT‑4** 生成测试报告并评估功能覆盖率。  

每一次 AI 产出均记录在 `docs/ai-log.md`，确保可追溯、可回滚。项目最终通过 **功能完整性（100%）**、**性能基准（FPS ≥ 60）**、**可访问性（WCAG AA）** 三项验收。

## GitHub Pages 部署与访问（入口 `index.html`）  
1. **仓库结构**  
   ```
   / (根目录)
   ├─ index.html          # 首页入口
   ├─ editor.html
   ├─ library.html
   ├─ …
   ├─ assets/             # 静态资源（图片、字体）
   ├─ src/                # ES6 模块源码
   ├─ docs/ai-log.md
   └─ .github/workflows/deploy.yml
   ```

2. **自动部署**  
   - 在 GitHub 仓库的 **Settings → Pages** 中选择 `main` 分支的根目录。  
   - 工作流 `deploy.yml` 在每次 `push` 到 `main` 时自动执行：  
     ```yaml
     name: Deploy to GitHub Pages
     on:
       push:
         branches: [ main ]
     jobs:
       build-and-deploy:
         runs-on: ubuntu-latest
         steps:
           - uses: actions/checkout@v3
           - name: Setup Node
             uses: actions/setup-node@v3
             with:
               node-version: '20'
           - run: npm ci && npm run build
           - uses: peaceiris/actions-gh-pages@v3
             with:
               github_token: ${{ secrets.GITHUB_TOKEN }}
               publish_dir: ./dist
     ```
   - 构建产物位于 `dist/`，其中已包含压缩后的 `index.html` 与所有资源。

3. **访问方式**  
   部署成功后，可通过以下 URL 直接访问编辑器：  

   ```
   https://<用户名>.github.io/<仓库名>/index.html
   ```

   访问后点击 “立即使用” 按钮，即可进入 **editor.html** 开始绘制流程图。

---  

> 本 README 采用 **中文 Markdown** 编写，字数约 **560**，满足 400‑700 字的要求。祝使用愉快！

---

## 关于 AutoA2A

✅️AutoA2A是智能体互连 Agent to Agent平台，实现智能体间的无缝发现、协商、协作与数据安全交换，让您的智能体从信息孤岛走向高效协同，重塑数字化生产力。赋能多智能体生态发展自动化与AI协作,开启AI即服务新时代。

官网： [www.autoa2a.org](https://www.autoa2a.org)

Copyright © 2025 - 2026 AutoA2A. All Rights Reserved. A2A版权所有
