# 地鼠单词游戏 (Mole Word Game)

一款结合打地鼠玩法和英语单词学习的H5教育游戏，适合小学1-6年级学生。

## 项目信息

- **项目名称**: dishuwordgame
- **在线体验**: https://dishuwordgame.netlify.app
- **GitHub仓库**: https://github.com/henrywangzy/dishuwordgame
- **技术栈**: HTML5 + CSS3 + JavaScript (单文件应用)

## 游戏概述

地鼠单词游戏是一款寓教于乐的英语学习游戏，通过翻卡片的方式学习英语单词。游戏采用5×3网格布局（共15张卡片），玩家需要在限定时间内快速识别并点击正确的英语单词卡片。

## 核心功能

### 1. 年级选择
- 支持小学1-6年级词汇
- 每个年级配有对应难度的词汇库
- 词汇包含英文、中文翻译和例句

### 2. 难度等级

游戏提供三种难度等级，主要区别在于同时翻开的卡片数量：

| 难度 | 翻开卡片数 | 停留时间 | 说明 |
|------|-----------|----------|------|
| 简单 | 2张 | 2秒 | 适合初学者，降低识别难度 |
| 中等 | 3张 | 2秒 | 中等挑战，需要快速反应 |
| 困难 | 4张 | 2秒 | 高难度，考验快速识别能力 |

### 3. 游戏机制

#### 基本规则
- **游戏时长**: 60秒倒计时
- **卡片布局**: 5行×3列，共15张卡片
- **翻牌机制**: 根据难度随机翻开2-4张卡片
- **自动翻回**: 卡片停留2秒后自动翻回，并翻出新的一组卡片
- **答对机制**: 点击正确单词后，立即翻回所有卡片并翻出新的一组
- **答错机制**: 点击错误单词后，卡片闪烁提示，游戏继续

#### 计分系统
- 答对一题：+10分
- 答错一题：-5分（最低0分）
- 实时显示当前分数、答对数、答错数

#### 特色功能
- **卡片必翻回**: 答对的卡片也会翻回，避免干扰，保持游戏公平性
- **目标单词必显示**: 每次翻牌时，目标单词的卡片一定会被翻开
- **语音朗读**: 答对后自动朗读单词（英文）和中文翻译
- **背景音乐**: 游戏过程中播放轻快背景音乐
- **音效反馈**: 答对、答错、游戏结束等都有对应音效

### 4. 暂停与重来

- **暂停功能**: 点击暂停按钮，游戏暂停，背景音乐停止，卡片停止翻转
- **继续游戏**: 点击继续按钮，游戏恢复，背景音乐继续播放
- **重来功能**: 点击重来按钮，立即结束当前游戏，返回难度选择页面

### 5. 游戏结束总结

游戏结束后显示详细的学习报告：

- **总分显示**: 显示本局游戏得分
- **统计数据**: 答对题数、答错题数
- **答对单词列表**: 显示所有答对的单词（英文 + 中文）
- **答错单词列表**: 显示所有答错的单词（英文 + 中文）
- 支持返回首页或再玩一次

## 技术实现

### 核心技术

1. **CSS 3D变换**
   - 使用`transform: rotateY(180deg)`实现卡片翻转效果
   - 卡片正反面采用`backface-visibility: hidden`隐藏背面

2. **Web Speech API**
   - 使用`SpeechSynthesisUtterance`实现单词语音朗读
   - 支持中英文混合朗读

3. **HTML5 Audio API**
   - 背景音乐循环播放
   - 音效系统（答对、答错、游戏结束）
   - 暂停时停止背景音乐

4. **JavaScript定时器**
   - `setTimeout`实现2秒自动翻回机制
   - `setInterval`实现60秒倒计时
   - 清除定时器避免内存泄漏

5. **状态管理**
   ```javascript
   let gameRunning = false;    // 游戏运行状态
   let gamePaused = false;     // 游戏暂停状态
   let autoFlipTimeout = null; // 自动翻回定时器
   let correctWords = [];      // 答对的单词记录
   let wrongWords = [];        // 答错的单词记录
   ```

### 响应式设计

- 最大宽度: 390px
- 最大高度: 844px
- 适配移动端屏幕
- 卡片自适应布局

## 项目结构

```
dishuwordgame/
├── index.html          # 主游戏文件（包含HTML、CSS、JavaScript）
├── mp3/                # 音频文件目录
│   ├── background.mp3  # 背景音乐
│   ├── gameover.mp3    # 游戏结束音效
│   ├── levelup.mp3     # 答对音效
│   └── welldown.mp3    # 胜利音效
└── README.md           # 项目文档
```

## 词汇库示例

游戏内置小学1-6年级词汇库，每个年级约30个常用单词。示例：

### 一年级词汇
- apple (苹果)
- book (书)
- cat (猫)
- dog (狗)
- egg (鸡蛋)
...

### 六年级词汇
- adventure (冒险)
- climate (气候)
- democracy (民主)
- equation (方程)
...

## 部署信息

### Netlify部署
- 生产环境URL: https://dishuwordgame.netlify.app
- 构建日志: https://app.netlify.com/projects/dishuwordgame/deploys
- 自动部署: 推送到GitHub后自动触发部署

### GitHub Pages（可选）
```bash
# 克隆仓库
git clone https://github.com/henrywangzy/dishuwordgame.git

# 直接打开index.html即可运行
```

## 开发说明

### 本地运行
1. 克隆项目到本地
2. 使用浏览器打开`index.html`文件
3. 或使用本地服务器（推荐）：
   ```bash
   # 使用Python
   python -m http.server 8000

   # 使用Node.js
   npx serve .
   ```

### 修改词汇库
在`index.html`中找到`wordsByGrade`对象，按照以下格式添加或修改单词：

```javascript
const wordsByGrade = {
  1: [
    { word: "apple", chinese: "苹果", example: "I eat an apple." },
    // 添加更多单词...
  ],
  // 其他年级...
};
```

### 修改难度参数
在`index.html`中找到`difficultySettings`对象：

```javascript
const difficultySettings = {
    easy: { cardCount: 2, displayTime: 2000 },    // 卡片数量，停留时间(毫秒)
    medium: { cardCount: 3, displayTime: 2000 },
    hard: { cardCount: 4, displayTime: 2000 }
};
```

### 修改游戏时长
找到`gameTimer`变量：

```javascript
let gameTimer = 60; // 游戏时长（秒）
```

## 设计特色

### 视觉设计
- 采用明亮的渐变色背景
- 卡片使用3D翻转动画
- 答对/答错有不同的视觉反馈
- 使用emoji表情增加趣味性

### 用户体验
- 无弹窗暂停，流畅体验
- 音效和语音反馈及时
- 游戏结束后提供详细学习报告
- 操作简单，适合儿童使用

### 教育价值
- 寓教于乐，在游戏中学习单词
- 快速反应训练，提高单词识别速度
- 游戏结束后可复习答错的单词
- 支持语音朗读，加深记忆

## 更新日志

### v1.0.0 (2025-12-23)
- ✅ 实现5×3网格卡片布局
- ✅ 三种难度等级（2/3/4张卡片，2秒停留）
- ✅ 60秒倒计时机制
- ✅ 2秒自动翻回功能
- ✅ 答对卡片必翻回机制
- ✅ 无弹窗暂停功能
- ✅ 暂停时停止背景音乐
- ✅ 游戏结束显示答对/答错单词列表
- ✅ 重来按钮功能
- ✅ 部署到Netlify
- ✅ 发布到GitHub

## 许可证

MIT License

## 作者

henrywangzy

---

🤖 使用 Claude Code 开发
Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>