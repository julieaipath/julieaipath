---
title: "Claude for Word 小白使用指南"
datePublished: 2026-06-10T08:44:08.900Z
cuid: cmq7to4rs00000bjabt5j3dvo
slug: claude-for-word

---

4 月 10 日，Anthropic 发布 Claude for Word（Beta版）。简单说，它是一个装进 Microsoft Word 的官方插件，让 Claude AI 作为侧边栏直接出现在 word 文档旁边。

以前用 AI 改文档，你要：打开浏览器 → 复制文字 → 粘贴给 AI → 复制结果 → 粘回 Word → 修格式。现在有了 Claude for Word，整个流程全在 Word 里完成，选中文字、输入指令、Claude 直接修改，所有改动以 Word 原生「追踪修订」的形式呈现，你接受或拒绝就行了。

**核心功能有哪些？**

- 生成：根据你的要求生成新内容
  
- 编辑：修改选中段落，保留格式
  
- 修订：全文或局部润色、改写
  
- 一致性检查：扫描术语、编号、引用的统一性
  
- 跨应用共享上下文：与 Claude for Excel / PowerPoint 无缝联动
  

**注意**：目前 Beta 阶段仅向 Claude Team 和 Enterprise 用户开放，个人 Pro 用户暂时还不能用。

# 解决了哪些真实问题？

用 AI 工具改文档时，常常会遇到这些问题：

- **来回切换工具**：Word 文档 和 Web浏览器来回跳，内容来回复制粘贴还容易出错。
  
- **追踪修订混乱**：AI 输出一段内容，但到底改了哪里？你得自己对比，费时还容易漏。
  
- **格式全崩**：标题层级、编号、项目符号，AI 改完后经常需要重新调整。
  
- **协作效率低**：同事在评论里写意见，你还得一条条手动处理。
  
- **重复教 AI**：每次都要重新交代背景、风格、要求。
  

**Claude for Word 的解法**

- 所有操作在 Word 里完成，零切换
  
- 所有 AI 修改自动变成可审查的追踪修订，一键接受 / 拒绝
  
- 完全保留原有格式：标题、编号、样式
  
- 可以读取评论、批量处理同事意见
  
- 可以跨Word、Excel 和 PowerPoint 工作
  

# 怎么用？

## 第一步：安装插件（1 分钟搞定）

**前提条件**：Claude Team 或 Enterprise 账号 \+ Microsoft Word 桌面版（Windows Microsoft 365 2205 及以上，或 Mac 16\.61 及以上）。

1. 打开 Word，点击顶部菜单「插入」→「加载项」→「获取加载项」
  
2. 搜索「Claude by Anthropic」，点击「添加」
  
3. 安装完成后，Word 右侧会出现 Claude 侧边栏
  
4. 用 Claude Team / Enterprise 账号登录
  

## 场景 1：选中文字，快速改写

这是最基础的用法，改写某段文字内容。在文档里选择你想修改的段落，在右侧 Claude 侧边栏输入指令，比如：把这段改得更简洁、专业，保持原有结构，Claude 以「追踪修订」形式将修改插入文档，你点击 Word「审阅」选项卡，逐条接受或拒绝修改。

## 场景 2：用评论驱动修改

如果你们团队常用 Word 评论功能来提意见，Claude 这个功能可以读取评论，并在评论里回复说明。**特别适合**：领导 / 客户批注了一堆意见，你不想一条条手动改的情况。

## 场景 3：跨Word \+ Excel \+ PowerPoint工作

这是 Claude 插件最强的地方。Claude for Word 与 Claude for Excel 和 Claude for PowerPoint 共享上下文，Claude 可以在单个对话中将其他文档的内容输出到你的当前文档内容中。比如，你可以要求 Claude 从 Excel 中提取数字到 Word文档里面，或者将 Word 文档总结为 PowerPoint 中，这样就不用多个应用之间复制和粘贴。

# Claude for Word 和 Copilot

到这里你可能会问，微软已经有了Copilot，为什么还要做一个Claude for Word，他们有什么区别。本质上这2个工具没什么区别，都是为了提升文档写作效率。但是因为底层模型的不同导致输出结果略有区别。

**如果你需要“生态联动”**：比如让 AI 读取昨天的几封内部邮件，再结合电脑里的一个 Excel 报表，自动起草一份会议通知。那就用 **Copilot**，因为它能拿到微软生态的全局数据。

**如果你需要“深度创作”**：比如精修一份几万字的深度报告，处理非常抠字眼的法律条款。拥有极高文本细腻度的 **Claude **是目前的绝对王者。