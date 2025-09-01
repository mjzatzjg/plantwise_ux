# PlantWise 设计系统规范

## 🎨 色彩体系

### 主要色彩
- **主绿色 (Primary Green)**: #4CAF50
  - 用途：主要按钮、图标、强调元素
  - 可访问性：与白色文本的对比度 4.5:1 (WCAG AA)
  
- **浅绿色 (Light Green)**: #E8F5E9
  - 用途：背景、卡片背景、次要区域
  - 可访问性：与深色文本的对比度 12:1

- **强调橙色 (Accent Orange)**: #FF9800
  - 用途：搜索按钮、警告状态、CTA按钮
  - 可访问性：与白色文本的对比度 4.1:1

### 中性色彩
- **纯白色 (Pure White)**: #FFFFFF
- **深灰色 (Dark Gray)**: #333333
- **中灰色 (Medium Gray)**: #666666
- **浅灰色 (Light Gray)**: #F5F5F5

### 状态色彩
- **成功绿色**: #4CAF50 (健康状态)
- **警告橙色**: #FF9800 (注意状态)
- **错误红色**: #F44336 (问题状态)

## 📝 字体系统

### 字体层次
```
标题 H1: 28pt, 重量:Bold, 颜色:#333333
标题 H2: 24pt, 重量:SemiBold, 颜色:#333333
标题 H3: 20pt, 重量:Medium, 颜色:#333333
正文 Body: 16pt, 重量:Regular, 颜色:#333333
说明文字 Caption: 14pt, 重量:Regular, 颜色:#666666
按钮文字 Button: 16pt, 重量:SemiBold, 颜色:根据背景调整
```

### 字体选择
- **iOS**: SF Pro Display / SF Pro Text
- **Android**: Roboto
- **Web**: Inter, -apple-system, BlinkMacSystemFont

## 🔘 按钮系统

### 主要按钮 (Primary Button)
```
背景: #4CAF50
文字: #FFFFFF 16pt SemiBold
圆角: 8px (方形现代风格)
最小高度: 44px
水平内边距: 24px
点击效果: 0.95倍缩放 + 阴影增强
```

### 次要按钮 (Secondary Button)
```
背景: 透明
边框: 2px solid #4CAF50
文字: #4CAF50 16pt SemiBold
圆角: 8px
最小高度: 44px
```

### 强调按钮 (Accent Button)
```
背景: #FF9800
文字: #FFFFFF 16pt SemiBold
圆角: 50% (圆形，用于拍照等重要功能)
最小尺寸: 56px x 56px
```

## 📐 间距系统

### 基础间距单位: 8px

```
XXS: 4px   - 细微间距
XS:  8px   - 最小间距
S:   16px  - 小间距
M:   24px  - 中等间距
L:   32px  - 大间距
XL:  48px  - 特大间距
XXL: 64px  - 页面级间距
```

## 🃏 卡片系统

### 标准卡片
```
背景: #FFFFFF
圆角: 12px
阴影: 0 2px 8px rgba(0,0,0,0.1)
内边距: 16px
边距: 16px (卡片间)
```

### 植物卡片
```
背景: #FFFFFF
圆角: 16px
阴影: 0 4px 12px rgba(0,0,0,0.15)
图片圆角: 12px (顶部)
状态指示器: 右上角圆形徽章
```

## 🖼️ 图标系统

### 图标风格
- **风格**: 线性图标 (Outline style)
- **粗细**: 2px stroke
- **尺寸**: 24x24px (标准), 32x32px (Tab bar)
- **颜色**: 继承父元素或 #666666

### 核心图标
```
首页: House outline
相机: Camera outline (居中突出)
花园: Plant/Garden fence outline
搜索: Magnifying glass
设置: Gear outline
收藏: Heart outline
分享: Share arrow
```

## 🎭 动画规范

### 过渡动画
```
标准缓动: cubic-bezier(0.4, 0, 0.2, 1)
快速缓动: cubic-bezier(0.4, 0, 1, 1)
慢速缓动: cubic-bezier(0, 0, 0.2, 1)
```

### 时间规范
```
快速过渡: 200ms - 按钮状态变化
标准过渡: 300ms - 页面切换
慢速过渡: 500ms - 复杂动画
```

### 微交互动画
```
按钮按下: transform: scale(0.95) + shadow增强
卡片悬停: transform: translateY(-2px) + shadow增强
加载动画: 绿色叶片旋转 (360° 1s infinite)
成功反馈: 绿色勾号从小放大 (scale 0->1.2->1)
```

## 📱 响应式规范

### 断点系统
```
Mobile (Portrait): 375px - 414px
Mobile (Landscape): 667px - 896px
Tablet: 768px - 1024px
Desktop: 1200px+
```

### 安全区域
```
iOS安全区域: env(safe-area-inset-*)
状态栏高度: 44px (考虑刘海屏)
Tab Bar高度: 84px (包含安全区域)
最小点击区域: 44x44px
```

## ♿ 可访问性规范

### 颜色对比度
- 正常文本: 4.5:1 (WCAG AA)
- 大文本: 3:1 (WCAG AA)
- 非文本元素: 3:1

### 触控目标
- 最小尺寸: 44x44px
- 推荐尺寸: 48x48px
- 间距: 8px minimum

### 语义化支持
```
角色标签: button, link, heading, etc.
状态标签: expanded, selected, disabled
描述性文本: aria-label, aria-describedby
动态内容: aria-live regions
```

## 🔄 状态系统

### 加载状态
```
初始加载: 骨架屏 (Skeleton Screen)
按钮加载: 按钮内小型 spinner
页面加载: 全屏绿色叶片动画
图片加载: 渐显效果 (fade-in)
```

### 错误状态
```
网络错误: "无法连接 - 请检查网络"
识别失败: "识别失败 - 尝试更清晰的照片"
空状态: 友好插图 + 引导文案
```

### 成功状态
```
识别成功: 绿色勾号 + "识别成功!"
添加植物: "已添加到我的花园"
诊断完成: "诊断报告已生成"
```
