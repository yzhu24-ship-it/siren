# Siren - AR决策训练系统

移动端AR手势交互原型集合，包含多个不同的AR决策训练系统。

## 🌐 纯网页版 - 电脑和手机都可直接使用

**✅ 100%纯网页应用 - 无需下载任何App**

Siren所有功能都在浏览器中运行，**不需要安装任何应用程序**：

- 💻 **电脑访问**：Chrome/Edge/Firefox/Safari浏览器直接打开网址
- 📱 **手机访问**：iOS Safari / Android Chrome 直接打开相同网址
- 📱 **平板访问**：iPad / Android平板完美支持
- 🌐 **统一入口**：所有设备访问同一个网址 `index.html`，自动检测设备类型并推荐最佳版本
- 🔄 **即时更新**：刷新页面即可获得最新功能
- 🔒 **隐私安全**：所有AI运算在您的设备本地进行，数据不上传服务器

**快速开始：**
1. 本地测试：`python -m http.server 8000` → 浏览器打开 `http://localhost:8000/`
2. 在线访问：部署到 GitHub Pages → `https://your-username.github.io/siren/`
3. 手机访问：与电脑在同一WiFi，手机浏览器打开电脑IP地址

**统一入口页面 `index.html` 功能：**
- 自动检测设备类型（电脑/手机/平板）
- 为当前设备推荐最适合的版本
- 展示所有5个版本的详细功能
- 提供完整的访问和部署说明

---

## 🚀 项目列表

### 1. AR手势交互原型
**入口:** [index-ar.html](index-ar.html)
**演示:** [ar-gesture.html](ar-gesture.html)

**特点:**
- 双手合十固定背景场景
- 6种手势交互模式
- 实时手势识别（MediaPipe Hands）
- Sobel边缘检测 + 区域着色

**手势列表:**
- 🙏 双手合十 - 固定背景场景
- ✊ 握拳 - 轮廓区域变色
- 👌 捏合 - AR元素虚拟化
- 🤟 摇滚 - 元素消失效果
- 🖐️ 展开手掌 - 显示信息面板
- 👆 指向 - 交换元素位置

---

### 2. AR决策训练教练（静态版）
**入口:** [index-trainer.html](index-trainer.html)
**演示:** [ar-decision-trainer.html](ar-decision-trainer.html)

**核心理念:**
不是告诉你往哪放，而是训练你快速决策的能力

**功能特性:**
- 📸 环境校准（15秒）- 双手合十扫描桌面，自动识别5-7个物品区域
- ⚡ 决策训练（60秒）- 每个物品3秒倒计时，手势快速决策
- 📊 决策回顾（30秒）- 获得评分、模式分析和个性化建议

**4种决策类型:**
- 👆 立即处理 - 需要马上行动
- 🖐️ 稍后处理 - 可以延后
- 🤟 丢弃 - 不再需要
- ✊ 归档 - 长期保存

**游戏机制:**
- 3秒倒计时 + 连击系统 + 压力值
- 决策模式分析（拖延型/完美型/冲动型/平衡型）
- Markdown格式待办清单导出

---

### 3. 动态AR决策教练（Phase 1原型）
**入口:** [index-dynamic.html](index-dynamic.html)
**演示:** [ar-dynamic-proto.html](ar-dynamic-proto.html)

**创新点:**
- 🔄 **持续扫描模式** - 无需固定背景，自由移动手机
- 🤖 **AI物品识别** - TensorFlow.js COCO-SSD识别80+类真实物品
- 🏷️ **实时AR标签** - 动态跟随物品移动
- 🎯 **自动聚焦** - 物体停留中心1秒自动触发决策

**Phase 1实现:**
- ✅ TensorFlow.js COCO-SSD模型加载
- ✅ 实时物品检测（杯子、书、手机等）
- ✅ 动态AR标签系统
- ✅ 中心聚焦区域检测
- ✅ 决策面板UI
- ✅ 基础统计追踪

**未来计划（Phase 2-3）:**
- 手势确认集成
- 音频反馈
- 训练仪表盘
- 决策模式分析
- 数据可视化

---

### 4. Mobile AR Palm Gesture Coach 🆕
**Entry:** [index-palm-mobile.html](index-palm-mobile.html)
**Demo:** [ar-magic-palm-mobile.html](ar-magic-palm-mobile.html)

**Core Innovation:**
Mobile-first AR system with palm gesture trigger and sequential processing

**Key Features:**
- 🤚 **Palm Gesture Summon** - Open palm + hold 1 second to trigger (prevents accidental activations)
- 🎯 **Center Focus Selection** - Align item with screen center (200px radius)
- 📋 **Sequential Processing** - One item at a time with visual progress tracking
- ✅ **Processed Item Tracking** - Checkmarks and grayscale for completed items
- 📱 **Mobile Optimized** - Landscape lock, touch-friendly buttons (100px+)
- 🔋 **Battery Efficient** - 300ms detection intervals, max 5 objects, 30 particles
- 👆 **Touch Fallback** - Direct button taps when gestures are difficult

**Interaction Flow:**
```
Scanning → Palm Open (1s) → Focus Item → Decision Panel → Gesture/Touch → Complete → Next
```

**Technical Highlights:**
- `PalmOpenDetector` class: All 5 fingers extended detection + 1-second hold validation
- `FocusItemSelector` class: Center proximity algorithm with pulsing visual feedback
- Sequential state machine: Set-based processed items tracking
- Mobile performance: Throttled detection (300ms), reduced particle count (30)
- Landscape enforcement: CSS media query + warning screen

**Mobile Requirements:**
- ✅ HTTPS deployment (GitHub Pages recommended)
- ✅ Landscape orientation (portrait shows warning)
- ✅ Modern mobile browser (Chrome 90+ / Safari 14+)
- ✅ Camera permission
- ✅ Good lighting for gesture accuracy

---

## 📋 技术栈

| 技术 | 用途 |
|------|------|
| **MediaPipe Hands** | 手势识别（21关键点追踪） |
| **TensorFlow.js COCO-SSD** | 物品识别（80+类别） |
| **Canvas API** | 多层渲染系统 |
| **Sobel算子** | 边缘检测 |
| **BFS洪水填充** | 区域着色 |
| **WebRTC getUserMedia** | 摄像头访问 |

---

## 🌐 部署

### 本地测试
```bash
# Python 3
python -m http.server 8000

# 然后访问
http://localhost:8000/index-ar.html
http://localhost:8000/index-trainer.html
http://localhost:8000/index-dynamic.html
http://localhost:8000/index-palm-mobile.html  # 🆕 Mobile version
```

### GitHub Pages部署 (推荐用于移动版)
1. 前往仓库 Settings → Pages
2. 选择分支（建议使用 `main` 或 `gh-pages`）
3. 点击 Save
4. 访问: `https://yzhu24-ship-it.github.io/siren/`

**重要：** Mobile Palm Gesture版本需要HTTPS才能访问摄像头。GitHub Pages自动提供HTTPS，是最佳部署选择。

### 移动端测试指南 (Mobile Palm Gesture)
1. **部署到HTTPS环境**（GitHub Pages或localhost）
2. **使用移动设备访问**（手机或平板）
3. **允许摄像头权限**
4. **切换到横屏模式**（竖屏会显示警告）
5. **确保光线充足**（提升手势识别准确度）
6. **测试手势：**
   - 张开手掌，5根手指完全展开
   - 手掌正对摄像头
   - 保持1秒钟，看到进度条填满
   - 屏幕中心物品会弹出决策面板
7. **备用方案：** 如果手势识别困难，可以直接点击按钮

---

## 📱 系统要求

- ✅ 现代移动浏览器（Chrome 90+ / Safari 14+）
- ✅ 摄像头访问权限
- ✅ HTTPS连接（本地开发可用HTTP）
- ✅ 稳定网络（首次加载MediaPipe/TensorFlow模型）
- ✅ 光线充足环境（提升识别准确度）

---

## 🎯 使用场景对比

| 场景 | 推荐版本 | 原因 |
|------|---------|------|
| 桌面整理 | 静态版 | 固定视角，批量决策 |
| 房间巡视 | 动态版 / Mobile Palm | 移动扫描，逐个处理 |
| 决策训练 | 静态版 | 完整游戏化机制 |
| 快速整理 | 动态版 | 实时识别，即扫即决 |
| 移动端AR | **Mobile Palm 🆕** | 专为手机优化，手势+触摸双模式 |
| 外出整理 | **Mobile Palm 🆕** | 移动设备，电池友好，触摸备用 |

---

## 📄 开源协议

MIT License

---

## 🔗 相关链接

- [MediaPipe Hands文档](https://google.github.io/mediapipe/solutions/hands.html)
- [TensorFlow.js COCO-SSD](https://github.com/tensorflow/tfjs-models/tree/master/coco-ssd)
- [整理决策理论](https://en.wikipedia.org/wiki/Tidying_Up)

---

**最后更新:** 2025-12-10
**版本:** v1.1.0 (新增Mobile Palm Gesture版本)
