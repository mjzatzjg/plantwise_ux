# PlantWise 交互设计规范

## 🎬 动画与过渡效果

### 页面切换动画

#### Tab切换动画
```css
/* 标准Tab切换 */
.tab-transition {
  transition: all 300ms cubic-bezier(0.4, 0, 0.2, 1);
  transform: translateX(0);
}

/* 左滑进入 */
.tab-enter-left {
  transform: translateX(100%);
  opacity: 0;
}

/* 右滑进入 */  
.tab-enter-right {
  transform: translateX(-100%);
  opacity: 0;
}

/* 进入完成 */
.tab-enter-active {
  transform: translateX(0);
  opacity: 1;
}
```

#### 页面推入动画 (Page Push)
```css
.page-push-enter {
  transform: translateX(100%);
  transition: transform 350ms cubic-bezier(0.4, 0, 0.2, 1);
}

.page-push-enter-active {
  transform: translateX(0);
}

.page-push-exit {
  transform: translateX(-30%);
  opacity: 0.7;
}
```

### 按钮交互动画

#### 主按钮按压效果
```css
.primary-button {
  transition: all 200ms cubic-bezier(0.4, 0, 0.2, 1);
  transform: scale(1);
  box-shadow: 0 2px 8px rgba(76, 175, 80, 0.3);
}

.primary-button:active {
  transform: scale(0.95);
  box-shadow: 0 4px 12px rgba(76, 175, 80, 0.4);
}

.primary-button:hover {
  box-shadow: 0 6px 16px rgba(76, 175, 80, 0.4);
}
```

#### 拍照按钮特殊效果
```css
.camera-button {
  position: relative;
  transition: all 200ms ease;
}

.camera-button:active {
  transform: scale(0.9);
}

/* 拍照成功波纹效果 */
.camera-button::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.6);
  transform: translate(-50%, -50%);
  animation: camera-ripple 600ms ease-out;
}

@keyframes camera-ripple {
  to {
    width: 120%;
    height: 120%;
    opacity: 0;
  }
}
```

### 卡片交互动画

#### 植物卡片悬停效果
```css
.plant-card {
  transition: all 250ms cubic-bezier(0.4, 0, 0.2, 1);
  transform: translateY(0);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.plant-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
}

.plant-card:active {
  transform: translateY(-2px);
  transition-duration: 100ms;
}
```

#### 卡片加载动画
```css
.plant-card-loading {
  animation: card-load 300ms cubic-bezier(0.4, 0, 0.2, 1);
}

@keyframes card-load {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
```

## 🔄 加载状态动画

### 叶片旋转加载器
```css
.leaf-loader {
  width: 48px;
  height: 48px;
  background: linear-gradient(45deg, #4CAF50, #66BB6A);
  border-radius: 50% 10%;
  animation: leaf-spin 1s linear infinite;
  position: relative;
}

.leaf-loader::before {
  content: '';
  position: absolute;
  width: 4px;
  height: 20px;
  background: #2E7D32;
  top: -10px;
  left: 50%;
  transform: translateX(-50%);
  border-radius: 2px;
}

@keyframes leaf-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
```

### 骨架屏动画
```css
.skeleton {
  background: linear-gradient(90deg, 
    #f0f0f0 25%, 
    #e0e0e0 50%, 
    #f0f0f0 75%);
  background-size: 200% 100%;
  animation: skeleton-loading 1.5s infinite;
}

@keyframes skeleton-loading {
  0% {
    background-position: 200% 0;
  }
  100% {
    background-position: -200% 0;
  }
}
```

### AI分析进度动画
```css
.ai-analyzing {
  display: flex;
  align-items: center;
  gap: 8px;
}

.ai-dots span {
  width: 8px;
  height: 8px;
  background: #4CAF50;
  border-radius: 50%;
  display: inline-block;
  animation: ai-pulse 1.4s infinite ease-in-out;
}

.ai-dots span:nth-child(1) { animation-delay: -0.32s; }
.ai-dots span:nth-child(2) { animation-delay: -0.16s; }
.ai-dots span:nth-child(3) { animation-delay: 0s; }

@keyframes ai-pulse {
  0%, 80%, 100% {
    transform: scale(0.6);
    opacity: 0.5;
  }
  40% {
    transform: scale(1);
    opacity: 1;
  }
}
```

## 🎯 微交互设计

### 收藏按钮动画
```css
.favorite-button {
  transition: all 200ms ease;
}

.favorite-button.liked {
  animation: heart-beat 600ms ease;
  color: #F44336;
}

@keyframes heart-beat {
  0% { transform: scale(1); }
  14% { transform: scale(1.3); }
  28% { transform: scale(1); }
  42% { transform: scale(1.2); }
  56% { transform: scale(1); }
  100% { transform: scale(1); }
}
```

### 成功状态动画
```css
.success-check {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: #4CAF50;
  position: relative;
  animation: success-scale 400ms cubic-bezier(0.4, 0, 0.2, 1);
}

.success-check::after {
  content: '✓';
  color: white;
  font-size: 24px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  animation: check-appear 200ms ease 200ms both;
}

@keyframes success-scale {
  0% { transform: scale(0); }
  50% { transform: scale(1.2); }
  100% { transform: scale(1); }
}

@keyframes check-appear {
  from { opacity: 0; transform: translate(-50%, -50%) scale(0); }
  to { opacity: 1; transform: translate(-50%, -50%) scale(1); }
}
```

### 搜索输入框聚焦动画
```css
.search-input {
  transition: all 300ms cubic-bezier(0.4, 0, 0.2, 1);
  border: 2px solid transparent;
}

.search-input:focus {
  border-color: #4CAF50;
  box-shadow: 0 0 0 4px rgba(76, 175, 80, 0.1);
  transform: scale(1.02);
}

.search-input::placeholder {
  transition: all 200ms ease;
}

.search-input:focus::placeholder {
  transform: translateY(-20px);
  opacity: 0;
}
```

## 📱 手势交互

### 滑动手势定义

#### 卡片轮播滑动
```javascript
// 水平滑动阈值
const SWIPE_THRESHOLD = 50; // 像素
const SWIPE_VELOCITY_THRESHOLD = 0.3; // 像素/ms

// 滑动检测
function handleSwipe(startX, endX, velocity) {
  const distance = endX - startX;
  
  if (Math.abs(distance) > SWIPE_THRESHOLD || velocity > SWIPE_VELOCITY_THRESHOLD) {
    if (distance > 0) {
      // 向右滑动 - 上一张
      showPreviousCard();
    } else {
      // 向左滑动 - 下一张  
      showNextCard();
    }
  }
}
```

#### 下拉刷新
```javascript
const PULL_REFRESH_THRESHOLD = 80;

function handlePullRefresh(distance) {
  if (distance > PULL_REFRESH_THRESHOLD) {
    // 触发刷新
    refreshContent();
    showRefreshAnimation();
  }
}

// 刷新动画
function showRefreshAnimation() {
  const loader = document.querySelector('.pull-refresh-loader');
  loader.style.transform = 'rotate(360deg)';
  loader.style.transition = 'transform 500ms ease';
}
```

### 长按交互
```css
.long-press-item {
  transition: all 200ms ease;
}

.long-press-item.pressing {
  transform: scale(0.95);
  opacity: 0.8;
}
```

```javascript
let pressTimer;

function handleLongPress(element, callback) {
  element.addEventListener('touchstart', () => {
    pressTimer = setTimeout(() => {
      callback();
      element.classList.add('pressing');
    }, 500); // 500ms长按触发
  });
  
  element.addEventListener('touchend', () => {
    clearTimeout(pressTimer);
    element.classList.remove('pressing');
  });
}
```

## 🔊 反馈系统

### 触觉反馈 (iOS)
```javascript
// 轻微反馈 - 按钮点击
if (window.DeviceMotionEvent) {
  navigator.vibrate(10);
}

// 中等反馈 - 成功操作
if (window.DeviceMotionEvent) {
  navigator.vibrate([20, 10, 20]);
}

// 强烈反馈 - 错误或警告
if (window.DeviceMotionEvent) {
  navigator.vibrate([50, 30, 50]);
}
```

### 音效反馈
```javascript
const audioFeedback = {
  click: new Audio('/sounds/click.mp3'),
  success: new Audio('/sounds/success.mp3'),
  error: new Audio('/sounds/error.mp3'),
  camera: new Audio('/sounds/camera-shutter.mp3')
};

// 播放音效
function playSound(type) {
  if (audioFeedback[type]) {
    audioFeedback[type].currentTime = 0;
    audioFeedback[type].play().catch(() => {
      // 静默处理播放失败
    });
  }
}
```

## 🌐 响应式交互

### 触摸优化
```css
/* 增大触摸目标 */
.touch-target {
  min-width: 44px;
  min-height: 44px;
  position: relative;
}

/* 触摸反馈 */
.touch-target::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.1);
  transform: translate(-50%, -50%);
  transition: all 200ms ease;
}

.touch-target:active::before {
  width: 100%;
  height: 100%;
}
```

### 键盘适应
```css
/* 虚拟键盘出现时的适应 */
@supports (height: 100dvh) {
  .full-height {
    height: 100dvh;
  }
}

/* 输入框聚焦时滚动到可见区域 */
.input-focused {
  scroll-margin-top: 20px;
  scroll-behavior: smooth;
}
```

### 暗黑模式过渡
```css
* {
  transition: background-color 300ms ease, color 300ms ease;
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg-primary: #121212;
    --text-primary: #FFFFFF;
    --card-bg: #1E1E1E;
  }
}
```

## 📊 性能优化交互

### 图片懒加载动画
```css
.lazy-image {
  opacity: 0;
  transition: opacity 300ms ease;
}

.lazy-image.loaded {
  opacity: 1;
}

.lazy-image.loading {
  background: linear-gradient(90deg, #f0f0f0 25%, #e0e0e0 50%, #f0f0f0 75%);
  background-size: 200% 100%;
  animation: skeleton-loading 1.5s infinite;
}
```

### 无限滚动指示器
```css
.infinite-loading {
  display: flex;
  justify-content: center;
  padding: 20px;
  opacity: 0;
  animation: fade-in-up 300ms ease forwards;
}

@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
```
