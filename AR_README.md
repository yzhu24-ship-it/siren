# 📱 AR手势交互原型 - Mobile AR Gesture Prototype

一个基于Web技术的手机AR手势交互原型，支持通过双手拍手冻结背景，并用手势与AR元素进行交互。

## ✨ 核心功能

### 1️⃣ 摄像头实时捕捉
- 📹 使用 WebRTC 访问手机摄像头
- 🔄 自动镜像翻转，提供自然的交互体验
- 📱 支持前后摄像头切换（默认后置）

### 2️⃣ 手势识别
- 🤖 基于 **MediaPipe Hands** 的高精度手势识别
- 👐 同时跟踪双手的 21 个关键点
- 🎯 实时手部骨架可视化（可切换调试模式）

### 3️⃣ 双手拍手检测
- 👏 智能检测双手快速接近动作
- ⏱️ 1秒冷却时间，避免误触发
- ✨ 拍手时显示动画特效

### 4️⃣ 背景冻结
- 📸 拍手瞬间捕获当前画面
- 🧊 冻结背景作为AR元素的基底
- 🔁 再次拍手可解冻并重置

### 5️⃣ AR元素交互
- ➕ 添加彩色AR圆球元素
- ✋ 用食指和拇指"捏取"手势拖动元素
- 💫 悬停时元素发光效果
- 🎨 随机颜色生成

## 🛠️ 技术栈

| 技术 | 用途 | 版本 |
|------|------|------|
| **MediaPipe Hands** | 手势识别 | Latest (CDN) |
| **HTML5 Canvas** | 图形渲染 | - |
| **WebRTC getUserMedia** | 摄像头访问 | - |
| **Vanilla JavaScript** | 核心逻辑 | ES6+ |
| **CSS3** | UI样式 | - |

## 📂 文件结构

```
siren/
├── ar-gesture.html        # AR手势交互原型（主文件）
├── index.html             # 社交人格切换器（原项目）
├── AR_README.md          # 本说明文档
└── 截屏2025-10-28 00.47.28.png
```

## 🚀 使用方法

### 方式一：直接打开（推荐）

1. **用手机浏览器打开文件**
   ```bash
   # 将 ar-gesture.html 部署到Web服务器
   # 或使用本地服务器（需要HTTPS）
   ```

2. **授权摄像头权限**
   - 浏览器会提示请求摄像头权限，点击"允许"

3. **等待模型加载**
   - 首次加载 MediaPipe 模型需要几秒钟
   - 加载完成后状态栏显示 "就绪"

### 方式二：本地服务器

```bash
# 使用 Python 启动简单服务器
python3 -m http.server 8000

# 或使用 Node.js
npx http-server -p 8000

# 然后在手机浏览器访问：
# http://你的电脑IP:8000/ar-gesture.html
```

> ⚠️ **重要**：由于摄像头需要安全上下文（HTTPS 或 localhost），请确保：
> - 本地测试：使用 `localhost` 或 `127.0.0.1`
> - 远程访问：使用 HTTPS 协议

## 🎮 操作指南

### 基础操作

| 操作 | 说明 |
|------|------|
| 👏 **双手拍手** | 冻结/解冻背景 |
| ➕ **点击"添加AR元素"** | 在画面中心添加彩色圆球 |
| ✋ **食指+拇指捏合** | 抓取并拖动AR元素 |
| 🔄 **点击"重置背景"** | 解冻背景并清除所有AR元素 |
| 🐛 **点击"切换调试"** | 显示/隐藏手部骨架 |

### 完整流程

1. **准备阶段**
   - 打开页面，允许摄像头权限
   - 等待手势识别模型加载完成

2. **冻结背景**
   - 将双手伸到摄像头前
   - 快速拍手一次
   - 看到拍手特效和"背景已冻结"提示

3. **添加AR元素**
   - 点击底部"添加AR元素"按钮
   - 彩色圆球出现在画面中心

4. **手势交互**
   - 用食指指向AR元素
   - 食指和拇指靠近（捏合手势）
   - 移动手部可拖动AR元素

5. **重置**
   - 再次拍手或点击"重置背景"
   - 返回实时摄像头画面

## 🔧 核心算法说明

### 拍手检测算法

```javascript
// 1. 获取双手手掌中心点（中指根部，关键点9）
const leftPalm = handsData.left.landmarks[9];
const rightPalm = handsData.right.landmarks[9];

// 2. 计算欧几里得距离
const distance = Math.sqrt(
    Math.pow(leftPalm.x - rightPalm.x, 2) +
    Math.pow(leftPalm.y - rightPalm.y, 2)
);

// 3. 检测快速接近（距离从大到小突变）
if (lastHandDistance > THRESHOLD && distance < THRESHOLD) {
    onClapDetected(); // 触发拍手事件
}
```

### 抓取手势判断

```javascript
// 判断食指尖端和拇指尖端的距离
const thumb = hand.landmarks[4];  // 拇指尖
const index = hand.landmarks[8];   // 食指尖

const distance = Math.sqrt(
    Math.pow(thumb.x - index.x, 2) +
    Math.pow(thumb.y - index.y, 2)
);

// 距离小于0.08认为是"捏取"手势
return distance < 0.08;
```

### MediaPipe 手部关键点索引

```
    8   12  16  20      (指尖)
    |   |   |   |
    7   11  15  19
    |   |   |   |
    6   10  14  18
    |   |   |   |
    5   9   13  17      (指根)
     \\  |   |   /
      \\ |   |  /
        0---4           (手腕 - 拇指)
```

## 🎯 应用场景

- 📚 **教育培训**：AR互动教学课件
- 🎮 **游戏娱乐**：体感游戏原型
- 🏠 **家居设计**：虚拟家具摆放
- 🛍️ **电商零售**：AR试穿试戴
- 🎨 **艺术创作**：空间涂鸦和绘画

## 🐛 已知问题和优化方向

### 当前限制

1. **性能优化**
   - 低端手机可能出现卡顿
   - 建议使用近两年发布的中高端手机

2. **光照条件**
   - 弱光环境下手势识别准确度下降
   - 建议在光线充足的环境使用

3. **手势识别**
   - 拍手检测需要双手同时在画面内
   - 手部遮挡会影响识别精度

### 未来改进

- [ ] 添加更多手势类型（OK手势、比心、摇手等）
- [ ] 支持3D AR对象（使用Three.js）
- [ ] 添加手势录制和回放功能
- [ ] 优化算法，降低延迟
- [ ] 添加多点触控支持
- [ ] AR元素的旋转和缩放
- [ ] 本地存储AR场景

## 🌐 浏览器兼容性

| 浏览器 | 版本 | 支持情况 |
|--------|------|----------|
| Chrome (Android) | 90+ | ✅ 完全支持 |
| Safari (iOS) | 14+ | ✅ 完全支持 |
| Firefox (Android) | 88+ | ⚠️ 部分支持 |
| Samsung Internet | 14+ | ✅ 完全支持 |
| Edge (Android) | 90+ | ✅ 完全支持 |

> 📝 建议使用最新版本的 Chrome 或 Safari 以获得最佳体验

## 🔒 隐私说明

- ✅ 所有处理均在本地完成，不上传任何数据
- ✅ 不会保存或记录摄像头画面
- ✅ MediaPipe 模型从 CDN 加载，首次需要网络连接
- ✅ 后续可离线使用（需浏览器缓存支持）

## 📖 参考资源

- [MediaPipe Hands 官方文档](https://google.github.io/mediapipe/solutions/hands.html)
- [WebRTC getUserMedia API](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia)
- [Canvas API 教程](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)

## 👨‍💻 开发者信息

**项目**：AR手势交互原型
**技术栈**：MediaPipe + HTML5 Canvas
**开发时间**：2025年12月
**许可证**：MIT

---

## 💡 快速故障排除

### 问题：摄像头无法访问

**解决方案**：
1. 检查浏览器权限设置
2. 确保使用 HTTPS 或 localhost
3. 尝试刷新页面重新授权

### 问题：手势识别不准确

**解决方案**：
1. 确保光线充足
2. 将手部完整展示在摄像头内
3. 保持手部稳定，不要移动过快

### 问题：拍手检测失灵

**解决方案**：
1. 确保双手都在画面内
2. 拍手动作要快速且明显
3. 等待1秒冷却时间后再次尝试

### 问题：页面加载缓慢

**解决方案**：
1. 首次加载需下载 MediaPipe 模型（~10MB）
2. 确保网络连接稳定
3. 后续访问会使用浏览器缓存

---

**🎉 祝使用愉快！如有问题，欢迎提交 Issue。**
