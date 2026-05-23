<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>TechVault — Premium Digital Products Store 🚀</title>
<style>
/* ═══════════════════════════════════════════
   🎨 全局样式：暗黑+玻璃态+蓝紫渐变
   ═══════════════════════════════════════════ */
:root {
  --bg: #0A0A12;
  --card-bg: rgba(255,255,255,0.06);
  --card-border: rgba(255,255,255,0.12);
  --accent: #4469B3;
  --accent2: #7B2FBE;
  --accent3: #E040FB;
  --green: #00E676;
  --red: #FF5252;
  --yellow: #FFD740;
  --text: #e0e0e0;
  --text-dim: #8888aa;
}
* { margin:0; padding:0; box-sizing:border-box; }
body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  background: var(--bg);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
  padding-bottom: 80px;
}

/* ═══════════════════════════════════════════
   🪟 玻璃态卡片
   ═══════════════════════════════════════════ */
.glass {
  background: var(--card-bg);
  backdrop-filter: blur(40px);
  -webkit-backdrop-filter: blur(40px);
  border: 1px solid var(--card-border);
  border-radius: 20px;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}
.glass:hover {
  transform: translateY(-6px);
  box-shadow: 0 16px 64px rgba(123,47,190,0.3);
  border-color: rgba(123,47,190,0.4);
}

/* ═══════════════════════════════════════════
   🔝 顶部导航栏
   ═══════════════════════════════════════════ */
nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 32px;
  position: sticky;
  top: 0;
  z-index: 100;
  background: rgba(10,10,18,0.7);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--card-border);
}
.logo {
  font-size: 24px; font-weight: 800;
  background: linear-gradient(135deg, var(--accent), var(--accent3));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  letter-spacing: -0.5px;
}
.nav-links { display: flex; gap: 24px; }
.nav-links a {
  color: var(--text-dim); text-decoration: none;
  font-size: 14px; font-weight: 500;
  transition: all 0.3s;
  position: relative;
}
.nav-links a:hover { color: var(--accent3); }
.nav-links a.active {
  color: var(--accent3);
  padding-bottom: 4px;
}
.nav-links a.active::after {
  content: '';
  position: absolute;
  bottom: -16px;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--accent), var(--accent3));
  border-radius: 2px;
}

/* ═══════════════════════════════════════════
   🔍 搜索栏（玻璃态+粒子聚焦）
   ═══════════════════════════════════════════ */
.search-bar {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px 20px;
  margin: 24px 32px;
  background: var(--card-bg);
  backdrop-filter: blur(40px);
  border: 1px solid var(--card-border);
  border-radius: 16px;
  transition: all 0.3s;
}
.search-bar:focus-within {
  border-color: var(--accent3);
  box-shadow: 0 0 30px rgba(224,64,251,0.2);
}
.search-bar input {
  flex: 1;
  background: none;
  border: none;
  outline: none;
  color: var(--text);
  font-size: 15px;
}
.search-bar input::placeholder { color: var(--text-dim); }

/* ═══════════════════════════════════════════
   📂 分类筛选栏（横向滑动+液态过渡）
   ═══════════════════════════════════════════ */
.filter-bar {
  display: flex;
  gap: 12px;
  padding: 0 32px;
  margin-bottom: 24px;
  overflow-x: auto;
  scrollbar-width: none;
}
.filter-bar::-webkit-scrollbar { display: none; }
.filter-chip {
  padding: 10px 20px;
  border-radius: 24px;
  background: var(--card-bg);
  backdrop-filter: blur(20px);
  border: 1px solid var(--card-border);
  color: var(--text-dim);
  font-size: 13px;
  font-weight: 600;
  white-space: nowrap;
  cursor: pointer;
  transition: all 0.3s;
}
.filter-chip:hover {
  color: var(--text);
  border-color: var(--accent2);
}
.filter-chip.active {
  background: linear-gradient(135deg, var(--accent), var(--accent3));
  color: white;
  border-color: transparent;
  box-shadow: 0 4px 20px rgba(123,47,190,0.4);
}

/* ═══════════════════════════════════════════
   🏷️ 产品展示区（卡片网格）
   ═══════════════════════════════════════════ */
.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 24px;
  padding: 0 32px;
}
.product-card {
  padding: 20px;
  position: relative;
  overflow: hidden;
}
.product-thumb {
  width: 100%;
  height: 180px;
  border-radius: 12px;
  background: linear-gradient(135deg, rgba(68,105,179,0.2), rgba(224,64,251,0.15));
  margin-bottom: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 48px;
  transition: all 0.4s;
  position: relative;
  overflow: hidden;
}
.product-card:hover .product-thumb {
  transform: scale(1.05);
}
.product-thumb::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(123,47,190,0.3), rgba(224,64,251,0.2));
  opacity: 0;
  transition: opacity 0.4s;
}
.product-card:hover .product-thumb::after { opacity: 1; }
.product-badge {
  position: absolute;
  top: 12px;
  right: 12px;
  background: var(--red);
  color: white;
  padding: 4px 12px;
  border-radius: 12px;
  font-size: 11px;
  font-weight: 700;
  animation: pulse 2s infinite;
}
@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.7; }
}
.product-name {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 8px;
}
.product-desc {
  font-size: 13px;
  color: var(--text-dim);
  margin-bottom: 12px;
  line-height: 1.5;
}
.product-price {
  font-size: 24px;
  font-weight: 800;
  background: linear-gradient(135deg, var(--accent), var(--accent3));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 12px;
}
.product-rating {
  display: flex;
  align-items: center;
  gap: 6px;
  font-size: 13px;
  color: var(--yellow);
  margin-bottom: 12px;
}
.buy-btn {
  width: 100%;
  padding: 12px;
  border: none;
  border-radius: 12px;
  background: linear-gradient(135deg, var(--accent), var(--accent3));
  color: white;
  font-size: 15px;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.3s;
}
.buy-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(123,47,190,0.5);
}

/* ═══════════════════════════════════════════
   🏪 真实店铺首页
   ═══════════════════════════════════════════ */
.store-header {
  text-align: center;
  padding: 48px 32px 32px;
}
.store-name {
  font-size: 42px;
  font-weight: 900;
  background: linear-gradient(135deg, var(--accent), var(--accent3));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 12px;
}
.store-rating {
  font-size: 20px;
  color: var(--yellow);
  margin-bottom: 24px;
}
.store-stats {
  display: flex;
  justify-content: center;
  gap: 48px;
  margin-top: 24px;
}
.stat-item {
  text-align: center;
}
.stat-num {
  font-size: 32px;
  font-weight: 800;
  color: var(--accent3);
}
.stat-label {
  font-size: 13px;
  color: var(--text-dim);
  margin-top: 4px;
}

/* ═══════════════════════════════════════════
   📊 店铺数据仪表盘（暗黑图表风格）
   ═══════════════════════════════════════════ */
.dashboard {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  padding: 0 32px;
  margin: 32px 0;
}
.kpi-card {
  padding: 24px;
  text-align: center;
}
.kpi-value {
  font-size: 36px;
  font-weight: 800;
  background: linear-gradient(135deg, var(--accent), var(--accent3));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 8px;
}
.kpi-label {
  font-size: 13px;
  color: var(--text-dim);
}
.kpi-change {
  font-size: 14px;
  font-weight: 700;
  color: var(--green);
  margin-top: 8px;
}

/* ═══════════════════════════════════════════
   💰 财务收账模块
   ═══════════════════════════════════════════ */
.finance-section {
  padding: 0 32px;
  margin-top: 48px;
}
.finance-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
  margin-bottom: 32px;
}
.finance-card {
  padding: 24px;
}
.finance-value {
  font-size: 28px;
  font-weight: 800;
  color: var(--accent3);
  margin-bottom: 8px;
}
.finance-label {
  font-size: 13px;
  color: var(--text-dim);
}

/* 订单列表 */
.orders-list {
  padding: 0 32px;
  margin-top: 32px;
}
.order-item {
  padding: 20px;
  margin-bottom: 16px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.order-info h4 {
  font-size: 16px;
  margin-bottom: 8px;
}
.order-meta {
  font-size: 13px;
  color: var(--text-dim);
}
.order-status {
  padding: 6px 16px;
  border-radius: 12px;
  font-size: 12px;
  font-weight: 700;
}
.status-completed {
  background: rgba(0,230,118,0.2);
  color: var(--green);
}
.status-processing {
  background: rgba(68,105,179,0.2);
  color: var(--accent2);
}

/* ═══════════════════════════════════════════
   📱 底部导航栏
   ═══════════════════════════════════════════ */
.bottom-nav {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: space-around;
  padding: 12px 0;
  background: rgba(10,10,18,0.9);
  backdrop-filter: blur(20px);
  border-top: 1px solid var(--card-border);
  z-index: 100;
}
.nav-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
  color: var(--text-dim);
  text-decoration: none;
  font-size: 11px;
  font-weight: 600;
  transition: all 0.3s;
  cursor: pointer;
}
.nav-item.active {
  color: var(--accent3);
}
.nav-item span { font-size: 24px; }

/* ═══════════════════════════════════════════
   ✨ 页面切换动画
   ═══════════════════════════════════════════ */
.page {
  display: none;
  animation: fadeIn 0.4s ease;
}
.page.active { display: block; }
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* 响应式 */
@media (max-width: 768px) {
  .hero { grid-template-columns: 1fr; }
  .dashboard, .finance-grid { grid-template-columns: 1fr; }
  .products-grid { grid-template-columns: 1fr; }
  nav { padding: 12px 16px; }
  .search-bar, .filter-bar, .products-grid, .dashboard, .finance-section, .orders-list {
    padding-left: 16px;
    padding-right: 16px;
  }
}
</style>
</head>
<body>

<!-- 🔝 顶部导航 -->
<nav>
  <div class="logo">🚀 TechVault</div>
  <div class="nav-links">
    <a href="#" class="active" onclick="showPage('home')">Home</a>
    <a href="#" onclick="showPage('products')">Products</a>
    <a href="#" onclick="showPage('store')">Store</a>
    <a href="#" onclick="showPage('finance')">Finance</a>
  </div>
</nav>

<!-- 🏠 首页 -->
<div id="home" class="page active">
  <!-- 搜索栏 -->
  <div class="search-bar">
    <span class="icon">🔍</span>
    <input type="text" placeholder="Search templates, or ask AI... (e.g. 'Show me best SaaS templates')" />
  </div>

  <!-- 分类筛选 -->
  <div class="filter-bar">
    <div class="filter-chip active">All</div>
    <div class="filter-chip">🏢 Websites</div>
    <div class="filter-chip">🛒 E-Commerce</div>
    <div class="filter-chip">☁️ SaaS</div>
    <div class="filter-chip">🎨 Portfolio</div>
    <div class="filter-chip">📊 Dashboard</div>
    <div class="filter-chip">🤖 AI Tools</div>
  </div>

  <!-- 产品展示区 -->
  <div class="products-grid">
    <!-- 产品1 -->
    <div class="product-card glass">
      <div class="product-thumb">🖥️</div>
      <div class="product-badge">🔥 HOT</div>
      <div class="product-name">Corporate Website Pro</div>
      <div class="product-desc">Responsive + SEO + CMS + Multi-language</div>
      <div class="product-price">$149</div>
      <div class="product-rating">⭐ 4.9 (342 reviews)</div>
      <button class="buy-btn">Add to Cart</button>
    </div>

    <!-- 产品2 -->
    <div class="product-card glass">
      <div class="product-thumb">🛒</div>
      <div class="product-name">E-Commerce Starter</div>
      <div class="product-desc">Full-featured store + Payment + Inventory</div>
      <div class="product-price">$249</div>
      <div class="product-rating">⭐ 4.8 (567 reviews)</div>
      <button class="buy-btn">Add to Cart</button>
    </div>

    <!-- 产品3 -->
    <div class="product-card glass">
      <div class="product-thumb">☁️</div>
      <div class="product-badge">🆕 NEW</div>
      <div class="product-name">SaaS Dashboard Kit</div>
      <div class="product-desc">Landing page + User system + API docs</div>
      <div class="product-price">$199</div>
      <div class="product-rating">⭐ 4.9 (189 reviews)</div>
      <button class="buy-btn">Add to Cart</button>
    </div>

    <!-- 产品4 -->
    <div class="product-card glass">
      <div class="product-thumb">🎨</div>
      <div class="product-name">Designer Portfolio</div>
      <div class="product-desc">Minimal + Blog + Contact form + CMS</div>
      <div class="product-price">$79</div>
      <div class="product-rating">⭐ 5.0 (89 reviews)</div>
      <button class="buy-btn">Add to Cart</button>
    </div>

    <!-- 产品5 -->
    <div class="product-card glass">
      <div class="product-thumb">📊</div>
      <div class="product-name">Data Viz Dashboard</div>
      <div class="product-desc">Charts + Real-time data + Dark mode</div>
      <div class="product-price">$349</div>
      <div class="product-rating">⭐ 4.7 (156 reviews)</div>
      <button class="buy-btn">Add to Cart</button>
    </div>

    <!-- 产品6 -->
    <div class="product-card glass">
      <div class="product-thumb">🤖</div>
      <div class="product-badge">🔥 HOT</div>
      <div class="product-name">AI Product Landing</div>
      <div class="product-desc">ChatUI + Prompt showcase + API demo</div>
      <div class="product-price">$299</div>
      <div class="product-rating">⭐ 4.9 (234 reviews)</div>
      <button class="buy-btn">Add to Cart</button>
    </div>
  </div>

  <!-- 热力图筛选区 -->
  <div style="padding: 48px 32px;">
    <h3 style="margin-bottom:16px;font-size:18px;color:var(--text-dim);">🔥 Category Heatmap</h3>
    <div style="display:grid;grid-template-columns:repeat(5,1fr);gap:12px;" id="heatmap"></div>
  </div>
</div>

<!-- 🏷️ 产品分类页 -->
<div id="products" class="page">
  <div style="padding:32px;">
    <h2 style="font-size:32px;margin-bottom:24px;background:linear-gradient(135deg,var(--accent),var(--accent3));-webkit-background-clip:text;-webkit-text-fill-color:transparent;">Product Categories</h2>
    <div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:20px;">
      <div class="glass" style="padding:24px;text-align:center;cursor:pointer;">
        <div style="font-size:48px;margin-bottom:12px;">🏢</div>
        <h3 style="font-size:18px;margin-bottom:8px;">Websites</h3>
        <p style="font-size:13px;color:var(--text-dim);margin-bottom:12px;">12 products · $49-$199</p>
        <div style="background:var(--accent);height:4px;border-radius:2px;width:60%;margin:0 auto;"></div>
      </div>
      <div class="glass" style="padding:24px;text-align:center;cursor:pointer;">
        <div style="font-size:48px;margin-bottom:12px;">🛒</div>
        <h3 style="font-size:18px;margin-bottom:8px;">E-Commerce</h3>
        <p style="font-size:13px;color:var(--text-dim);margin-bottom:12px;">18 products · $79-$299</p>
        <div style="background:var(--accent2);height:4px;border-radius:2px;width:80%;margin:0 auto;"></div>
      </div>
      <div class="glass" style="padding:24px;text-align:center;cursor:pointer;">
        <div style="font-size:48px;margin-bottom:12px;">☁️</div>
        <h3 style="font-size:18px;margin-bottom:8px;">SaaS</h3>
        <p style="font-size:13px;color:var(--text-dim);margin-bottom:12px;">9 products · $99-$399</p>
        <div style="background:var(--accent3);height:4px;border-radius:2px;width:70%;margin:0 auto;"></div>
      </div>
      <div class="glass" style="padding:24px;text-align:center;cursor:pointer;">
        <div style="font-size:48px;margin-bottom:12px;">🎨</div>
        <h3 style="font-size:18px;margin-bottom:8px;">Portfolio</h3>
        <p style="font-size:13px;color:var(--text-dim);margin-bottom:12px;">24 products · $29-$99</p>
        <div style="background:var(--green);height:4px;border-radius:2px;width:50%;margin:0 auto;"></div>
      </div>
      <div class="glass" style="padding:24px;text-align:center;cursor:pointer;">
        <div style="font-size:48px;margin-bottom:12px;">📊</div>
        <h3 style="font-size:18px;margin-bottom:8px;">Dashboard</h3>
        <p style="font-size:13px;color:var(--text-dim);margin-bottom:12px;">7 products · $149-$499</p>
        <div style="background:var(--yellow);height:4px;border-radius:2px;width:90%;margin:0 auto;"></div>
      </div>
      <div class="glass" style="padding:24px;text-align:center;cursor:pointer;">
        <div style="font-size:48px;margin-bottom:12px;">🤖</div>
        <h3 style="font-size:18px;margin-bottom:8px;">AI Tools</h3>
        <p style="font-size:13px;color:var(--text-dim);margin-bottom:12px;">11 products · $89-$349</p>
        <div style="background:var(--red);height:4px;border-radius:2px;width:75%;margin:0 auto;"></div>
      </div>
    </div>
  </div>
</div>

<!-- 🏪 真实店铺页 -->
<div id="store" class="page">
  <div class="store-header">
    <h1 class="store-name">TechVault Digital Store</h1>
    <div class="store-rating">⭐ 4.9 / 5.0 (2,341 reviews)</div>
    <div class="store-stats">
      <div class="stat-item">
        <div class="stat-num">12,847</div>
        <div class="stat-label">Orders Shipped</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">8,234</div>
        <div class="stat-label">Happy Customers</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">96.8%</div>
        <div class="stat-label">Satisfaction Rate</div>
      </div>
    </div>
  </div>

  <!-- 店铺数据仪表盘 -->
  <div class="dashboard">
    <div class="kpi-card glass">
      <div class="kpi-value">$48,230</div>
      <div class="kpi-label">Monthly Revenue</div>
      <div class="kpi-change">↑ 23.5%</div>
    </div>
    <div class="kpi-card glass">
      <div class="kpi-value">2,341</div>
      <div class="kpi-label">Total Reviews</div>
      <div class="kpi-change">↑ 12.8%</div>
    </div>
    <div class="kpi-card glass">
      <div class="kpi-value">2.3h</div>
      <div class="kpi-label">Avg. Delivery</div>
      <div class="kpi-change">↓ 0.5h</div>
    </div>
  </div>

  <!-- 热销排行 -->
  <div style="padding:0 32px;margin-bottom:48px;">
    <h3 style="margin-bottom:16px;font-size:18px;">🔥 Top Sellers</h3>
    <div style="display:flex;flex-direction:column;gap:12px;">
      <div class="glass order-item">
        <div>
          <div style="font-size:16px;font-weight:700;margin-bottom:4px;">🏆 Corporate Website Pro</div>
          <div style="font-size:13px;color:var(--text-dim);">567 sold · ⭐ 4.9</div>
        </div>
        <div style="font-size:20px;font-weight:800;color:var(--accent3);">$149</div>
      </div>
      <div class="glass order-item">
        <div>
          <div style="font-size:16px;font-weight:700;margin-bottom:4px;">🥈 E-Commerce Starter</div>
          <div style="font-size:13px;color:var(--text-dim);">342 sold · ⭐ 4.8</div>
        </div>
        <div style="font-size:20px;font-weight:800;color:var(--accent3);">$249</div>
      </div>
      <div class="glass order-item">
        <div>
          <div style="font-size:16px;font-weight:700;margin-bottom:4px;">🥉 SaaS Dashboard Kit</div>
          <div style="font-size:13px;color:var(--text-dim);">189 sold · ⭐ 4.9</div>
        </div>
        <div style="font-size:20px;font-weight:800;color:var(--accent3);">$199</div>
      </div>
    </div>
  </div>

  <!-- 信任徽章 -->
  <div style="padding:0 32px;text-align:center;margin-bottom:48px;">
    <div style="display:flex;justify-content:center;gap:16px;flex-wrap:wrap;">
      <div class="glass" style="padding:12px 20px;font-size:13px;">🔒 SSL Secured</div>
      <div class="glass" style="padding:12px 20px;font-size:13px;">📦 7-Day Refund</div>
      <div class="glass" style="padding:12px 20px;font-size:13px;">🚚 Instant Delivery</div>
      <div class="glass" style="padding:12px 20px;font-size:13px;">🤖 24/7 AI Support</div>
    </div>
  </div>
</div>

<!-- 💰 财务收账页 -->
<div id="finance" class="page">
  <div class="finance-section">
    <h2 style="font-size:32px;margin-bottom:32px;background:linear-gradient(135deg,var(--accent),var(--accent3));-webkit-background-clip:text;-webkit-text-fill-color:transparent;">💰 Financial Center</h2>

    <div class="finance-grid">
      <div class="finance-card glass">
        <div style="font-size:13px;color:var(--text-dim);margin-bottom:8px;">Total Revenue</div>
        <div class="finance-value">$128,430</div>
        <div style="font-size:14px;color:var(--green);font-weight:700;">↑ 23.5%</div>
      </div>
      <div class="finance-card glass">
        <div style="font-size:13px;color:var(--text-dim);margin-bottom:8px;">This Month</div>
        <div class="finance-value">$18,230</div>
        <div style="font-size:14px;color:var(--green);font-weight:700;">↑ 12.8%</div>
      </div>
      <div class="finance-card glass">
        <div style="font-size:13px;color:var(--text-dim);margin-bottom:8px;">Available to Withdraw</div>
        <div class="finance-value">$12,450</div>
        <div style="font-size:14px;color:var(--yellow);font-weight:700;">2 pending</div>
      </div>
    </div>

    <!-- 订单列表 -->
    <h3 style="margin-bottom:16px;font-size:18px;color:var(--text-dim);">📋 Recent Orders</h3>
    <div class="orders-list">
      <div class="order-item glass">
        <div class="order-info">
          <h4>#ORD-20250612 · Corporate Website Pro x1</h4>
          <div class="order-meta">💵 $149.00 · ✅ Completed · 2025-06-12</div>
        </div>
        <div class="order-status status-completed">✅ Completed</div>
      </div>
      <div class="order-item glass">
        <div class="order-info">
          <h4>#ORD-20250611 · SaaS Dashboard Kit x2</h4>
          <div class="order-meta">💵 $598.00 · 🔄 Processing · 2025-06-11</div>
        </div>
        <div class="order-status status-processing">🔄 Processing</div>
      </div>
      <div class="order-item glass">
        <div class="order-info">
          <h4>#ORD-20250610 · AI Product Landing x1</h4>
          <div class="order-meta">💵 $299.00 · ✅ Completed · 2025-06-10</div>
        </div>
        <div class="order-status status-completed">✅ Completed</div>
      </div>
    </div>

    <!-- 税务计算 -->
    <div style="margin-top:48px;">
      <h3 style="margin-bottom:16px;font-size:18px;color:var(--text-dim);">🧮 Tax Calculator</h3>
      <div class="glass" style="padding:24px;">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;">
          <span style="font-size:14px;color:var(--text-dim);">Taxable Income (This Month)</span>
          <span style="font-size:24px;font-weight:800;color:var(--accent3);">$18,230.00</span>
        </div>
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;">
          <span style="font-size:14px;color:var(--text-dim);">Est. Tax Rate (Federal + State)</span>
          <span style="font-size:18px;font-weight:700;color:var(--yellow);">25.3%</span>
        </div>
        <div style="display:flex;justify-content:space-between;align-items:center;padding-top:16px;border-top:1px solid var(--card-border);">
          <span style="font-size:14px;color:var(--text-dim);">Est. Tax Due</span>
          <span style="font-size:28px;font-weight:800;color:var(--green);">$4,612.19</span>
        </div>
        <button class="buy-btn" style="margin-top:20px;">Export Tax Report</button>
      </div>
    </div>

    <!-- 提现功能 -->
    <div style="margin-top:48px;">
      <h3 style="margin-bottom:16px;font-size:18px;color:var(--text-dim);">💸 Withdraw Funds</h3>
      <div class="glass" style="padding:24px;">
        <div style="margin-bottom:16px;">
          <div style="font-size:13px;color:var(--text-dim);margin-bottom:8px;">Bank Account</div>
          <div style="font-size:18px;font-weight:700;">Chase Bank ****4521</div>
        </div>
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:20px;">
          <span style="font-size:14px;color:var(--text-dim);">Available</span>
          <span style="font-size:28px;font-weight:800;color:var(--accent3);">$12,450.00</span>
        </div>
        <button class="buy-btn">Withdraw to Bank</button>
        <div style="margin-top:12px;font-size:12px;color:var(--text-dim);text-align:center;">Min: $50 · 1-3 business days</div>
      </div>
    </div>
  </div>
</div>

<!-- 📱 底部导航栏 -->
<div class="bottom-nav">
  <div class="nav-item active" onclick="showPage('home')">
    <span>🏠</span>
    Home
  </div>
  <div class="nav-item" onclick="showPage('products')">
    <span>🏷️</span>
    Products
  </div>
  <div class="nav-item" onclick="showPage('store')">
    <span>🏪</span>
    Store
  </div>
  <div class="nav-item" onclick="showPage('finance')">
    <span>💰</span>
    Finance
  </div>
</div>

<script>
// 页面切换
function showPage(pageId) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById(pageId).classList.add('active');
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  event.currentTarget.classList.add('active');
  window.scrollTo({ top: 0, behavior: 'smooth' });
}

// 分类筛选交互
document.querySelectorAll('.filter-chip').forEach(chip => {
  chip.addEventListener('click', function() {
    document.querySelectorAll('.filter-chip').forEach(c => c.classList.remove('active'));
    this.classList.add('active');
  });
});

// 生成热力图
const sectors = ['Tech', 'Health', 'Finance', 'Energy', 'Consumer', 'Industrial'];
const heatEl = document.getElementById('heatmap');
sectors.forEach(s => {
  const pct = (Math.random() * 10 - 5).toFixed(1);
  const intensity = Math.min(1, Math.max(0, (parseFloat(pct) + 5) / 10));
  const r = Math.round(255 * intensity);
  const g = Math.round(80 * (1 - intensity));
  const b = Math.round(80 * (1 - intensity));
  const cell = document.createElement('div');
  cell.className = 'glass';
  cell.style.cssText = `
    padding: 16px;
    text-align: center;
    background: rgba(${r},${g},${b},0.35);
    color: ${parseFloat(pct) >= 0 ? '#00E676' : '#FF5252'};
    font-weight: 700;
    font-size: 14px;
  `;
  cell.textContent = s + ' ' + pct + '%';
  heatEl.appendChild(cell);
});

// 购物车交互
document.querySelectorAll('.buy-btn').forEach(btn => {
  btn.addEventListener('click', function() {
    this.textContent = '✅ Added!';
    this.style.background = 'linear-gradient(135deg, #00E676, #00C853)';
    setTimeout(() => {
      this.textContent = 'Add to Cart';
      this.style.background = 'linear-gradient(135deg, var(--accent), var(--accent3))';
    }, 2000);
  });
});
</script>

</body>
</html>
