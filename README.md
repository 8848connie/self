# 个人主页资料页面

<div align="center">

<!-- 样式定义 -->
<style>
  /* 主容器 */
  .profile-container {
    max-width: 800px;
    margin: 0 auto;
    padding: 40px 20px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #667eea 100%);
    background-size: 200% 200%;
    animation: gradientShift 15s ease infinite;
    border-radius: 30px;
    box-shadow: 0 20px 60px rgba(102, 126, 234, 0.3);
  }

  @keyframes gradientShift {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
  }

  /* 内容区域 */
  .profile-content {
    background: rgba(255, 255, 255, 0.95);
    backdrop-filter: blur(10px);
    border-radius: 25px;
    padding: 50px 40px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  }

  /* 姓名样式 */
  .profile-name {
    font-size: 3.5em;
    font-weight: 700;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin: 0;
    padding: 20px 0;
    text-shadow: 0 4px 20px rgba(102, 126, 234, 0.3);
    letter-spacing: 2px;
    animation: nameGlow 3s ease-in-out infinite;
  }

  @keyframes nameGlow {
    0%, 100% { filter: drop-shadow(0 0 10px rgba(102, 126, 234, 0.5)); }
    50% { filter: drop-shadow(0 0 25px rgba(118, 75, 162, 0.8)); }
  }

  /* 分割线样式 */
  .divider {
    width: 80%;
    height: 3px;
    background: linear-gradient(90deg, 
      transparent 0%, 
      rgba(102, 126, 234, 0.3) 15%,
      rgba(118, 75, 162, 0.8) 50%,
      rgba(102, 126, 234, 0.3) 85%,
      transparent 100%);
    margin: 30px auto;
    position: relative;
    border: none;
  }

  .divider::before {
    content: '✨';
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    font-size: 1.5em;
    background: white;
    padding: 0 15px;
    animation: sparkle 2s ease-in-out infinite;
  }

  @keyframes sparkle {
    0%, 100% { opacity: 1; transform: translate(-50%, -50%) scale(1); }
    50% { opacity: 0.6; transform: translate(-50%, -50%) scale(1.2); }
  }

  /* 自我介绍 */
  .profile-bio {
    font-size: 1.3em;
    color: #4a5568;
    line-height: 1.8;
    margin: 25px 0;
    font-style: italic;
    position: relative;
    padding: 0 30px;
  }

  .profile-bio::before,
  .profile-bio::after {
    content: '"';
    font-size: 3em;
    color: rgba(102, 126, 234, 0.3);
    position: absolute;
    font-family: Georgia, serif;
  }

  .profile-bio::before {
    left: 0;
    top: -20px;
  }

  .profile-bio::after {
    right: 0;
    bottom: -40px;
  }

  /* 拍立得相框 */
  .polaroid-frame {
    background: white;
    padding: 15px 15px 60px 15px;
    box-shadow: 
      0 4px 6px rgba(0, 0, 0, 0.1),
      0 10px 20px rgba(0, 0, 0, 0.15),
      0 0 0 1px rgba(0, 0, 0, 0.05);
    border-radius: 3px;
    display: inline-block;
    margin: 40px 0;
    transform: rotate(-2deg);
    transition: all 0.3s ease;
    position: relative;
  }

  .polaroid-frame:hover {
    transform: rotate(0deg) scale(1.05);
    box-shadow: 
      0 10px 20px rgba(0, 0, 0, 0.15),
      0 20px 40px rgba(102, 126, 234, 0.3);
  }

  .polaroid-frame::before {
    content: '';
    position: absolute;
    top: -10px;
    left: 50%;
    transform: translateX(-50%);
    width: 50px;
    height: 20px;
    background: rgba(102, 126, 234, 0.1);
    border-radius: 3px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }

  .polaroid-image {
    width: 300px;
    height: 300px;
    object-fit: cover;
    display: block;
    border-radius: 2px;
  }

  .polaroid-caption {
    font-family: 'Caveat', cursive;
    font-size: 1.5em;
    color: #4a5568;
    margin-top: 15px;
    text-align: center;
  }

  /* 装饰品容器 */
  .decorations {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 30px;
    margin: 40px 0;
    flex-wrap: wrap;
  }

  .decoration-item {
    font-size: 3em;
    animation: float 3s ease-in-out infinite;
    filter: drop-shadow(0 5px 15px rgba(102, 126, 234, 0.3));
  }

  .decoration-item:nth-child(1) { animation-delay: 0s; }
  .decoration-item:nth-child(2) { animation-delay: 0.5s; }
  .decoration-item:nth-child(3) { animation-delay: 1s; }
  .decoration-item:nth-child(4) { animation-delay: 1.5s; }
  .decoration-item:nth-child(5) { animation-delay: 2s; }

  @keyframes float {
    0%, 100% { transform: translateY(0px); }
    50% { transform: translateY(-20px); }
  }

  /* 技能标签 */
  .skills-section {
    margin-top: 50px;
  }

  .skills-title {
    font-size: 2em;
    font-weight: 600;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 30px;
  }

  .skills-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 15px;
    margin-top: 20px;
  }

  .skill-badge {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    padding: 12px 24px;
    border-radius: 25px;
    font-size: 1em;
    font-weight: 500;
    display: inline-flex;
    align-items: center;
    gap: 8px;
    box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
    transition: all 0.3s ease;
    cursor: pointer;
  }

  .skill-badge:hover {
    transform: translateY(-5px) scale(1.05);
    box-shadow: 0 8px 25px rgba(102, 126, 234, 0.6);
  }

  .skill-icon {
    font-size: 1.3em;
  }

  /* 底部装饰波浪 */
  .wave-decoration {
    margin-top: 50px;
    position: relative;
    height: 60px;
  }

  .wave {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1200 120' preserveAspectRatio='none'%3E%3Cpath d='M321.39,56.44c58-10.79,114.16-30.13,172-41.86,82.39-16.72,168.19-17.73,250.45-.39C823.78,31,906.67,72,985.66,92.83c70.05,18.48,146.53,26.09,214.34,3V0H0V27.35A600.21,600.21,0,0,0,321.39,56.44Z' fill='rgba(102, 126, 234, 0.1)'/%3E%3C/svg%3E") repeat-x;
    animation: wave 10s linear infinite;
  }

  @keyframes wave {
    0% { background-position: 0 0; }
    100% { background-position: 1200px 0; }
  }

  /* 响应式设计 */
  @media (max-width: 768px) {
    .profile-name { font-size: 2.5em; }
    .profile-bio { font-size: 1.1em; padding: 0 20px; }
    .polaroid-image { width: 250px; height: 250px; }
    .skill-badge { font-size: 0.9em; padding: 10px 20px; }
  }
</style>

<!-- 主容器 -->
<div class="profile-container">
  <div class="profile-content">
    
    <!-- 姓名 -->
    <h1 class="profile-name">张三</h1>
    
    <!-- 分割线 -->
    <hr class="divider">
    
    <!-- 自我介绍 -->
    <p class="profile-bio">
      追求卓越，永不止步。热爱技术，享受创造的乐趣。
    </p>
    
    <!-- 分割线 -->
    <hr class="divider">
    
    <!-- 拍立得相框 -->
    <div class="polaroid-frame">
      <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=400&h=400&fit=crop" 
           alt="个人照片" 
           class="polaroid-image">
      <p class="polaroid-caption">Keep Moving Forward ✨</p>
    </div>
    
    <!-- 装饰品 -->
    <div class="decorations">
      <span class="decoration-item">🌟</span>
      <span class="decoration-item">💎</span>
      <span class="decoration-item">🚀</span>
      <span class="decoration-item">⚡</span>
      <span class="decoration-item">🎯</span>
    </div>
    
    <!-- 技能部分 -->
    <div class="skills-section">
      <h2 class="skills-title">语言 & 工具</h2>
      
      <div class="skills-container">
        <span class="skill-badge">
          <span class="skill-icon">🐍</span> Python
        </span>
        <span class="skill-badge">
          <span class="skill-icon">☕</span> Java
        </span>
        <span class="skill-badge">
          <span class="skill-icon">📜</span> JavaScript
        </span>
        <span class="skill-badge">
          <span class="skill-icon">⚛️</span> React
        </span>
        <span class="skill-badge">
          <span class="skill-icon">🎨</span> CSS
        </span>
        <span class="skill-badge">
          <span class="skill-icon">🗄️</span> SQL
        </span>
        <span class="skill-badge">
          <span class="skill-icon">🐳</span> Docker
        </span>
        <span class="skill-badge">
          <span class="skill-icon">📊</span> Git
        </span>
        <span class="skill-badge">
          <span class="skill-icon">☁️</span> AWS
        </span>
        <span class="skill-badge">
          <span class="skill-icon">🔧</span> VS Code
        </span>
      </div>
    </div>
    
    <!-- 底部波浪装饰 -->
    <div class="wave-decoration">
      <div class="wave"></div>
    </div>
    
  </div>
</div>

</div>

---

## 使用说明

### 📝 自定义内容

1. **修改姓名**：将 `张三` 替换为你的名字
2. **修改介绍**：将自我介绍文字替换为你的个人简介
3. **替换照片**：将 `src="..."` 中的链接替换为你的照片链接
4. **修改标题**：将 `Keep Moving Forward ✨` 替换为你喜欢的文字
5. **调整技能**：添加或删除技能标签，修改图标和文字

### 🎨 颜色自定义

主要颜色变量：
- 主渐变色：`#667eea` (淡紫蓝) 到 `#764ba2` (紫色)
- 可以替换为其他蓝色系：
  - 天空蓝：`#3b82f6` 到 `#2563eb`
  - 深蓝：`#1e3a8a` to `#1e40af`
  - 青蓝：`#0891b2` to `#06b6d4`

### ✨ 装饰图标

可以替换的装饰 Emoji：
- `🌟 💫 ⭐ ✨ 🌙 🌈 🦋 🌸 🎭 🎨 🎪 🎯 🚀 💎 ⚡ 🔮 🏆 👑 🎖️ 🎁`

### 🛠️ 技能图标

常用技能图标：
- 编程语言：`🐍 ☕ 📜 💎 🦀 ⚡`
- 框架：`⚛️ 📱 🎯 🔥`
- 工具：`🐳 📊 🔧 ☁️ 🗄️`

### 📸 照片建议

推荐尺寸：正方形 400x400px 或更高
照片来源：
- 自己的照片
- Unsplash: `https://images.unsplash.com/photo-xxxxx?w=400&h=400&fit=crop`
- 头像生成器: UI Avatars, Boring Avatars

---

## 效果预览特点

✅ **蓝紫渐变背景** - 梦幻唯美  
✅ **动态光晕效果** - 神圣氛围  
✅ **拍立得相框** - 怀旧质感  
✅ **浮动装饰品** - 生动活泼  
✅ **炫彩技能标签** - 专业现代  
✅ **波浪装饰** - 柔和过渡  
✅ **响应式设计** - 移动端友好  
✅ **悬停动画** - 交互丰富  

---

<div align="center">
  <sub>Built with ❤️ using HTML & CSS</sub>
</div>
