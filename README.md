<!DOCTYPE html>
<html lang="uz">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#0a0a0a">
<meta name="description" content="YULDUZCHA - Premium Uzbek Fast Food Delivery">
<title>YULDUZCHA | Premium Food Delivery</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
<style>
:root {
  --bg-primary: #0a0a0a;
  --bg-secondary: #111111;
  --bg-tertiary: #1a1a1a;
  --bg-card: rgba(255,255,255,0.04);
  --bg-glass: rgba(255,255,255,0.06);
  --bg-glass-hover: rgba(255,255,255,0.1);
  --border-glass: rgba(255,255,255,0.1);
  --border-subtle: rgba(255,255,255,0.06);
  --text-primary: #ffffff;
  --text-secondary: #a1a1aa;
  --text-muted: #71717a;
  --gold: #f5c542;
  --gold-dim: #d4a017;
  --gold-glow: rgba(245,197,66,0.25);
  --accent: #f5c542;
  --success: #22c55e;
  --danger: #ef4444;
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-xl: 24px;
  --shadow-sm: 0 2px 8px rgba(0,0,0,0.3);
  --shadow-md: 0 8px 24px rgba(0,0,0,0.4);
  --shadow-lg: 0 16px 48px rgba(0,0,0,0.5);
  --transition: 0.25s cubic-bezier(0.4,0,0.2,1);
  --nav-height: 72px;
  --bottom-nav-height: 64px;
  --max-width: 1400px;
  --font: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
}

[data-theme="light"] {
  --bg-primary: #f8f7f4;
  --bg-secondary: #ffffff;
  --bg-tertiary: #f0efe9;
  --bg-card: rgba(255,255,255,0.85);
  --bg-glass: rgba(255,255,255,0.7);
  --bg-glass-hover: rgba(255,255,255,0.9);
  --border-glass: rgba(0,0,0,0.08);
  --border-subtle: rgba(0,0,0,0.05);
  --text-primary: #111111;
  --text-secondary: #52525b;
  --text-muted: #a1a1aa;
  --gold: #c9a227;
  --gold-dim: #a8841a;
  --gold-glow: rgba(201,162,39,0.2);
  --shadow-sm: 0 2px 8px rgba(0,0,0,0.06);
  --shadow-md: 0 8px 24px rgba(0,0,0,0.08);
  --shadow-lg: 0 16px 48px rgba(0,0,0,0.12);
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; -webkit-tap-highlight-color: transparent; }
body {
  font-family: var(--font);
  background: var(--bg-primary);
  color: var(--text-primary);
  line-height: 1.5;
  overflow-x: hidden;
  min-height: 100vh;
  transition: background 0.4s ease, color 0.4s ease;
}
img { max-width: 100%; display: block; }
button, input, select, textarea { font-family: inherit; border: none; outline: none; background: none; color: inherit; }
button { cursor: pointer; }
a { text-decoration: none; color: inherit; }
ul, ol { list-style: none; }
::-webkit-scrollbar { width: 6px; height: 6px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: var(--text-muted); border-radius: 3px; }

/* ========== LOADING SCREEN ========== */
#loader {
  position: fixed; inset: 0; z-index: 99999;
  background: #0a0a0a;
  display: flex; flex-direction: column; align-items: center; justify-content: center;
  transition: opacity 0.6s ease, visibility 0.6s ease;
}
#loader.hide { opacity: 0; visibility: hidden; pointer-events: none; }
.loader-logo {
  font-size: 2rem; font-weight: 800; letter-spacing: 0.05em;
  display: flex; align-items: center; gap: 12px; margin-bottom: 32px;
}
.loader-star {
  width: 40px; height: 40px;
  animation: starSpin 2s ease-in-out infinite;
}
.loader-bar {
  width: 120px; height: 3px; background: rgba(255,255,255,0.1); border-radius: 2px; overflow: hidden;
}
.loader-bar-fill {
  height: 100%; width: 0%; background: var(--gold);
  animation: loadBar 1.8s ease-in-out forwards;
}
@keyframes starSpin { 0%,100%{transform:rotate(0) scale(1)} 50%{transform:rotate(180deg) scale(1.15)} }
@keyframes loadBar { 0%{width:0} 100%{width:100%} }

/* ========== NAVIGATION ========== */
.navbar {
  position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
  height: var(--nav-height);
  background: rgba(10,10,10,0.75);
  backdrop-filter: blur(24px) saturate(180%);
  -webkit-backdrop-filter: blur(24px) saturate(180%);
  border-bottom: 1px solid var(--border-subtle);
  transition: height 0.3s ease, background 0.3s ease;
}
[data-theme="light"] .navbar { background: rgba(248,247,244,0.85); }
.navbar.scrolled { height: 60px; }
.nav-progress {
  position: absolute; bottom: 0; left: 0; height: 2px;
  background: linear-gradient(90deg, var(--gold), var(--gold-dim));
  width: 0%; transition: width 0.1s linear; z-index: 2;
}
.nav-inner {
  max-width: var(--max-width); margin: 0 auto; height: 100%;
  display: flex; align-items: center; justify-content: space-between;
  padding: 0 24px; gap: 24px;
}
.nav-logo {
  display: flex; align-items: center; gap: 10px;
  font-weight: 800; font-size: 1.25rem; letter-spacing: 0.04em;
  white-space: nowrap; flex-shrink: 0;
}
.nav-logo svg { width: 28px; height: 28px; flex-shrink: 0; }
.nav-links {
  display: flex; align-items: center; gap: 8px;
}
.nav-links a {
  padding: 8px 16px; font-size: 0.875rem; font-weight: 500;
  color: var(--text-secondary); border-radius: var(--radius-sm);
  transition: all var(--transition); position: relative;
}
.nav-links a:hover, .nav-links a.active { color: var(--text-primary); background: var(--bg-glass); }
.nav-actions {
  display: flex; align-items: center; gap: 8px; flex-shrink: 0;
}
.nav-btn {
  width: 42px; height: 42px; border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  color: var(--text-secondary); transition: all var(--transition);
  position: relative;
}
.nav-btn:hover { background: var(--bg-glass-hover); color: var(--text-primary); border-color: var(--gold); }
.nav-btn .badge {
  position: absolute; top: -2px; right: -2px;
  min-width: 18px; height: 18px; padding: 0 5px;
  background: var(--gold); color: #0a0a0a;
  font-size: 0.65rem; font-weight: 700; border-radius: 10px;
  display: flex; align-items: center; justify-content: center;
  transform: scale(0); transition: transform 0.3s cubic-bezier(0.34,1.56,0.64,1);
}
.nav-btn .badge.show { transform: scale(1); }
.nav-btn.pulse .badge { animation: badgePulse 0.4s ease; }
@keyframes badgePulse { 0%,100%{transform:scale(1)} 50%{transform:scale(1.3)} }

.hamburger {
  display: none; width: 42px; height: 42px; border-radius: 50%;
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  flex-direction: column; align-items: center; justify-content: center; gap: 5px;
}
.hamburger span {
  display: block; width: 18px; height: 2px; background: var(--text-primary);
  border-radius: 1px; transition: all 0.3s ease;
}
.hamburger.open span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
.hamburger.open span:nth-child(2) { opacity: 0; }
.hamburger.open span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }

.mobile-menu {
  position: fixed; top: var(--nav-height); left: 0; right: 0; bottom: 0;
  background: rgba(10,10,10,0.95); backdrop-filter: blur(24px);
  z-index: 999; display: flex; flex-direction: column;
  padding: 24px; transform: translateX(100%);
  transition: transform 0.35s cubic-bezier(0.4,0,0.2,1);
  overflow-y: auto;
}
[data-theme="light"] .mobile-menu { background: rgba(248,247,244,0.97); }
.mobile-menu.open { transform: translateX(0); }
.mobile-menu a {
  padding: 16px 0; font-size: 1.125rem; font-weight: 600;
  border-bottom: 1px solid var(--border-subtle); color: var(--text-primary);
}
.mobile-menu-actions { margin-top: 24px; display: flex; gap: 12px; }

/* ========== HERO ========== */
.hero {
  position: relative; min-height: 100vh; display: flex; align-items: center;
  padding: calc(var(--nav-height) + 40px) 24px 80px;
  overflow: hidden;
}
.hero-bg {
  position: absolute; inset: 0; z-index: 0;
  background: url('https://images.unsplash.com/photo-1565299624946-b28f40a0ae38?w=1600&q=80') center/cover no-repeat;
}
.hero-overlay {
  position: absolute; inset: 0; z-index: 1;
  background: linear-gradient(135deg, rgba(10,10,10,0.92) 0%, rgba(10,10,10,0.7) 40%, rgba(10,10,10,0.85) 100%);
}
[data-theme="light"] .hero-overlay {
  background: linear-gradient(135deg, rgba(248,247,244,0.92) 0%, rgba(248,247,244,0.75) 40%, rgba(248,247,244,0.88) 100%);
}
.hero-particles {
  position: absolute; inset: 0; z-index: 2; pointer-events: none; overflow: hidden;
}
.particle {
  position: absolute; width: 4px; height: 4px; background: var(--gold);
  border-radius: 50%; opacity: 0.3; animation: floatParticle 8s ease-in-out infinite;
}
@keyframes floatParticle {
  0%,100%{transform:translateY(0) scale(1);opacity:0.2}
  50%{transform:translateY(-30px) scale(1.3);opacity:0.5}
}
.hero-content {
  position: relative; z-index: 3; max-width: var(--max-width); margin: 0 auto; width: 100%;
  display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center;
}
.hero-text h1 {
  font-size: clamp(2.25rem, 5vw, 3.75rem); font-weight: 800; line-height: 1.15;
  margin-bottom: 20px; letter-spacing: -0.02em;
}
.hero-text h1 span { color: var(--gold); }
.hero-text p {
  font-size: 1.125rem; color: var(--text-secondary); max-width: 480px;
  margin-bottom: 36px; line-height: 1.7;
}
.hero-btns { display: flex; gap: 16px; flex-wrap: wrap; }
.btn {
  display: inline-flex; align-items: center; justify-content: center; gap: 8px;
  padding: 14px 28px; font-size: 0.9375rem; font-weight: 600;
  border-radius: var(--radius-md); transition: all var(--transition);
  position: relative; overflow: hidden; white-space: nowrap;
}
.btn-primary {
  background: var(--gold); color: #0a0a0a;
  box-shadow: 0 4px 20px var(--gold-glow);
}
.btn-primary:hover { background: var(--gold-dim); transform: translateY(-2px); box-shadow: 0 8px 28px var(--gold-glow); }
.btn-secondary {
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  color: var(--text-primary); backdrop-filter: blur(12px);
}
.btn-secondary:hover { background: var(--bg-glass-hover); border-color: var(--gold); }
.btn-sm { padding: 10px 18px; font-size: 0.875rem; }
.btn-block { width: 100%; }
.btn .ripple {
  position: absolute; border-radius: 50%; background: rgba(255,255,255,0.3);
  transform: scale(0); animation: rippleAnim 0.6s linear; pointer-events: none;
}
@keyframes rippleAnim { to { transform: scale(4); opacity: 0; } }

.hero-visual {
  position: relative; display: flex; justify-content: center; align-items: center;
}
.hero-food {
  width: 100%; max-width: 480px; aspect-ratio: 1;
  border-radius: 50%; object-fit: cover;
  box-shadow: 0 0 80px var(--gold-glow), 0 20px 60px rgba(0,0,0,0.5);
  animation: heroFloat 6s ease-in-out infinite;
  border: 3px solid rgba(245,197,66,0.2);
}
@keyframes heroFloat {
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-16px)}
}
.hero-glow {
  position: absolute; width: 60%; height: 60%; border-radius: 50%;
  background: radial-gradient(circle, var(--gold-glow), transparent 70%);
  filter: blur(40px); z-index: -1;
}

/* ========== SECTIONS ========== */
.section {
  max-width: var(--max-width); margin: 0 auto; padding: 80px 24px;
}
.section-header {
  text-align: center; margin-bottom: 48px;
}
.section-header h2 {
  font-size: clamp(1.75rem, 3.5vw, 2.5rem); font-weight: 800;
  margin-bottom: 12px; letter-spacing: -0.02em;
}
.section-header p { color: var(--text-secondary); font-size: 1.0625rem; max-width: 520px; margin: 0 auto; }
.section-label {
  display: inline-block; font-size: 0.75rem; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.12em; color: var(--gold);
  margin-bottom: 12px;
}

/* ========== SEARCH & CATEGORIES ========== */
.menu-controls {
  display: flex; flex-direction: column; gap: 20px; margin-bottom: 40px;
}
.search-box {
  position: relative; max-width: 520px; width: 100%; margin: 0 auto;
}
.search-box input {
  width: 100%; padding: 16px 20px 16px 52px;
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  border-radius: var(--radius-lg); font-size: 0.9375rem;
  color: var(--text-primary); backdrop-filter: blur(12px);
  transition: all var(--transition);
}
.search-box input:focus { border-color: var(--gold); box-shadow: 0 0 0 3px var(--gold-glow); }
.search-box input::placeholder { color: var(--text-muted); }
.search-box svg {
  position: absolute; left: 18px; top: 50%; transform: translateY(-50%);
  width: 20px; height: 20px; color: var(--text-muted); pointer-events: none;
}
.search-shortcut {
  position: absolute; right: 16px; top: 50%; transform: translateY(-50%);
  font-size: 0.7rem; color: var(--text-muted); background: var(--bg-tertiary);
  padding: 3px 8px; border-radius: 4px; border: 1px solid var(--border-subtle);
  pointer-events: none;
}
.search-count {
  text-align: center; font-size: 0.875rem; color: var(--text-muted); margin-top: 8px;
}

.categories {
  display: flex; gap: 10px; overflow-x: auto; padding: 4px 0 12px;
  scrollbar-width: none; -ms-overflow-style: none;
  justify-content: center; flex-wrap: wrap;
}
.categories::-webkit-scrollbar { display: none; }
.cat-pill {
  padding: 10px 20px; font-size: 0.875rem; font-weight: 600;
  border-radius: 50px; white-space: nowrap; flex-shrink: 0;
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  color: var(--text-secondary); transition: all var(--transition);
  cursor: pointer;
}
.cat-pill:hover { background: var(--bg-glass-hover); color: var(--text-primary); }
.cat-pill.active {
  background: var(--gold); color: #0a0a0a; border-color: var(--gold);
  box-shadow: 0 4px 16px var(--gold-glow);
}

/* ========== PRODUCT GRID ========== */
.products-grid {
  display: grid; grid-template-columns: repeat(4, 1fr); gap: 24px;
}
.product-card {
  background: var(--bg-card); border: 1px solid var(--border-glass);
  border-radius: var(--radius-lg); overflow: hidden;
  transition: all 0.35s cubic-bezier(0.4,0,0.2,1);
  cursor: pointer; position: relative;
  backdrop-filter: blur(12px);
}
.product-card:hover {
  transform: translateY(-6px);
  box-shadow: var(--shadow-lg);
  border-color: rgba(245,197,66,0.25);
}
.product-card .img-wrap {
  position: relative; aspect-ratio: 4/3; overflow: hidden;
  background: var(--bg-tertiary);
}
.product-card .img-wrap img {
  width: 100%; height: 100%; object-fit: cover;
  transition: transform 0.5s ease;
}
.product-card:hover .img-wrap img { transform: scale(1.08); }
.product-card .badge-tag {
  position: absolute; top: 12px; left: 12px;
  padding: 4px 10px; font-size: 0.7rem; font-weight: 700;
  border-radius: 6px; background: var(--gold); color: #0a0a0a;
  z-index: 2;
}
.product-card .fav-btn {
  position: absolute; top: 12px; right: 12px; z-index: 2;
  width: 36px; height: 36px; border-radius: 50%;
  background: rgba(0,0,0,0.5); backdrop-filter: blur(8px);
  display: flex; align-items: center; justify-content: center;
  color: #fff; transition: all var(--transition); border: none;
}
.product-card .fav-btn:hover, .product-card .fav-btn.active { color: #ef4444; }
.product-card .fav-btn.active svg { fill: #ef4444; }
.product-card .card-body { padding: 16px; }
.product-card .card-cat {
  font-size: 0.7rem; font-weight: 600; text-transform: uppercase;
  letter-spacing: 0.06em; color: var(--gold); margin-bottom: 6px;
}
.product-card .card-name {
  font-size: 1rem; font-weight: 700; margin-bottom: 6px;
  display: -webkit-box; -webkit-line-clamp: 1; -webkit-box-orient: vertical; overflow: hidden;
}
.product-card .card-desc {
  font-size: 0.8125rem; color: var(--text-muted); margin-bottom: 12px;
  display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical; overflow: hidden;
  line-height: 1.45;
}
.product-card .card-rating {
  display: flex; align-items: center; gap: 6px; margin-bottom: 12px;
  font-size: 0.8125rem;
}
.product-card .card-rating .stars { color: var(--gold); }
.product-card .card-rating .count { color: var(--text-muted); }
.product-card .card-footer {
  display: flex; align-items: center; justify-content: space-between; gap: 8px;
}
.product-card .price-block { display: flex; flex-direction: column; }
.product-card .price { font-size: 1.0625rem; font-weight: 700; color: var(--text-primary); }
.product-card .old-price { font-size: 0.75rem; color: var(--text-muted); text-decoration: line-through; }
.product-card .discount { font-size: 0.7rem; font-weight: 700; color: var(--success); }
.product-card .add-btn {
  padding: 8px 14px; font-size: 0.8125rem; font-weight: 600;
  background: var(--gold); color: #0a0a0a; border-radius: var(--radius-sm);
  transition: all var(--transition); white-space: nowrap;
}
.product-card .add-btn:hover { background: var(--gold-dim); }
.product-card .qty-controls {
  display: none; align-items: center; gap: 0;
  background: var(--bg-tertiary); border-radius: var(--radius-sm); overflow: hidden;
}
.product-card .qty-controls.show { display: flex; }
.product-card .qty-controls button {
  width: 32px; height: 32px; display: flex; align-items: center; justify-content: center;
  font-size: 1rem; font-weight: 600; color: var(--text-primary);
  transition: background var(--transition);
}
.product-card .qty-controls button:hover { background: var(--bg-glass-hover); }
.product-card .qty-controls span {
  min-width: 28px; text-align: center; font-size: 0.875rem; font-weight: 600;
}

.img-fallback {
  width: 100%; height: 100%; display: flex; align-items: center; justify-content: center;
  background: linear-gradient(135deg, var(--bg-tertiary), var(--bg-secondary));
  color: var(--text-muted); font-size: 2.5rem;
}

.empty-state {
  text-align: center; padding: 60px 24px; color: var(--text-muted);
}
.empty-state svg { width: 64px; height: 64px; margin: 0 auto 16px; opacity: 0.4; }
.empty-state h3 { font-size: 1.25rem; color: var(--text-secondary); margin-bottom: 8px; }

/* ========== PROMOTIONS ========== */
.promos-grid {
  display: grid; grid-template-columns: repeat(3, 1fr); gap: 24px;
}
.promo-card {
  position: relative; border-radius: var(--radius-xl); overflow: hidden;
  aspect-ratio: 16/10; cursor: pointer;
  border: 1px solid var(--border-glass);
  transition: all 0.35s ease;
}
.promo-card:hover { transform: translateY(-4px); box-shadow: var(--shadow-lg); }
.promo-card img { width: 100%; height: 100%; object-fit: cover; }
.promo-card .promo-overlay {
  position: absolute; inset: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.85) 0%, rgba(0,0,0,0.2) 60%);
  display: flex; flex-direction: column; justify-content: flex-end; padding: 24px;
}
.promo-card .promo-badge {
  position: absolute; top: 16px; right: 16px;
  background: var(--gold); color: #0a0a0a; font-size: 0.75rem; font-weight: 800;
  padding: 4px 12px; border-radius: 6px;
}
.promo-card h3 { font-size: 1.25rem; font-weight: 700; margin-bottom: 4px; }
.promo-card p { font-size: 0.875rem; color: rgba(255,255,255,0.7); margin-bottom: 8px; }
.promo-card .promo-price {
  display: flex; align-items: baseline; gap: 10px;
}
.promo-card .promo-price .new { font-size: 1.25rem; font-weight: 800; color: var(--gold); }
.promo-card .promo-price .old { font-size: 0.875rem; text-decoration: line-through; color: rgba(255,255,255,0.5); }

/* ========== ABOUT ========== */
.about-grid {
  display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center;
}
.about-features {
  display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-top: 32px;
}
.about-feature {
  padding: 20px; background: var(--bg-glass); border: 1px solid var(--border-glass);
  border-radius: var(--radius-md); backdrop-filter: blur(12px);
}
.about-feature .icon { font-size: 1.5rem; margin-bottom: 8px; }
.about-feature h4 { font-size: 0.9375rem; font-weight: 700; margin-bottom: 4px; }
.about-feature p { font-size: 0.8125rem; color: var(--text-muted); }
.stats-row {
  display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px; margin-top: 48px;
}
.stat-item {
  text-align: center; padding: 24px 16px;
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  border-radius: var(--radius-lg); backdrop-filter: blur(12px);
}
.stat-item .num { font-size: 1.75rem; font-weight: 800; color: var(--gold); margin-bottom: 4px; }
.stat-item .label { font-size: 0.8125rem; color: var(--text-muted); }

/* ========== REVIEWS ========== */
.rating-overview {
  display: grid; grid-template-columns: 200px 1fr; gap: 40px;
  margin-bottom: 40px; padding: 32px;
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  border-radius: var(--radius-xl); backdrop-filter: blur(12px);
}
.rating-score { text-align: center; }
.rating-score .big { font-size: 3.5rem; font-weight: 800; line-height: 1; }
.rating-score .stars { color: var(--gold); font-size: 1.25rem; margin: 8px 0; }
.rating-score .total { font-size: 0.875rem; color: var(--text-muted); }
.rating-bars { display: flex; flex-direction: column; gap: 8px; justify-content: center; }
.rating-bar-row { display: flex; align-items: center; gap: 12px; font-size: 0.8125rem; }
.rating-bar-row span:first-child { width: 48px; color: var(--text-muted); }
.rating-bar-track {
  flex: 1; height: 8px; background: var(--bg-tertiary); border-radius: 4px; overflow: hidden;
}
.rating-bar-fill {
  height: 100%; background: var(--gold); border-radius: 4px;
  transition: width 1s ease; width: 0;
}
.rating-bar-row span:last-child { width: 36px; text-align: right; color: var(--text-muted); }

.reviews-sort {
  display: flex; gap: 8px; margin-bottom: 24px; flex-wrap: wrap;
}
.reviews-sort button {
  padding: 8px 16px; font-size: 0.8125rem; font-weight: 600;
  border-radius: 50px; background: var(--bg-glass); border: 1px solid var(--border-glass);
  color: var(--text-secondary); transition: all var(--transition);
}
.reviews-sort button.active, .reviews-sort button:hover {
  background: var(--gold); color: #0a0a0a; border-color: var(--gold);
}
.reviews-list { display: flex; flex-direction: column; gap: 16px; }
.review-card {
  padding: 20px; background: var(--bg-glass); border: 1px solid var(--border-glass);
  border-radius: var(--radius-md); backdrop-filter: blur(8px);
}
.review-header {
  display: flex; align-items: center; gap: 12px; margin-bottom: 12px;
}
.review-avatar {
  width: 40px; height: 40px; border-radius: 50%;
  background: var(--gold); color: #0a0a0a;
  display: flex; align-items: center; justify-content: center;
  font-weight: 700; font-size: 0.875rem; flex-shrink: 0;
}
.review-meta { flex: 1; }
.review-meta .name { font-weight: 600; font-size: 0.9375rem; }
.review-meta .date { font-size: 0.75rem; color: var(--text-muted); }
.review-stars { color: var(--gold); font-size: 0.875rem; }
.review-text { font-size: 0.9375rem; color: var(--text-secondary); line-height: 1.6; margin-bottom: 12px; }
.review-helpful {
  font-size: 0.8125rem; color: var(--text-muted);
  display: flex; align-items: center; gap: 6px; cursor: pointer;
  transition: color var(--transition);
}
.review-helpful:hover, .review-helpful.active { color: var(--gold); }

/* ========== CONTACT ========== */
.contact-grid {
  display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px;
}
.contact-card {
  padding: 28px 20px; text-align: center;
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  border-radius: var(--radius-lg); backdrop-filter: blur(12px);
  transition: all var(--transition);
}
.contact-card:hover { border-color: var(--gold); transform: translateY(-2px); }
.contact-card .icon { font-size: 1.75rem; margin-bottom: 12px; }
.contact-card h4 { font-size: 0.875rem; font-weight: 600; color: var(--text-muted); margin-bottom: 6px; }
.contact-card p, .contact-card a { font-size: 1rem; font-weight: 600; }

/* ========== FOOTER ========== */
.footer {
  border-top: 1px solid var(--border-subtle); padding: 48px 24px 100px;
  text-align: center; color: var(--text-muted); font-size: 0.875rem;
}
.footer-logo {
  display: flex; align-items: center; justify-content: center; gap: 10px;
  font-weight: 800; font-size: 1.25rem; color: var(--text-primary); margin-bottom: 16px;
}
.footer-links { display: flex; justify-content: center; gap: 24px; margin-bottom: 20px; flex-wrap: wrap; }
.footer-links a { color: var(--text-secondary); transition: color var(--transition); }
.footer-links a:hover { color: var(--gold); }

/* ========== CART DRAWER ========== */
.cart-overlay {
  position: fixed; inset: 0; z-index: 2000;
  background: rgba(0,0,0,0.5); backdrop-filter: blur(6px);
  opacity: 0; visibility: hidden; transition: all 0.3s ease;
}
.cart-overlay.open { opacity: 1; visibility: visible; }
.cart-drawer {
  position: fixed; top: 0; right: 0; bottom: 0; z-index: 2001;
  width: min(420px, 100vw); background: var(--bg-secondary);
  border-left: 1px solid var(--border-glass);
  display: flex; flex-direction: column;
  transform: translateX(100%); transition: transform 0.35s cubic-bezier(0.4,0,0.2,1);
}
.cart-drawer.open { transform: translateX(0); }
.cart-header {
  display: flex; align-items: center; justify-content: space-between;
  padding: 20px 24px; border-bottom: 1px solid var(--border-subtle);
}
.cart-header h3 { font-size: 1.125rem; font-weight: 700; }
.cart-close {
  width: 36px; height: 36px; border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  font-size: 1.25rem; transition: all var(--transition);
}
.cart-close:hover { background: var(--bg-glass-hover); }
.cart-body { flex: 1; overflow-y: auto; padding: 16px 24px; }
.cart-item {
  display: flex; gap: 14px; padding: 14px 0;
  border-bottom: 1px solid var(--border-subtle);
}
.cart-item img {
  width: 72px; height: 72px; border-radius: var(--radius-sm);
  object-fit: cover; flex-shrink: 0; background: var(--bg-tertiary);
}
.cart-item-info { flex: 1; min-width: 0; }
.cart-item-info h4 {
  font-size: 0.9375rem; font-weight: 600; margin-bottom: 2px;
  white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
}
.cart-item-info .custom { font-size: 0.75rem; color: var(--text-muted); margin-bottom: 8px; }
.cart-item-actions {
  display: flex; align-items: center; justify-content: space-between;
}
.cart-item-actions .qty {
  display: flex; align-items: center; gap: 0;
  background: var(--bg-tertiary); border-radius: var(--radius-sm); overflow: hidden;
}
.cart-item-actions .qty button {
  width: 28px; height: 28px; display: flex; align-items: center; justify-content: center;
  font-size: 0.875rem; font-weight: 600;
}
.cart-item-actions .qty span { min-width: 24px; text-align: center; font-size: 0.8125rem; font-weight: 600; }
.cart-item-price { font-weight: 700; font-size: 0.9375rem; }
.cart-item-remove {
  color: var(--text-muted); font-size: 0.75rem; cursor: pointer;
  transition: color var(--transition); margin-top: 4px;
}
.cart-item-remove:hover { color: var(--danger); }

.cart-footer {
  padding: 20px 24px; border-top: 1px solid var(--border-subtle);
  background: var(--bg-primary);
}
.cart-summary { margin-bottom: 16px; }
.cart-row {
  display: flex; justify-content: space-between; font-size: 0.875rem;
  margin-bottom: 8px; color: var(--text-secondary);
}
.cart-row.total {
  font-size: 1.125rem; font-weight: 800; color: var(--text-primary);
  margin-top: 12px; padding-top: 12px; border-top: 1px solid var(--border-subtle);
}
.free-delivery-bar {
  margin-bottom: 16px; padding: 12px; background: var(--bg-glass);
  border-radius: var(--radius-sm); border: 1px solid var(--border-glass);
}
.free-delivery-bar p { font-size: 0.8125rem; color: var(--text-secondary); margin-bottom: 8px; }
.progress-track {
  height: 6px; background: var(--bg-tertiary); border-radius: 3px; overflow: hidden;
}
.progress-fill {
  height: 100%; background: linear-gradient(90deg, var(--gold), var(--gold-dim));
  border-radius: 3px; transition: width 0.4s ease;
}
.coupon-field {
  display: flex; gap: 8px; margin-bottom: 16px;
}
.coupon-field input {
  flex: 1; padding: 12px 16px; background: var(--bg-glass);
  border: 1px solid var(--border-glass); border-radius: var(--radius-sm);
  font-size: 0.875rem;
}
.coupon-field input:focus { border-color: var(--gold); }
.coupon-field button {
  padding: 12px 18px; background: var(--bg-tertiary); border: 1px solid var(--border-glass);
  border-radius: var(--radius-sm); font-size: 0.875rem; font-weight: 600;
  transition: all var(--transition);
}
.coupon-field button:hover { border-color: var(--gold); color: var(--gold); }
.coupon-msg { font-size: 0.8125rem; margin-bottom: 12px; }
.coupon-msg.success { color: var(--success); }
.coupon-msg.error { color: var(--danger); }

/* ========== PRODUCT MODAL ========== */
.modal-overlay {
  position: fixed; inset: 0; z-index: 3000;
  background: rgba(0,0,0,0.6); backdrop-filter: blur(8px);
  display: flex; align-items: center; justify-content: center;
  padding: 24px; opacity: 0; visibility: hidden;
  transition: all 0.3s ease;
}
.modal-overlay.open { opacity: 1; visibility: visible; }
.modal {
  background: var(--bg-secondary); border: 1px solid var(--border-glass);
  border-radius: var(--radius-xl); width: min(720px, 100%);
  max-height: 90vh; overflow-y: auto; position: relative;
  transform: scale(0.95) translateY(20px); transition: transform 0.3s ease;
}
.modal-overlay.open .modal { transform: scale(1) translateY(0); }
.modal-close {
  position: absolute; top: 16px; right: 16px; z-index: 5;
  width: 36px; height: 36px; border-radius: 50%;
  background: rgba(0,0,0,0.5); backdrop-filter: blur(8px);
  display: flex; align-items: center; justify-content: center;
  font-size: 1.25rem; color: #fff; border: none;
}
.modal-img {
  width: 100%; aspect-ratio: 16/9; object-fit: cover;
  background: var(--bg-tertiary);
}
.modal-body { padding: 28px; }
.modal-body h2 { font-size: 1.5rem; font-weight: 800; margin-bottom: 8px; }
.modal-rating { display: flex; align-items: center; gap: 8px; margin-bottom: 12px; font-size: 0.875rem; }
.modal-rating .stars { color: var(--gold); }
.modal-desc { color: var(--text-secondary); font-size: 0.9375rem; margin-bottom: 20px; line-height: 1.6; }
.modal-section { margin-bottom: 20px; }
.modal-section h4 {
  font-size: 0.8125rem; font-weight: 700; text-transform: uppercase;
  letter-spacing: 0.06em; color: var(--text-muted); margin-bottom: 10px;
}
.option-group { display: flex; flex-wrap: wrap; gap: 8px; }
.option-btn {
  padding: 8px 16px; font-size: 0.8125rem; font-weight: 600;
  border-radius: 50px; background: var(--bg-glass); border: 1px solid var(--border-glass);
  color: var(--text-secondary); transition: all var(--transition); cursor: pointer;
}
.option-btn:hover, .option-btn.active {
  background: var(--gold); color: #0a0a0a; border-color: var(--gold);
}
.extra-item {
  display: flex; align-items: center; justify-content: space-between;
  padding: 10px 0; border-bottom: 1px solid var(--border-subtle);
  font-size: 0.875rem;
}
.extra-item label { display: flex; align-items: center; gap: 10px; cursor: pointer; }
.extra-item input[type="checkbox"] {
  width: 18px; height: 18px; accent-color: var(--gold); cursor: pointer;
}
.modal-price-row {
  display: flex; align-items: center; justify-content: space-between;
  margin-top: 24px; padding-top: 20px; border-top: 1px solid var(--border-subtle);
}
.modal-price { font-size: 1.5rem; font-weight: 800; }
.modal-qty {
  display: flex; align-items: center; gap: 0;
  background: var(--bg-tertiary); border-radius: var(--radius-sm); overflow: hidden;
}
.modal-qty button {
  width: 40px; height: 40px; display: flex; align-items: center; justify-content: center;
  font-size: 1.125rem; font-weight: 600;
}
.modal-qty span { min-width: 36px; text-align: center; font-weight: 700; }
.special-input {
  width: 100%; padding: 12px 16px; background: var(--bg-glass);
  border: 1px solid var(--border-glass); border-radius: var(--radius-sm);
  font-size: 0.875rem; resize: vertical; min-height: 60px;
}
.special-input:focus { border-color: var(--gold); }

/* ========== CHECKOUT ========== */
.checkout-overlay {
  position: fixed; inset: 0; z-index: 4000;
  background: var(--bg-primary); overflow-y: auto;
  opacity: 0; visibility: hidden; transition: all 0.3s ease;
}
.checkout-overlay.open { opacity: 1; visibility: visible; }
.checkout-container {
  max-width: 640px; margin: 0 auto; padding: 24px; min-height: 100vh;
}
.checkout-header {
  display: flex; align-items: center; justify-content: space-between; margin-bottom: 32px;
}
.checkout-header h2 { font-size: 1.5rem; font-weight: 800; }
.checkout-steps {
  display: flex; align-items: center; justify-content: center; gap: 0; margin-bottom: 40px;
}
.step-dot {
  width: 36px; height: 36px; border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 0.8125rem; font-weight: 700;
  background: var(--bg-tertiary); border: 2px solid var(--border-glass);
  color: var(--text-muted); transition: all var(--transition); position: relative;
}
.step-dot.active { background: var(--gold); border-color: var(--gold); color: #0a0a0a; }
.step-dot.done { background: var(--success); border-color: var(--success); color: #fff; }
.step-line {
  width: 48px; height: 2px; background: var(--border-glass);
}
.step-line.done { background: var(--success); }
.checkout-step { display: none; }
.checkout-step.active { display: block; animation: fadeIn 0.3s ease; }
@keyframes fadeIn { from{opacity:0;transform:translateY(10px)} to{opacity:1;transform:translateY(0)} }
.form-group { margin-bottom: 20px; }
.form-group label {
  display: block; font-size: 0.8125rem; font-weight: 600;
  color: var(--text-muted); margin-bottom: 8px; text-transform: uppercase; letter-spacing: 0.04em;
}
.form-group input, .form-group select, .form-group textarea {
  width: 100%; padding: 14px 16px; background: var(--bg-glass);
  border: 1px solid var(--border-glass); border-radius: var(--radius-sm);
  font-size: 0.9375rem; transition: all var(--transition);
}
.form-group input:focus, .form-group select:focus, .form-group textarea:focus {
  border-color: var(--gold); box-shadow: 0 0 0 3px var(--gold-glow);
}
.form-group .error-msg { font-size: 0.75rem; color: var(--danger); margin-top: 6px; display: none; }
.form-group.has-error input, .form-group.has-error select { border-color: var(--danger); }
.form-group.has-error .error-msg { display: block; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
.payment-options { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.payment-opt {
  padding: 16px; text-align: center; border-radius: var(--radius-md);
  background: var(--bg-glass); border: 2px solid var(--border-glass);
  cursor: pointer; transition: all var(--transition); font-weight: 600; font-size: 0.875rem;
}
.payment-opt:hover, .payment-opt.active {
  border-color: var(--gold); background: rgba(245,197,66,0.08);
}
.payment-opt .pay-icon { font-size: 1.5rem; margin-bottom: 6px; }
.checkout-actions {
  display: flex; gap: 12px; margin-top: 32px;
}
.checkout-actions .btn { flex: 1; }
.order-summary-box {
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  border-radius: var(--radius-md); padding: 20px; margin-bottom: 24px;
}
.order-summary-box h4 { font-size: 0.875rem; font-weight: 700; margin-bottom: 12px; color: var(--text-muted); text-transform: uppercase; }
.summary-item {
  display: flex; justify-content: space-between; font-size: 0.875rem;
  padding: 6px 0; color: var(--text-secondary);
}
.summary-item .name { flex: 1; }
.geo-btn {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 10px 16px; font-size: 0.8125rem; font-weight: 600;
  background: var(--bg-glass); border: 1px solid var(--border-glass);
  border-radius: var(--radius-sm); margin-top: 8px; transition: all var(--transition);
}
.geo-btn:hover { border-color: var(--gold); color: var(--gold); }

/* ========== SUCCESS SCREEN ========== */
.success-screen {
  text-align: center; padding: 40px 0;
}
.success-check {
  width: 80px; height: 80px; margin: 0 auto 24px;
  border-radius: 50%; background: var(--success);
  display: flex; align-items: center; justify-content: center;
  animation: checkPop 0.5s cubic-bezier(0.34,1.56,0.64,1);
}
.success-check svg { width: 40px; height: 40px; stroke: #fff; stroke-width: 3; fill: none; }
@keyframes checkPop { 0%{transform:scale(0)} 100%{transform:scale(1)} }
.success-screen h2 { font-size: 1.75rem; font-weight: 800; margin-bottom: 8px; }
.success-screen .order-id { font-size: 1.125rem; color: var(--gold); font-weight: 700; margin-bottom: 8px; }
.success-screen .eta { color: var(--text-secondary); margin-bottom: 32px; }
.timeline {
  display: flex; flex-direction: column; align-items: flex-start;
  max-width: 280px; margin: 0 auto 32px; text-align: left;
}
.timeline-item {
  display: flex; align-items: center; gap: 16px; padding: 12px 0;
  position: relative; width: 100%;
}
.timeline-item::before {
  content: ''; position: absolute; left: 11px; top: 36px; bottom: -12px;
  width: 2px; background: var(--border-glass);
}
.timeline-item:last-child::before { display: none; }
.timeline-dot {
  width: 24px; height: 24px; border-radius: 50%; flex-shrink: 0;
  background: var(--bg-tertiary); border: 2px solid var(--border-glass);
  transition: all 0.4s ease; z-index: 1;
}
.timeline-item.active .timeline-dot {
  background: var(--gold); border-color: var(--gold);
  box-shadow: 0 0 12px var(--gold-glow);
}
.timeline-item.done .timeline-dot { background: var(--success); border-color: var(--success); }
.timeline-item.done::before { background: var(--success); }
.timeline-label { font-size: 0.9375rem; font-weight: 600; }

/* ========== TOAST ========== */
.toast-container {
  position: fixed; bottom: 100px; left: 50%; transform: translateX(-50%);
  z-index: 9000; display: flex; flex-direction: column; gap: 8px;
  pointer-events: none; width: min(360px, calc(100% - 32px));
}
.toast {
  padding: 14px 20px; background: var(--bg-secondary);
  border: 1px solid var(--border-glass); border-radius: var(--radius-md);
  box-shadow: var(--shadow-lg); font-size: 0.875rem; font-weight: 500;
  display: flex; align-items: center; gap: 10px;
  animation: toastIn 0.35s cubic-bezier(0.34,1.56,0.64,1);
  backdrop-filter: blur(16px);
}
.toast.hide { animation: toastOut 0.3s ease forwards; }
.toast .icon { color: var(--success); font-size: 1.125rem; }
@keyframes toastIn { from{opacity:0;transform:translateY(20px) scale(0.95)} to{opacity:1;transform:translateY(0) scale(1)} }
@keyframes toastOut { to{opacity:0;transform:translateY(10px) scale(0.95)} }

/* ========== MOBILE BOTTOM NAV ========== */
.bottom-nav {
  display: none; position: fixed; bottom: 0; left: 0; right: 0; z-index: 1000;
  height: var(--bottom-nav-height); background: rgba(10,10,10,0.9);
  backdrop-filter: blur(24px); border-top: 1px solid var(--border-subtle);
  padding: 0 8px; padding-bottom: env(safe-area-inset-bottom, 0);
}
[data-theme="light"] .bottom-nav { background: rgba(248,247,244,0.92); }
.bottom-nav-inner {
  display: flex; align-items: center; justify-content: space-around; height: 100%; max-width: 480px; margin: 0 auto;
}
.bnav-item {
  display: flex; flex-direction: column; align-items: center; gap: 2px;
  padding: 6px 12px; color: var(--text-muted); font-size: 0.65rem; font-weight: 600;
  transition: color var(--transition); position: relative; background: none; border: none;
}
.bnav-item svg { width: 22px; height: 22px; }
.bnav-item.active, .bnav-item:hover { color: var(--gold); }
.bnav-item .bnav-badge {
  position: absolute; top: 2px; right: 6px;
  min-width: 16px; height: 16px; padding: 0 4px;
  background: var(--gold); color: #0a0a0a; font-size: 0.6rem; font-weight: 700;
  border-radius: 8px; display: none; align-items: center; justify-content: center;
}
.bnav-item .bnav-badge.show { display: flex; }

.mobile-cart-bar {
  display: none; position: fixed; bottom: calc(var(--bottom-nav-height) + env(safe-area-inset-bottom, 0px));
  left: 0; right: 0; z-index: 999;
  padding: 12px 16px; background: var(--bg-secondary);
  border-top: 1px solid var(--border-subtle);
  transform: translateY(100%); transition: transform 0.3s ease;
}
.mobile-cart-bar.show { transform: translateY(0); }
.mobile-cart-bar .inner {
  display: flex; align-items: center; justify-content: space-between;
  max-width: 480px; margin: 0 auto; gap: 12px;
}
.mobile-cart-bar .info { font-size: 0.875rem; }
.mobile-cart-bar .info strong { font-size: 1rem; }
.mobile-cart-bar .btn { padding: 12px 24px; }

/* ========== LOYALTY ========== */
.loyalty-panel {
  padding: 24px; background: var(--bg-glass); border: 1px solid var(--border-glass);
  border-radius: var(--radius-xl); backdrop-filter: blur(12px);
  text-align: center; margin-bottom: 40px;
}
.loyalty-panel .points {
  font-size: 2.5rem; font-weight: 800; color: var(--gold); margin-bottom: 8px;
}
.loyalty-panel p { color: var(--text-secondary); font-size: 0.9375rem; }

/* ========== ORDERS HISTORY ========== */
.orders-list { display: flex; flex-direction: column; gap: 16px; }
.order-card {
  padding: 20px; background: var(--bg-glass); border: 1px solid var(--border-glass);
  border-radius: var(--radius-md); backdrop-filter: blur(8px);
}
.order-card-header {
  display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px;
}
.order-card-header .oid { font-weight: 700; font-size: 0.9375rem; }
.order-card-header .status {
  font-size: 0.75rem; font-weight: 700; padding: 4px 10px; border-radius: 6px;
  background: rgba(34,197,94,0.15); color: var(--success);
}
.order-card .date { font-size: 0.8125rem; color: var(--text-muted); margin-bottom: 8px; }
.order-card .items { font-size: 0.875rem; color: var(--text-secondary); margin-bottom: 12px; }
.order-card .total-row {
  display: flex; justify-content: space-between; align-items: center;
}
.order-card .total-row strong { font-size: 1rem; }

/* ========== SKELETON ========== */
.skeleton {
  background: linear-gradient(90deg, var(--bg-tertiary) 25%, var(--bg-glass) 50%, var(--bg-tertiary) 75%);
  background-size: 200% 100%; animation: shimmer 1.5s infinite; border-radius: var(--radius-sm);
}
@keyframes shimmer { 0%{background-position:200% 0} 100%{background-position:-200% 0} }

/* ========== REVEAL ANIMATIONS ========== */
.reveal {
  opacity: 0; transform: translateY(30px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.reveal.visible { opacity: 1; transform: translateY(0); }

/* ========== FAVORITES SECTION ========== */
#favorites-section { display: none; }
#favorites-section.active { display: block; }
#orders-section { display: none; }
#orders-section.active { display: block; }

/* ========== RESPONSIVE ========== */
@media (max-width: 1100px) {
  .products-grid { grid-template-columns: repeat(3, 1fr); }
  .promos-grid { grid-template-columns: repeat(2, 1fr); }
  .contact-grid { grid-template-columns: repeat(2, 1fr); }
  .stats-row { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 768px) {
  .nav-links { display: none; }
  .hamburger { display: flex; }
  .hero-content { grid-template-columns: 1fr; text-align: center; }
  .hero-text p { margin-left: auto; margin-right: auto; }
  .hero-btns { justify-content: center; }
  .hero-visual { order: -1; }
  .hero-food { max-width: 280px; }
  .products-grid { grid-template-columns: repeat(2, 1fr); gap: 12px; }
  .promos-grid { grid-template-columns: 1fr; }
  .about-grid { grid-template-columns: 1fr; gap: 32px; }
  .about-features { grid-template-columns: 1fr; }
  .rating-overview { grid-template-columns: 1fr; gap: 24px; }
  .contact-grid { grid-template-columns: 1fr 1fr; }
  .form-row { grid-template-columns: 1fr; }
  .payment-options { grid-template-columns: 1fr 1fr; }
  .bottom-nav { display: block; }
  body { padding-bottom: calc(var(--bottom-nav-height) + 16px); }
  .section { padding: 48px 16px; }
  .product-card .card-body { padding: 12px; }
  .product-card .card-name { font-size: 0.875rem; }
  .product-card .add-btn { padding: 6px 10px; font-size: 0.75rem; }
  .categories { justify-content: flex-start; flex-wrap: nowrap; }
  .search-shortcut { display: none; }
  .nav-actions .nav-btn:not(.cart-nav-btn):not(.theme-btn) { display: none; }
}
@media (max-width: 480px) {
  .products-grid { grid-template-columns: 1fr 1fr; gap: 10px; }
  .stats-row { grid-template-columns: 1fr 1fr; }
  .hero-text h1 { font-size: 1.75rem; }
  .contact-grid { grid-template-columns: 1fr; }
}
</style>
</head>
<body>
<!-- LOADER -->
<div id="loader">
  <div class="loader-logo">
    <svg class="loader-star" viewBox="0 0 40 40" fill="none"><path d="M20 2l4.5 13.8H39l-11.5 8.4 4.4 13.6L20 29.4 8.1 37.8l4.4-13.6L1 15.8h14.5L20 2z" fill="#f5c542"/></svg>
    YULDUZCHA
  </div>
  <div class="loader-bar"><div class="loader-bar-fill"></div></div>
</div>

<!-- NAVBAR -->
<nav class="navbar" id="navbar">
  <div class="nav-progress" id="navProgress"></div>
  <div class="nav-inner">
    <a href="#hero" class="nav-logo" onclick="scrollToSection('hero')">
      <svg viewBox="0 0 28 28" fill="none"><path d="M14 1.5l3.2 9.8H28l-8.2 6 3.1 9.7L14 20.8 5.1 27l3.1-9.7L0 11.3h10.8L14 1.5z" fill="#f5c542"/></svg>
      YULDUZCHA
    </a>
    <div class="nav-links">
      <a href="#hero" class="active" data-section="hero">Bosh sahifa</a>
      <a href="#menu" data-section="menu">Menyu</a>
      <a href="#promos" data-section="promos">Aksiyalar</a>
      <a href="#about" data-section="about">Biz haqimizda</a>
      <a href="#contact" data-section="contact">Kontakt</a>
    </div>
    <div class="nav-actions">
      <button class="nav-btn" id="searchNavBtn" aria-label="Qidiruv" onclick="focusSearch()">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
      </button>
      <button class="nav-btn" id="favNavBtn" aria-label="Sevimlilar" onclick="showFavorites()">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg>
        <span class="badge" id="favBadge">0</span>
      </button>
      <button class="nav-btn theme-btn" id="themeBtn" aria-label="Mavzu" onclick="toggleTheme()">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" class="sun-icon"><circle cx="12" cy="12" r="5"/><path d="M12 1v2M12 21v2M4.22 4.22l1.42 1.42M18.36 18.36l1.42 1.42M1 12h2M21 12h2M4.22 19.78l1.42-1.42M18.36 5.64l1.42-1.42"/></svg>
      </button>
      <button class="nav-btn cart-nav-btn" id="cartNavBtn" aria-label="Savat" onclick="openCart()">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"/></svg>
        <span class="badge" id="cartBadge">0</span>
      </button>
      <button class="hamburger" id="hamburger" aria-label="Menyu" onclick="toggleMobileMenu()">
        <span></span><span></span><span></span>
      </button>
    </div>
  </div>
</nav>

<!-- MOBILE MENU -->
<div class="mobile-menu" id="mobileMenu">
  <a href="#hero" onclick="closeMobileMenu();scrollToSection('hero')">Bosh sahifa</a>
  <a href="#menu" onclick="closeMobileMenu();scrollToSection('menu')">Menyu</a>
  <a href="#promos" onclick="closeMobileMenu();scrollToSection('promos')">Aksiyalar</a>
  <a href="#about" onclick="closeMobileMenu();scrollToSection('about')">Biz haqimizda</a>
  <a href="#contact" onclick="closeMobileMenu();scrollToSection('contact')">Kontakt</a>
  <a href="#" onclick="closeMobileMenu();showFavorites()">Sevimlilar</a>
  <a href="#" onclick="closeMobileMenu();showOrders()">Buyurtmalarim</a>
</div>

<!-- HERO -->
<section class="hero" id="hero">
  <div class="hero-bg"></div>
  <div class="hero-overlay"></div>
  <div class="hero-particles" id="heroParticles"></div>
  <div class="hero-content">
    <div class="hero-text reveal">
      <h1>Har luqmada <span>YULDUZCHA</span> ta’mi.</h1>
      <p>Yangi tayyorlangan lavashlar, burgerlar va sevimli fast-foodlaringiz. Tez yetkazib berish, premium sifat.</p>
      <div class="hero-btns">
        <button class="btn btn-primary" onclick="scrollToSection('menu')">MENYUNI KO‘RISH</button>
        <button class="btn btn-secondary" onclick="openCart()">BUYURTMA BERISH</button>
      </div>
    </div>
    <div class="hero-visual reveal">
      <div class="hero-glow"></div>
      <img class="hero-food" src="https://images.unsplash.com/photo-1529006557810-274b9b2fc783?w=600&q=80" alt="YULDUZCHA Lavash" loading="eager" onerror="this.style.display='none'">
    </div>
  </div>
</section>

<!-- MENU -->
<section class="section" id="menu">
  <div class="section-header reveal">
    <span class="section-label">Menyu</span>
    <h2>Sevimli taomlaringiz</h2>
    <p>Eng yangi va eng mazali taomlarimizni tanlang</p>
  </div>
  <div class="menu-controls reveal">
    <div class="search-box">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
      <input type="text" id="searchInput" placeholder="Lavash, burger yoki ichimlik qidiring..." autocomplete="off">
      <span class="search-shortcut">Ctrl+K</span>
    </div>
    <div class="search-count" id="searchCount"></div>
    <div class="categories" id="categories"></div>
  </div>
  <div class="products-grid" id="productsGrid"></div>
</section>

<!-- FAVORITES (hidden by default) -->
<section class="section" id="favorites-section">
  <div class="section-header">
    <span class="section-label">Sevimlilar</span>
    <h2>Sevimli taomlaringiz</h2>
  </div>
  <div class="products-grid" id="favoritesGrid"></div>
</section>

<!-- ORDERS HISTORY -->
<section class="section" id="orders-section">
  <div class="section-header">
    <span class="section-label">Buyurtmalar</span>
    <h2>Buyurtmalarim</h2>
  </div>
  <div class="orders-list" id="ordersList"></div>
</section>

<!-- PROMOTIONS -->
<section class="section" id="promos">
  <div class="section-header reveal">
    <span class="section-label">Aksiyalar</span>
    <h2>Maxsus takliflar</h2>
    <p>YULDUZCHA combo va chegirmali to‘plamlar</p>
  </div>
  <div class="promos-grid" id="promosGrid"></div>
</section>

<!-- LOYALTY -->
<section class="section" style="padding-top:0">
  <div class="loyalty-panel reveal" id="loyaltyPanel">
    <div class="points">⭐ <span id="loyaltyPoints">0</span> ball</div>
    <p id="loyaltyMsg">Har 10 000 so‘m uchun 1 ball olasiz. 100 ball = 10 000 so‘m chegirma!</p>
  </div>
</section>

<!-- ABOUT -->
<section class="section" id="about">
  <div class="section-header reveal">
    <span class="section-label">Biz haqimizda</span>
    <h2>Nima uchun YULDUZCHA?</h2>
  </div>
  <div class="about-grid">
    <div class="reveal">
      <p style="color:var(--text-secondary);font-size:1.0625rem;line-height:1.7;margin-bottom:8px">
        YULDUZCHA — Toshkentning eng mazali va tezkor fast-food brendi. Biz har bir lavashni yangi pishiramiz, eng yaxshi mahsulotlardan foydalanamiz va buyurtmangizni issiq holda yetkazib beramiz.
      </p>
      <div class="about-features">
        <div class="about-feature"><div class="icon">🥬</div><h4>Yangi mahsulotlar</h4><p>Har kuni yangi yetkazib beriladigan ingredientlar</p></div>
        <div class="about-feature"><div class="icon">👨‍🍳</div><h4>Professional oshpazlar</h4><p>Tajribali mutaxassislar tomonidan tayyorlanadi</p></div>
        <div class="about-feature"><div class="icon">⚡</div><h4>Tez yetkazib berish</h4><p>O‘rtacha 25-40 daqiqada eshigingizda</p></div>
        <div class="about-feature"><div class="icon">✨</div><h4>Toza oshxona</h4><p>Eng yuqori gigiyena standartlari</p></div>
      </div>
    </div>
    <div class="reveal">
      <img src="https://images.unsplash.com/photo-1555396273-367ea4eb4db5?w=600&q=80" alt="YULDUZCHA Kitchen" style="border-radius:var(--radius-xl);width:100%;aspect-ratio:4/3;object-fit:cover;border:1px solid var(--border-glass)" loading="lazy" onerror="this.style.display='none'">
    </div>
  </div>
  <div class="stats-row reveal" id="statsRow">
    <div class="stat-item"><div class="num" data-target="10000">0</div><div class="label">Buyurtma</div></div>
    <div class="stat-item"><div class="num" data-target="4.9" data-decimal="1">0</div><div class="label">Reyting</div></div>
    <div class="stat-item"><div class="num" data-target="25">0</div><div class="label">Daqiqa (o‘rtacha)</div></div>
    <div class="stat-item"><div class="num" data-target="100">0</div><div class="label">% Yangi tayyorlash</div></div>
  </div>
</section>

<!-- REVIEWS -->
<section class="section" id="reviews">
  <div class="section-header reveal">
    <span class="section-label">Sharhlar</span>
    <h2>Mijozlarimiz nima deydi</h2>
  </div>
  <div class="rating-overview reveal">
    <div class="rating-score">
      <div class="big">4.9</div>
      <div class="stars">★★★★★</div>
      <div class="total">1,247 sharh</div>
    </div>
    <div class="rating-bars">
      <div class="rating-bar-row"><span>5 yulduz</span><div class="rating-bar-track"><div class="rating-bar-fill" data-width="92"></div></div><span>92%</span></div>
      <div class="rating-bar-row"><span>4 yulduz</span><div class="rating-bar-track"><div class="rating-bar-fill" data-width="6"></div></div><span>6%</span></div>
      <div class="rating-bar-row"><span>3 yulduz</span><div class="rating-bar-track"><div class="rating-bar-fill" data-width="1"></div></div><span>1%</span></div>
      <div class="rating-bar-row"><span>2 yulduz</span><div class="rating-bar-track"><div class="rating-bar-fill" data-width="1"></div></div><span>1%</span></div>
      <div class="rating-bar-row"><span>1 yulduz</span><div class="rating-bar-track"><div class="rating-bar-fill" data-width="0"></div></div><span>0%</span></div>
    </div>
  </div>
  <div class="reviews-sort reveal">
    <button class="active" data-sort="newest" onclick="sortReviews('newest')">Eng yangi</button>
    <button data-sort="helpful" onclick="sortReviews('helpful')">Eng foydali</button>
    <button data-sort="highest" onclick="sortReviews('highest')">Eng yuqori baho</button>
  </div>
  <div class="reviews-list reveal" id="reviewsList"></div>
</section>

<!-- CONTACT -->
<section class="section" id="contact">
  <div class="section-header reveal">
    <span class="section-label">Kontakt</span>
    <h2>Biz bilan bog‘laning</h2>
  </div>
  <div class="contact-grid reveal" id="contactGrid"></div>
</section>

<!-- FOOTER -->
<footer class="footer">
  <div class="footer-logo">
    <svg width="24" height="24" viewBox="0 0 28 28" fill="none"><path d="M14 1.5l3.2 9.8H28l-8.2 6 3.1 9.7L14 20.8 5.1 27l3.1-9.7L0 11.3h10.8L14 1.5z" fill="#f5c542"/></svg>
    YULDUZCHA
  </div>
  <div class="footer-links">
    <a href="#menu">Menyu</a>
    <a href="#promos">Aksiyalar</a>
    <a href="#about">Biz haqimizda</a>
    <a href="#contact">Kontakt</a>
  </div>
  <p>© 2026 YULDUZCHA. Barcha huquqlar himoyalangan.</p>
</footer>

<!-- BOTTOM NAV (Mobile) -->
<nav class="bottom-nav" id="bottomNav">
  <div class="bottom-nav-inner">
    <button class="bnav-item active" data-page="home" onclick="goPage('home')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>
      Bosh
    </button>
    <button class="bnav-item" data-page="menu" onclick="goPage('menu')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 3h18v18H3zM3 9h18M3 15h18M9 3v18"/></svg>
      Menyu
    </button>
    <button class="bnav-item" data-page="fav" onclick="goPage('fav')">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg>
      Sevimli
    </button>
    <button class="bnav-item" data-page="cart" onclick="openCart()">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"/></svg>
      Savat
      <span class="bnav-badge" id="bnavCartBadge">0</span>
    </button>
  </div>
</nav>

<!-- MOBILE CART BAR -->
<div class="mobile-cart-bar" id="mobileCartBar">
  <div class="inner">
    <div class="info"><span id="mcbCount">0</span> ta mahsulot · <strong id="mcbTotal">0 so‘m</strong></div>
    <button class="btn btn-primary btn-sm" onclick="openCart()">Savat</button>
  </div>
</div>

<!-- CART DRAWER -->
<div class="cart-overlay" id="cartOverlay" onclick="closeCart()"></div>
<aside class="cart-drawer" id="cartDrawer">
  <div class="cart-header">
    <h3>Savat (<span id="cartCountLabel">0</span>)</h3>
    <button class="cart-close" onclick="closeCart()" aria-label="Yopish">×</button>
  </div>
  <div class="cart-body" id="cartBody"></div>
  <div class="cart-footer" id="cartFooter" style="display:none">
    <div class="free-delivery-bar" id="freeDeliveryBar">
      <p id="freeDeliveryText"></p>
      <div class="progress-track"><div class="progress-fill" id="freeDeliveryProgress"></div></div>
    </div>
    <div class="coupon-field">
      <input type="text" id="couponInput" placeholder="Promo kod">
      <button onclick="applyCoupon()">Qo‘llash</button>
    </div>
    <div class="coupon-msg" id="couponMsg"></div>
    <div class="cart-summary">
      <div class="cart-row"><span>Oraliq summa</span><span id="cartSubtotal">0 so‘m</span></div>
      <div class="cart-row" id="cartDiscountRow" style="display:none"><span>Chegirma</span><span id="cartDiscount" style="color:var(--success)">-0 so‘m</span></div>
      <div class="cart-row"><span>Yetkazib berish</span><span id="cartDelivery">0 so‘m</span></div>
      <div class="cart-row total"><span>Jami</span><span id="cartTotal">0 so‘m</span></div>
    </div>
    <button class="btn btn-primary btn-block" onclick="startCheckout()">BUYURTMA BERISH</button>
  </div>
</aside>

<!-- PRODUCT MODAL -->
<div class="modal-overlay" id="productModal" onclick="if(event.target===this)closeProductModal()">
  <div class="modal" id="productModalInner"></div>
</div>

<!-- CHECKOUT -->
<div class="checkout-overlay" id="checkoutOverlay">
  <div class="checkout-container">
    <div class="checkout-header">
      <h2>Buyurtma</h2>
      <button class="cart-close" onclick="closeCheckout()" aria-label="Yopish">×</button>
    </div>
    <div class="checkout-steps" id="checkoutSteps">
      <div class="step-dot active" data-step="1">1</div>
      <div class="step-line" data-line="1"></div>
      <div class="step-dot" data-step="2">2</div>
      <div class="step-line" data-line="2"></div>
      <div class="step-dot" data-step="3">3</div>
      <div class="step-line" data-line="3"></div>
      <div class="step-dot" data-step="4">4</div>
    </div>

    <!-- STEP 1: Customer -->
    <div class="checkout-step active" id="step1">
      <div class="form-group" id="nameGroup">
        <label>Ism</label>
        <input type="text" id="customerName" placeholder="Ismingizni kiriting">
        <div class="error-msg">Ismingizni kiriting</div>
      </div>
      <div class="form-group" id="phoneGroup">
        <label>Telefon</label>
        <input type="tel" id="customerPhone" placeholder="+998 90 123 45 67" maxlength="17">
        <div class="error-msg">Telefon raqamingizni tekshiring</div>
      </div>
      <div class="checkout-actions">
        <button class="btn btn-primary btn-block" onclick="goCheckoutStep(2)">Davom etish</button>
      </div>
    </div>

    <!-- STEP 2: Address -->
    <div class="checkout-step" id="step2">
      <div class="form-group" id="cityGroup">
        <label>Shahar</label>
        <input type="text" id="addrCity" value="Toshkent" placeholder="Shahar">
        <div class="error-msg">Shaharni kiriting</div>
      </div>
      <div class="form-group" id="districtGroup">
        <label>Tuman</label>
        <input type="text" id="addrDistrict" placeholder="Tuman">
        <div class="error-msg">Tumanni kiriting</div>
      </div>
      <div class="form-row">
        <div class="form-group" id="streetGroup">
          <label>Ko‘cha</label>
          <input type="text" id="addrStreet" placeholder="Ko‘cha nomi">
          <div class="error-msg">Ko‘chani kiriting</div>
        </div>
        <div class="form-group" id="houseGroup">
          <label>Uy</label>
          <input type="text" id="addrHouse" placeholder="Uy raqami">
          <div class="error-msg">Uy raqamini kiriting</div>
        </div>
      </div>
      <div class="form-row">
        <div class="form-group">
          <label>Kvartira</label>
          <input type="text" id="addrApt" placeholder="Ixtiyoriy">
        </div>
        <div class="form-group">
          <label>Qavat / Kirish</label>
          <input type="text" id="addrFloor" placeholder="Ixtiyoriy">
        </div>
      </div>
      <div class="form-group">
        <label>Mo‘ljal</label>
        <input type="text" id="addrLandmark" placeholder="Masalan: Metro yonida">
      </div>
      <button class="geo-btn" onclick="detectLocation()">📍 Joylashuvimni aniqlash</button>
      <div class="checkout-actions">
        <button class="btn btn-secondary" onclick="goCheckoutStep(1)">Orqaga</button>
        <button class="btn btn-primary" onclick="goCheckoutStep(3)">Davom etish</button>
      </div>
    </div>

    <!-- STEP 3: Payment -->
    <div class="checkout-step" id="step3">
      <div class="form-group">
        <label>To‘lov usuli</label>
        <div class="payment-options">
          <div class="payment-opt active" data-pay="cash" onclick="selectPayment(this)"><div class="pay-icon">💵</div>Naqd pul</div>
          <div class="payment-opt" data-pay="card" onclick="selectPayment(this)"><div class="pay-icon">💳</div>Karta</div>
          <div class="payment-opt" data-pay="click" onclick="selectPayment(this)"><div class="pay-icon">📱</div>Click</div>
          <div class="payment-opt" data-pay="payme" onclick="selectPayment(this)"><div class="pay-icon">💙</div>Payme</div>
        </div>
      </div>
      <div class="checkout-actions">
        <button class="btn btn-secondary" onclick="goCheckoutStep(2)">Orqaga</button>
        <button class="btn btn-primary" onclick="goCheckoutStep(4)">Davom etish</button>
      </div>
    </div>

    <!-- STEP 4: Confirm -->
    <div class="checkout-step" id="step4">
      <div class="order-summary-box" id="orderSummaryBox"></div>
      <div class="checkout-actions">
        <button class="btn btn-secondary" onclick="goCheckoutStep(3)">Orqaga</button>
        <button class="btn btn-primary" id="confirmOrderBtn" onclick="confirmOrder()">TASDIQLASH</button>
      </div>
    </div>

    <!-- SUCCESS -->
    <div class="checkout-step" id="stepSuccess">
      <div class="success-screen">
        <div class="success-check">
          <svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg>
        </div>
        <h2>Buyurtmangiz qabul qilindi!</h2>
        <div class="order-id" id="successOrderId">YL-000000</div>
        <p class="eta">Taxminiy yetkazib berish: <strong>25–40 daqiqa</strong></p>
        <div class="timeline" id="orderTimeline">
          <div class="timeline-item active done"><div class="timeline-dot"></div><div class="timeline-label">Buyurtma qabul qilindi</div></div>
          <div class="timeline-item active"><div class="timeline-dot"></div><div class="timeline-label">Tayyorlanmoqda</div></div>
          <div class="timeline-item"><div class="timeline-dot"></div><div class="timeline-label">Yetkazilmoqda</div></div>
          <div class="timeline-item"><div class="timeline-dot"></div><div class="timeline-label">Yetkazildi</div></div>
        </div>
        <button class="btn btn-primary" onclick="closeCheckout();showOrders()">Buyurtmalarimni ko‘rish</button>
      </div>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast-container" id="toastContainer"></div>

<script>
/* ============================================================
   1. RESTAURANT CONFIGURATION
   ============================================================ */
const RESTAURANT_CONFIG = {
  restaurantName: 'YULDUZCHA',
  phone: '+998 90 123 45 67',
  telegram: '@YULDUZCHA',
  instagram: '@YULDUZCHA',
  address: 'Toshkent, O‘zbekiston',
  deliveryFee: 5000,
  freeDeliveryThreshold: 100000,
  currency: 'so‘m',
  workingHours: '10:00 — 23:00'
};

/* ============================================================
   2. PRODUCT DATABASE
   ============================================================ */
const PRODUCTS = [
  { id: 1, name: 'Klassik Lavash', category: 'Lavash', price: 32000, oldPrice: 40000, description: 'Yangi pishirilgan non, mol go‘shti, yangi sabzavotlar va maxsus sous. Klassik ta’m.', image: 'https://images.unsplash.com/photo-1529006557810-274b9b2fc783?w=600&q=80', rating: 4.9, reviews: 342, badge: 'Hit', ingredients: ['Lavash noni', 'Mol go‘shti', 'Pomidor', 'Bodring', 'Piyoz', 'Mayonez', 'Ketchup'], extras: true },
  { id: 2, name: 'Pishloqli Lavash', category: 'Lavash', price: 36000, oldPrice: null, description: 'Erigan pishloq, mol go‘shti va yangi sabzavotlar bilan boyitilgan lavash.', image: 'https://images.unsplash.com/photo-1626700051175-6818013e1d4f?w=600&q=80', rating: 4.8, reviews: 218, badge: null, ingredients: ['Lavash noni', 'Mol go‘shti', 'Pishloq', 'Pomidor', 'Mayonez'], extras: true },
  { id: 3, name: 'Mol Go‘shtli Lavash', category: 'Lavash', price: 38000, oldPrice: 45000, description: 'Qo‘shimcha mol go‘shti bo‘laklari, qarsildoq non va maxsus sous.', image: 'https://images.unsplash.com/photo-1565299624946-b28f40a0ae38?w=600&q=80', rating: 4.9, reviews: 189, badge: '-15%', ingredients: ['Lavash noni', 'Extra mol go‘shti', 'Sabzavotlar', 'Garlic sous'], extras: true },
  { id: 4, name: 'Achchiq Lavash', category: 'Lavash', price: 34000, oldPrice: null, description: 'Olovli achchiq sous, mol go‘shti va yangi sabzavotlar. Achchiq sevuvchilar uchun!', image: 'https://images.unsplash.com/photo-1599487489732-ad6d2c2b0d4d?w=600&q=80', rating: 4.7, reviews: 156, badge: 'Achchiq', ingredients: ['Lavash noni', 'Mol go‘shti', 'Achchiq sous', 'Jalapeno', 'Sabzavotlar'], extras: true },
  { id: 5, name: 'Chicken Burger', category: 'Burger', price: 35000, oldPrice: 42000, description: 'Qarsildoq tovuq kotleti, yangi salat, pomidor va maxsus sous.', image: 'https://images.unsplash.com/photo-1568901346375-23c9450c58cd?w=600&q=80', rating: 4.8, reviews: 276, badge: 'Hit', ingredients: ['Burger noni', 'Tovuq kotleti', 'Salat', 'Pomidor', 'Mayonez'], extras: true },
  { id: 6, name: 'Beef Burger', category: 'Burger', price: 40000, oldPrice: null, description: 'Suyuq mol go‘shti kotleti, cheddar pishloq, karamelizatsiyalangan piyoz.', image: 'https://images.unsplash.com/photo-1553979459-d2229ba7433b?w=600&q=80', rating: 4.9, reviews: 198, badge: null, ingredients: ['Burger noni', 'Mol go‘shti kotleti', 'Cheddar', 'Piyoz', 'Sous'], extras: true },
  { id: 7, name: 'Hot Dog', category: 'Hot Dog', price: 22000, oldPrice: 28000, description: 'Klassik hot dog, qarsildoq sosiska, yangi non va souslar.', image: 'https://images.unsplash.com/photo-1612392062126-3a65c0491def?w=600&q=80', rating: 4.6, reviews: 134, badge: '-21%', ingredients: ['Hot dog noni', 'Sosiska', 'Ketchup', 'Mayonez', 'Piyoz'], extras: false },
  { id: 8, name: 'Kartoshka Fri', category: 'Fri', price: 15000, oldPrice: null, description: 'Oltin rangdagi qarsildoq kartoshka fri. Tuz va maxsus ziravorlar bilan.', image: 'https://images.unsplash.com/photo-1573080496219-bb080dd4f877?w=600&q=80', rating: 4.7, reviews: 412, badge: null, ingredients: ['Kartoshka', 'O‘simlik yog‘i', 'Tuz'], extras: false },
  { id: 9, name: 'Nuggets', category: 'Nuggets', price: 25000, oldPrice: 30000, description: '6 dona qarsildoq tovuq naggetsi. Sous bilan birga.', image: 'https://images.unsplash.com/photo-1562967914-608f82629710?w=600&q=80', rating: 4.8, reviews: 267, badge: null, ingredients: ['Tovuq go‘shti', 'Panirovka', 'Sous'], extras: false },
  { id: 10, name: 'Cola', category: 'Ichimlik', price: 8000, oldPrice: null, description: 'Sovuq Coca-Cola 0.5L', image: 'https://images.unsplash.com/photo-1554866585-cd94860890b7?w=600&q=80', rating: 4.5, reviews: 89, badge: null, ingredients: ['Gazli ichimlik'], extras: false },
  { id: 11, name: 'Fanta', category: 'Ichimlik', price: 8000, oldPrice: null, description: 'Sovuq Fanta 0.5L', image: 'https://images.unsplash.com/photo-1624517452489-f3c4e4e4c8e5?w=600&q=80', rating: 4.4, reviews: 67, badge: null, ingredients: ['Gazli ichimlik'], extras: false },
  { id: 12, name: 'Sprite', category: 'Ichimlik', price: 8000, oldPrice: null, description: 'Sovuq Sprite 0.5L', image: 'https://images.unsplash.com/photo-1625772299848-391b6a87d7b3?w=600&q=80', rating: 4.5, reviews: 72, badge: null, ingredients: ['Gazli ichimlik'], extras: false },
  { id: 13, name: 'Garlic Sauce', category: 'Sous', price: 5000, oldPrice: null, description: 'Uyda tayyorlangan sarimsoqli sous. 50ml', image: 'https://images.unsplash.com/photo-1472476443507-c7a8ba43e40b?w=600&q=80', rating: 4.9, reviews: 145, badge: null, ingredients: ['Sarimsoq', 'Mayonez', 'Ziravorlar'], extras: false },
  { id: 14, name: 'Spicy Sauce', category: 'Sous', price: 5000, oldPrice: null, description: 'Olovli achchiq sous. 50ml', image: 'https://images.unsplash.com/photo-1598511724997-8a1a0f3a0c5e?w=600&q=80', rating: 4.7, reviews: 98, badge: 'Achchiq', ingredients: ['Chili', 'Sarimsoq', 'Ziravorlar'], extras: false },
  { id: 15, name: 'YULDUZCHA COMBO', category: 'Combo', price: 79000, oldPrice: 95000, description: '2 ta Lavash + 1 Fri + 2 Ichimlik. Ideal oilaviy to‘plam!', image: 'https://images.unsplash.com/photo-1594212699903-ec8a3eca50f5?w=600&q=80', rating: 5.0, reviews: 87, badge: '-17%', ingredients: ['2x Lavash', 'Kartoshka Fri', '2x Ichimlik'], extras: false }
];

const CATEGORIES = ['Barchasi', 'Lavash', 'Burger', 'Hot Dog', 'Fri', 'Nuggets', 'Ichimlik', 'Sous', 'Combo'];

const COUPONS = {
  'YULDUZ10': { type: 'percent', value: 10 },
  'STAR15': { type: 'percent', value: 15 },
  'LAVASH20': { type: 'percent', value: 20 }
};

const REVIEWS_DATA = [
  { id: 1, name: 'Jasur A.', rating: 5, date: '2026-10-05', text: 'Eng mazali lavash Toshkentda! Yetkazib berish juda tez, 20 daqiqada yetib keldi. Tavsiya qilaman!', helpful: 24 },
  { id: 2, name: 'Madina K.', rating: 5, date: '2026-10-03', text: 'Pishloqli lavash ajoyib chiqdi. Pishloq erigan, non qarsildoq. Yana buyurtma beraman.', helpful: 18 },
  { id: 3, name: 'Bobur R.', rating: 4, date: '2026-09-28', text: 'Burger zo‘r, lekin fri biroz sovuq edi. Umuman olganda yaxshi xizmat.', helpful: 7 },
  { id: 4, name: 'Dilnoza S.', rating: 5, date: '2026-09-25', text: 'Combo juda foydali! Oilamiz uchun ideal. Bola ham yoqtirib yedi.', helpful: 31 },
  { id: 5, name: 'Sardor T.', rating: 5, date: '2026-09-20', text: 'Achchiq lavash — olov! Achchiqni yaxshi ko‘raman, bu eng yaxshisi.', helpful: 15 }
];

/* ============================================================
   3. STATE MANAGEMENT
   ============================================================ */
let state = {
  cart: [],
  favorites: [],
  orders: [],
  theme: 'dark',
  activeCategory: 'Barchasi',
  searchQuery: '',
  coupon: null,
  loyaltyPoints: 0,
  checkoutStep: 1,
  selectedPayment: 'cash',
  currentProduct: null,
  modalQty: 1,
  modalExtras: { cheese: false, meat: false, sauce: false },
  modalOptions: { bread: 'Oddiy', sauce: 'Mayonez', spicy: 0 },
  modalSpecial: '',
  reviewSort: 'newest'
};

/* ============================================================
   4. LOCAL STORAGE HELPERS
   ============================================================ */
function saveData(key, data) {
  try { localStorage.setItem('yulduzcha_' + key, JSON.stringify(data)); } catch(e) {}
}
function loadData(key, fallback) {
  try {
    const v = localStorage.getItem('yulduzcha_' + key);
    return v ? JSON.parse(v) : fallback;
  } catch(e) { return fallback; }
}
function removeData(key) {
  try { localStorage.removeItem('yulduzcha_' + key); } catch(e) {}
}

function loadState() {
  state.cart = loadData('cart', []);
  state.favorites = loadData('favorites', []);
  state.orders = loadData('orders', []);
  state.theme = loadData('theme', 'dark');
  state.coupon = loadData('coupon', null);
  state.loyaltyPoints = loadData('loyaltyPoints', 0);
  const cust = loadData('customer', {});
  if (cust.name) document.getElementById('customerName').value = cust.name;
  if (cust.phone) document.getElementById('customerPhone').value = cust.phone;
}

function persistState() {
  saveData('cart', state.cart);
  saveData('favorites', state.favorites);
  saveData('orders', state.orders);
  saveData('theme', state.theme);
  saveData('coupon', state.coupon);
  saveData('loyaltyPoints', state.loyaltyPoints);
}

/* ============================================================
   5. UTILITY
   ============================================================ */
function formatPrice(n) {
  return n.toLocaleString('uz-UZ') + ' ' + RESTAURANT_CONFIG.currency;
}
function escapeHtml(str) {
  const d = document.createElement('div');
  d.textContent = str;
  return d.innerHTML;
}
function generateOrderId() {
  return 'YL-' + Math.random().toString(36).substring(2, 8).toUpperCase();
}
function showToast(msg) {
  const c = document.getElementById('toastContainer');
  const t = document.createElement('div');
  t.className = 'toast';
  t.innerHTML = `<span class="icon">✓</span> ${escapeHtml(msg)}`;
  c.appendChild(t);
  setTimeout(() => { t.classList.add('hide'); setTimeout(() => t.remove(), 300); }, 2800);
}

/* ============================================================
   6. THEME
   ============================================================ */
function applyTheme() {
  document.documentElement.setAttribute('data-theme', state.theme);
  persistState();
}
function toggleTheme() {
  state.theme = state.theme === 'dark' ? 'light' : 'dark';
  applyTheme();
}

/* ============================================================
   7. NAVIGATION & SCROLL
   ============================================================ */
function scrollToSection(id) {
  const el = document.getElementById(id);
  if (el) el.scrollIntoView({ behavior: 'smooth' });
  document.querySelectorAll('.nav-links a').forEach(a => {
    a.classList.toggle('active', a.dataset.section === id);
  });
}
function toggleMobileMenu() {
  document.getElementById('hamburger').classList.toggle('open');
  document.getElementById('mobileMenu').classList.toggle('open');
}
function closeMobileMenu() {
  document.getElementById('hamburger').classList.remove('open');
  document.getElementById('mobileMenu').classList.remove('open');
}
function focusSearch() {
  scrollToSection('menu');
  setTimeout(() => document.getElementById('searchInput').focus(), 400);
}
function goPage(page) {
  document.querySelectorAll('.bnav-item').forEach(b => b.classList.remove('active'));
  document.querySelector(`.bnav-item[data-page="${page}"]`)?.classList.add('active');
  document.getElementById('favorites-section').classList.remove('active');
  document.getElementById('orders-section').classList.remove('active');
  if (page === 'home') scrollToSection('hero');
  else if (page === 'menu') scrollToSection('menu');
  else if (page === 'fav') showFavorites();
}

/* ============================================================
   8. PRODUCTS RENDER
   ============================================================ */
function getFilteredProducts() {
  let list = PRODUCTS.slice();
  if (state.activeCategory !== 'Barchasi') {
    list = list.filter(p => p.category === state.activeCategory);
  }
  if (state.searchQuery) {
    const q = state.searchQuery.toLowerCase();
    list = list.filter(p =>
      p.name.toLowerCase().includes(q) ||
      p.description.toLowerCase().includes(q) ||
      p.category.toLowerCase().includes(q)
    );
  }
  return list;
}

function renderCategories() {
  const el = document.getElementById('categories');
  el.innerHTML = CATEGORIES.map(c =>
    `<button class="cat-pill ${state.activeCategory === c ? 'active' : ''}" onclick="setCategory('${c}')">${c}</button>`
  ).join('');
}

function setCategory(cat) {
  state.activeCategory = cat;
  renderCategories();
  renderProducts();
}

function renderProducts() {
  const list = getFilteredProducts();
  const grid = document.getElementById('productsGrid');
  const countEl = document.getElementById('searchCount');
  if (state.searchQuery) {
    countEl.textContent = list.length ? `${list.length} ta natija topildi` : '';
  } else {
    countEl.textContent = '';
  }
  if (!list.length) {
    grid.innerHTML = `<div class="empty-state" style="grid-column:1/-1">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
      <h3>Hech narsa topilmadi</h3>
      <p>Boshqa so‘rov bilan qidirib ko‘ring</p>
    </div>`;
    return;
  }
  grid.innerHTML = list.map(p => productCardHTML(p)).join('');
}

function productCardHTML(p) {
  const inCart = state.cart.find(i => i.id === p.id && !i.customKey);
  const isFav = state.favorites.includes(p.id);
  const discount = p.oldPrice ? Math.round((1 - p.price / p.oldPrice) * 100) : 0;
  return `
  <div class="product-card" data-id="${p.id}" onclick="openProductModal(${p.id})">
    <div class="img-wrap">
      ${p.badge ? `<span class="badge-tag">${escapeHtml(p.badge)}</span>` : ''}
      <button class="fav-btn ${isFav ? 'active' : ''}" onclick="event.stopPropagation();toggleFavorite(${p.id})" aria-label="Sevimli">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="${isFav ? '#ef4444' : 'none'}" stroke="currentColor" stroke-width="2"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg>
      </button>
      <img src="${p.image}" alt="${escapeHtml(p.name)}" loading="lazy" onerror="this.parentElement.innerHTML+='<div class=\\'img-fallback\\'>🍽️</div>';this.remove();">
    </div>
    <div class="card-body">
      <div class="card-cat">${escapeHtml(p.category)}</div>
      <div class="card-name">${escapeHtml(p.name)}</div>
      <div class="card-desc">${escapeHtml(p.description)}</div>
      <div class="card-rating">
        <span class="stars">★ ${p.rating}</span>
        <span class="count">${p.reviews} sharh</span>
      </div>
      <div class="card-footer">
        <div class="price-block">
          <span class="price">${formatPrice(p.price)}</span>
          ${p.oldPrice ? `<span class="old-price">${formatPrice(p.oldPrice)}</span>` : ''}
          ${discount ? `<span class="discount">-${discount}%</span>` : ''}
        </div>
        <div class="qty-controls ${inCart ? 'show' : ''}" id="qty-${p.id}" onclick="event.stopPropagation()">
          <button onclick="updateCartQty(${p.id}, -1)">−</button>
          <span>${inCart ? inCart.qty : 0}</span>
          <button onclick="updateCartQty(${p.id}, 1)">+</button>
        </div>
        <button class="add-btn" style="${inCart ? 'display:none' : ''}" id="addbtn-${p.id}" onclick="event.stopPropagation();quickAdd(${p.id})">+ Savatga</button>
      </div>
    </div>
  </div>`;
}

/* ============================================================
   9. CART
   ============================================================ */
function quickAdd(id) {
  const p = PRODUCTS.find(x => x.id === id);
  if (!p) return;
  const existing = state.cart.find(i => i.id === id && !i.customKey);
  if (existing) {
    existing.qty++;
  } else {
    state.cart.push({
      id: p.id, name: p.name, price: p.price, image: p.image,
      qty: 1, customKey: null, customSummary: '', extras: {}
    });
  }
  persistState();
  updateCartUI();
  renderProducts();
  showToast(`${p.name} savatga qo‘shildi`);
  animateCartBadge();
}

function updateCartQty(id, delta, customKey) {
  const idx = state.cart.findIndex(i => i.id === id && (customKey ? i.customKey === customKey : !i.customKey));
  if (idx === -1) return;
  state.cart[idx].qty += delta;
  if (state.cart[idx].qty <= 0) state.cart.splice(idx, 1);
  persistState();
  updateCartUI();
  renderProducts();
  if (document.getElementById('cartDrawer').classList.contains('open')) renderCart();
}

function removeFromCart(id, customKey) {
  state.cart = state.cart.filter(i => !(i.id === id && (customKey ? i.customKey === customKey : !i.customKey)));
  persistState();
  updateCartUI();
  renderProducts();
  renderCart();
}

function getCartTotals() {
  let subtotal = state.cart.reduce((s, i) => s + i.price * i.qty, 0);
  let discount = 0;
  if (state.coupon && COUPONS[state.coupon]) {
    const c = COUPONS[state.coupon];
    if (c.type === 'percent') discount = Math.round(subtotal * c.value / 100);
  }
  const afterDiscount = subtotal - discount;
  const delivery = afterDiscount >= RESTAURANT_CONFIG.freeDeliveryThreshold ? 0 : RESTAURANT_CONFIG.deliveryFee;
  const total = afterDiscount + delivery;
  return { subtotal, discount, delivery, total };
}

function updateCartUI() {
  const count = state.cart.reduce((s, i) => s + i.qty, 0);
  const { total } = getCartTotals();
  const badge = document.getElementById('cartBadge');
  const bnavBadge = document.getElementById('bnavCartBadge');
  badge.textContent = count;
  badge.classList.toggle('show', count > 0);
  bnavBadge.textContent = count;
  bnavBadge.classList.toggle('show', count > 0);
  document.getElementById('cartCountLabel').textContent = count;
  const mcb = document.getElementById('mobileCartBar');
  if (count > 0) {
    mcb.classList.add('show');
    document.getElementById('mcbCount').textContent = count;
    document.getElementById('mcbTotal').textContent = formatPrice(total);
  } else {
    mcb.classList.remove('show');
  }
}

function animateCartBadge() {
  const btn = document.getElementById('cartNavBtn');
  btn.classList.add('pulse');
  setTimeout(() => btn.classList.remove('pulse'), 400);
}

function openCart() {
  renderCart();
  document.getElementById('cartOverlay').classList.add('open');
  document.getElementById('cartDrawer').classList.add('open');
  document.body.style.overflow = 'hidden';
}
function closeCart() {
  document.getElementById('cartOverlay').classList.remove('open');
  document.getElementById('cartDrawer').classList.remove('open');
  document.body.style.overflow = '';
}

function renderCart() {
  const body = document.getElementById('cartBody');
  const footer = document.getElementById('cartFooter');
  if (!state.cart.length) {
    body.innerHTML = `<div class="empty-state">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"/></svg>
      <h3>Savatda hali mahsulot yo‘q</h3>
      <p>Menyudan taom tanlang</p>
    </div>`;
    footer.style.display = 'none';
    return;
  }
  footer.style.display = 'block';
  body.innerHTML = state.cart.map(item => `
    <div class="cart-item">
      <img src="${item.image}" alt="" onerror="this.src='';this.style.background='var(--bg-tertiary)'">
      <div class="cart-item-info">
        <h4>${escapeHtml(item.name)}</h4>
        ${item.customSummary ? `<div class="custom">${escapeHtml(item.customSummary)}</div>` : ''}
        <div class="cart-item-actions">
          <div class="qty">
            <button onclick="updateCartQty(${item.id}, -1, ${item.customKey ? `'${item.customKey}'` : 'null'})">−</button>
            <span>${item.qty}</span>
            <button onclick="updateCartQty(${item.id}, 1, ${item.customKey ? `'${item.customKey}'` : 'null'})">+</button>
          </div>
          <span class="cart-item-price">${formatPrice(item.price * item.qty)}</span>
        </div>
        <div class="cart-item-remove" onclick="removeFromCart(${item.id}, ${item.customKey ? `'${item.customKey}'` : 'null'})">O‘chirish</div>
      </div>
    </div>
  `).join('');

  const { subtotal, discount, delivery, total } = getCartTotals();
  document.getElementById('cartSubtotal').textContent = formatPrice(subtotal);
  const discRow = document.getElementById('cartDiscountRow');
  if (discount > 0) {
    discRow.style.display = 'flex';
    document.getElementById('cartDiscount').textContent = '-' + formatPrice(discount);
  } else {
    discRow.style.display = 'none';
  }
  document.getElementById('cartDelivery').textContent = delivery === 0 ? 'BEPUL' : formatPrice(delivery);
  document.getElementById('cartTotal').textContent = formatPrice(total);

  const remaining = RESTAURANT_CONFIG.freeDeliveryThreshold - (subtotal - discount);
  const progress = Math.min(100, ((subtotal - discount) / RESTAURANT_CONFIG.freeDeliveryThreshold) * 100);
  document.getElementById('freeDeliveryProgress').style.width = progress + '%';
  if (remaining > 0) {
    document.getElementById('freeDeliveryText').textContent = `Yana ${formatPrice(remaining)}lik buyurtma qilsangiz yetkazib berish BEPUL.`;
  } else {
    document.getElementById('freeDeliveryText').textContent = '🎉 Yetkazib berish BEPUL!';
  }
}

/* ============================================================
   10. COUPON
   ============================================================ */
function applyCoupon() {
  const code = document.getElementById('couponInput').value.trim().toUpperCase();
  const msg = document.getElementById('couponMsg');
  if (!code) { msg.textContent = 'Promo kodni kiriting'; msg.className = 'coupon-msg error'; return; }
  if (COUPONS[code]) {
    state.coupon = code;
    persistState();
    msg.textContent = 'Promo kod qabul qilindi ✓';
    msg.className = 'coupon-msg success';
    renderCart();
  } else {
    msg.textContent = 'Bu promo kod mavjud emas';
    msg.className = 'coupon-msg error';
  }
}

/* ============================================================
   11. FAVORITES
   ============================================================ */
function toggleFavorite(id) {
  const idx = state.favorites.indexOf(id);
  if (idx === -1) state.favorites.push(id);
  else state.favorites.splice(idx, 1);
  persistState();
  updateFavBadge();
  renderProducts();
  if (document.getElementById('favorites-section').classList.contains('active')) renderFavorites();
}

function updateFavBadge() {
  const b = document.getElementById('favBadge');
  b.textContent = state.favorites.length;
  b.classList.toggle('show', state.favorites.length > 0);
}

function showFavorites() {
  document.getElementById('favorites-section').classList.add('active');
  document.getElementById('orders-section').classList.remove('active');
  renderFavorites();
  document.getElementById('favorites-section').scrollIntoView({ behavior: 'smooth' });
}

function renderFavorites() {
  const grid = document.getElementById('favoritesGrid');
  const list = PRODUCTS.filter(p => state.favorites.includes(p.id));
  if (!list.length) {
    grid.innerHTML = `<div class="empty-state" style="grid-column:1/-1">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg>
      <h3>Sevimli taomlaringiz shu yerda paydo bo‘ladi</h3>
      <p>Yurakcha belgisini bosing</p>
    </div>`;
    return;
  }
  grid.innerHTML = list.map(p => productCardHTML(p)).join('');
}

/* ============================================================
   12. PRODUCT MODAL
   ============================================================ */
function openProductModal(id) {
  const p = PRODUCTS.find(x => x.id === id);
  if (!p) return;
  state.currentProduct = p;
  state.modalQty = 1;
  state.modalExtras = { cheese: false, meat: false, sauce: false };
  state.modalOptions = { bread: 'Oddiy', sauce: 'Mayonez', spicy: 0 };
  state.modalSpecial = '';
  renderProductModal();
  document.getElementById('productModal').classList.add('open');
  document.body.style.overflow = 'hidden';
}

function closeProductModal() {
  document.getElementById('productModal').classList.remove('open');
  document.body.style.overflow = '';
  state.currentProduct = null;
}

function calcModalPrice() {
  const p = state.currentProduct;
  if (!p) return 0;
  let price = p.price;
  if (state.modalExtras.cheese) price += 5000;
  if (state.modalExtras.meat) price += 10000;
  if (state.modalExtras.sauce) price += 2000;
  return price * state.modalQty;
}

function renderProductModal() {
  const p = state.currentProduct;
  if (!p) return;
  const price = calcModalPrice();
  const isLavash = p.category === 'Lavash' || p.extras;
  document.getElementById('productModalInner').innerHTML = `
    <button class="modal-close" onclick="closeProductModal()" aria-label="Yopish">×</button>
    <img class="modal-img" src="${p.image}" alt="${escapeHtml(p.name)}" onerror="this.style.background='var(--bg-tertiary)'">
    <div class="modal-body">
      <h2>${escapeHtml(p.name)}</h2>
      <div class="modal-rating"><span class="stars">★ ${p.rating}</span><span style="color:var(--text-muted)">${p.reviews} sharh</span></div>
      <p class="modal-desc">${escapeHtml(p.description)}</p>
      ${p.ingredients ? `<div class="modal-section"><h4>Tarkibi</h4><p style="font-size:0.875rem;color:var(--text-secondary)">${p.ingredients.join(', ')}</p></div>` : ''}
      ${isLavash ? `
      <div class="modal-section">
        <h4>Non</h4>
        <div class="option-group">
          <button class="option-btn ${state.modalOptions.bread==='Oddiy'?'active':''}" onclick="setModalOpt('bread','Oddiy')">Oddiy</button>
          <button class="option-btn ${state.modalOptions.bread==='Qarsildoq'?'active':''}" onclick="setModalOpt('bread','Qarsildoq')">Qarsildoq</button>
        </div>
      </div>
      <div class="modal-section">
        <h4>Sous</h4>
        <div class="option-group">
          ${['Ketchup','Mayonez','Garlic','Spicy'].map(s =>
            `<button class="option-btn ${state.modalOptions.sauce===s?'active':''}" onclick="setModalOpt('sauce','${s}')">${s}</button>`
          ).join('')}
        </div>
      </div>
      <div class="modal-section">
        <h4>Achchiqlik</h4>
        <div class="option-group">
          ${[0,1,2,3,4].map(s =>
            `<button class="option-btn ${state.modalOptions.spicy===s?'active':''}" onclick="setModalOpt('spicy',${s})">${s}</button>`
          ).join('')}
        </div>
      </div>
      <div class="modal-section">
        <h4>Qo‘shimchalar</h4>
        <div class="extra-item"><label><input type="checkbox" ${state.modalExtras.cheese?'checked':''} onchange="toggleExtra('cheese')"> Extra pishloq</label><span>+5 000</span></div>
        <div class="extra-item"><label><input type="checkbox" ${state.modalExtras.meat?'checked':''} onchange="toggleExtra('meat')"> Extra go‘sht</label><span>+10 000</span></div>
        <div class="extra-item"><label><input type="checkbox" ${state.modalExtras.sauce?'checked':''} onchange="toggleExtra('sauce')"> Extra sous</label><span>+2 000</span></div>
      </div>
      ` : ''}
      <div class="modal-section">
        <h4>Maxsus izoh</h4>
        <textarea class="special-input" id="modalSpecial" placeholder="Masalan: piyozsiz..." oninput="state.modalSpecial=this.value">${escapeHtml(state.modalSpecial)}</textarea>
      </div>
      <div class="modal-price-row">
        <div class="modal-price">${formatPrice(price)}</div>
        <div class="modal-qty">
          <button onclick="changeModalQty(-1)">−</button>
          <span>${state.modalQty}</span>
          <button onclick="changeModalQty(1)">+</button>
        </div>
      </div>
      <button class="btn btn-primary btn-block" style="margin-top:16px" onclick="addCustomToCart()">SAVATGA QO‘SHISH</button>
    </div>
  `;
}

function setModalOpt(key, val) {
  state.modalOptions[key] = val;
  renderProductModal();
}
function toggleExtra(key) {
  state.modalExtras[key] = !state.modalExtras[key];
  renderProductModal();
}
function changeModalQty(d) {
  state.modalQty = Math.max(1, state.modalQty + d);
  renderProductModal();
}

function addCustomToCart() {
  const p = state.currentProduct;
  if (!p) return;
  let unitPrice = p.price;
  if (state.modalExtras.cheese) unitPrice += 5000;
  if (state.modalExtras.meat) unitPrice += 10000;
  if (state.modalExtras.sauce) unitPrice += 2000;
  const summaryParts = [];
  if (p.extras || p.category === 'Lavash') {
    summaryParts.push(state.modalOptions.bread);
    summaryParts.push(state.modalOptions.sauce);
    if (state.modalOptions.spicy > 0) summaryParts.push(`Achchiq: ${state.modalOptions.spicy}`);
    if (state.modalExtras.cheese) summaryParts.push('Extra pishloq');
    if (state.modalExtras.meat) summaryParts.push('Extra go‘sht');
    if (state.modalExtras.sauce) summaryParts.push('Extra sous');
  }
  if (state.modalSpecial) summaryParts.push(state.modalSpecial);
  const customKey = summaryParts.length ? btoa(unescape(encodeURIComponent(JSON.stringify({ opts: state.modalOptions, extras: state.modalExtras, special: state.modalSpecial })))).substring(0, 16) : null;
  const existing = state.cart.find(i => i.id === p.id && i.customKey === customKey);
  if (existing) {
    existing.qty += state.modalQty;
  } else {
    state.cart.push({
      id: p.id, name: p.name, price: unitPrice, image: p.image,
      qty: state.modalQty, customKey, customSummary: summaryParts.join(' · '),
      extras: { ...state.modalExtras }, options: { ...state.modalOptions }
    });
  }
  persistState();
  updateCartUI();
  renderProducts();
  closeProductModal();
  showToast(`${p.name} savatga qo‘shildi`);
  animateCartBadge();
}

/* ============================================================
   13. CHECKOUT
   ============================================================ */
function startCheckout() {
  if (!state.cart.length) { showToast('Savatda mahsulot yo‘q'); return; }
  closeCart();
  state.checkoutStep = 1;
  showCheckoutStep(1);
  document.getElementById('checkoutOverlay').classList.add('open');
  document.body.style.overflow = 'hidden';
}

function closeCheckout() {
  document.getElementById('checkoutOverlay').classList.remove('open');
  document.body.style.overflow = '';
}

function showCheckoutStep(n) {
  document.querySelectorAll('.checkout-step').forEach(s => s.classList.remove('active'));
  if (n === 'success') {
    document.getElementById('stepSuccess').classList.add('active');
    return;
  }
  document.getElementById('step' + n).classList.add('active');
  document.querySelectorAll('.step-dot').forEach(d => {
    const s = parseInt(d.dataset.step);
    d.classList.toggle('active', s === n);
    d.classList.toggle('done', s < n);
  });
  document.querySelectorAll('.step-line').forEach(l => {
    l.classList.toggle('done', parseInt(l.dataset.line) < n);
  });
  state.checkoutStep = n;
  if (n === 4) renderOrderSummary();
}

function goCheckoutStep(n) {
  if (n > state.checkoutStep) {
    if (state.checkoutStep === 1 && !validateStep1()) return;
    if (state.checkoutStep === 2 && !validateStep2()) return;
  }
  showCheckoutStep(n);
}

function validateStep1() {
  let ok = true;
  const name = document.getElementById('customerName').value.trim();
  const phone = document.getElementById('customerPhone').value.trim();
  const nameG = document.getElementById('nameGroup');
  const phoneG = document.getElementById('phoneGroup');
  nameG.classList.remove('has-error');
  phoneG.classList.remove('has-error');
  if (!name || name.length < 2) { nameG.classList.add('has-error'); ok = false; }
  const phoneClean = phone.replace(/\s/g, '');
  if (!/^\+?998\d{9}$/.test(phoneClean) && !/^\d{9}$/.test(phoneClean)) {
    phoneG.classList.add('has-error'); ok = false;
  }
  if (ok) {
    saveData('customer', { name, phone });
  }
  return ok;
}

function validateStep2() {
  let ok = true;
  ['city','district','street','house'].forEach(f => {
    const el = document.getElementById('addr' + f.charAt(0).toUpperCase() + f.slice(1));
    const g = document.getElementById(f + 'Group');
    if (g) g.classList.remove('has-error');
    if (!el.value.trim()) { if (g) g.classList.add('has-error'); ok = false; }
  });
  return ok;
}

function selectPayment(el) {
  document.querySelectorAll('.payment-opt').forEach(o => o.classList.remove('active'));
  el.classList.add('active');
  state.selectedPayment = el.dataset.pay;
}

function renderOrderSummary() {
  const { subtotal, discount, delivery, total } = getCartTotals();
  const name = document.getElementById('customerName').value;
  const phone = document.getElementById('customerPhone').value;
  const addr = [
    document.getElementById('addrCity').value,
    document.getElementById('addrDistrict').value,
    document.getElementById('addrStreet').value,
    'uy ' + document.getElementById('addrHouse').value,
    document.getElementById('addrApt').value ? 'kv ' + document.getElementById('addrApt').value : ''
  ].filter(Boolean).join(', ');
  const payLabels = { cash: 'Naqd pul', card: 'Karta', click: 'Click', payme: 'Payme' };
  document.getElementById('orderSummaryBox').innerHTML = `
    <h4>Buyurtma tafsilotlari</h4>
    ${state.cart.map(i => `<div class="summary-item"><span class="name">${escapeHtml(i.name)} ×${i.qty}</span><span>${formatPrice(i.price * i.qty)}</span></div>`).join('')}
    <div class="summary-item" style="margin-top:12px;border-top:1px solid var(--border-subtle);padding-top:12px"><span>Oraliq</span><span>${formatPrice(subtotal)}</span></div>
    ${discount ? `<div class="summary-item"><span>Chegirma</span><span style="color:var(--success)">-${formatPrice(discount)}</span></div>` : ''}
    <div class="summary-item"><span>Yetkazib berish</span><span>${delivery === 0 ? 'BEPUL' : formatPrice(delivery)}</span></div>
    <div class="summary-item" style="font-weight:800;font-size:1.0625rem;color:var(--text-primary)"><span>Jami</span><span>${formatPrice(total)}</span></div>
    <div style="margin-top:16px;font-size:0.875rem;color:var(--text-secondary)">
      <p><strong>${escapeHtml(name)}</strong> · ${escapeHtml(phone)}</p>
      <p>${escapeHtml(addr)}</p>
      <p>To‘lov: ${payLabels[state.selectedPayment] || state.selectedPayment}</p>
    </div>
  `;
}

function confirmOrder() {
  const btn = document.getElementById('confirmOrderBtn');
  btn.disabled = true;
  btn.textContent = 'Yuborilmoqda...';
  const { subtotal, discount, delivery, total } = getCartTotals();
  const orderId = generateOrderId();
  const order = {
    id: orderId,
    date: new Date().toISOString(),
    items: state.cart.map(i => ({ ...i })),
    subtotal, discount, delivery, total,
    customer: {
      name: document.getElementById('customerName').value,
      phone: document.getElementById('customerPhone').value,
      address: [
        document.getElementById('addrCity').value,
        document.getElementById('addrDistrict').value,
        document.getElementById('addrStreet').value,
        document.getElementById('addrHouse').value
      ].join(', ')
    },
    payment: state.selectedPayment,
    status: 'accepted',
    coupon: state.coupon
  };
  state.orders.unshift(order);
  const pointsEarned = Math.floor(total / 10000);
  state.loyaltyPoints += pointsEarned;
  state.cart = [];
  state.coupon = null;
  persistState();
  updateCartUI();
  updateLoyaltyUI();
  document.getElementById('successOrderId').textContent = orderId;
  showCheckoutStep('success');
  btn.disabled = false;
  btn.textContent = 'TASDIQLASH';
  // Animate timeline
  setTimeout(() => {
    const items = document.querySelectorAll('#orderTimeline .timeline-item');
    if (items[1]) { items[1].classList.add('done'); items[1].classList.remove('active'); }
    if (items[2]) items[2].classList.add('active');
  }, 3000);
}

function detectLocation() {
  if (!navigator.geolocation) { showToast('Geolokatsiya qo‘llab-quvvatlanmaydi'); return; }
  navigator.geolocation.getCurrentPosition(
    pos => {
      document.getElementById('addrCity').value = 'Toshkent';
      document.getElementById('addrLandmark').value = `Lat: ${pos.coords.latitude.toFixed(4)}, Lng: ${pos.coords.longitude.toFixed(4)}`;
      showToast('Joylashuv aniqlandi');
    },
    () => showToast('Joylashuvni aniqlab bo‘lmadi')
  );
}

/* Phone formatting */
document.getElementById('customerPhone').addEventListener('input', function(e) {
  let v = e.target.value.replace(/\D/g, '');
  if (v.startsWith('998')) v = v.substring(3);
  if (v.length > 9) v = v.substring(0, 9);
  let formatted = '+998';
  if (v.length > 0) formatted += ' ' + v.substring(0, 2);
  if (v.length > 2) formatted += ' ' + v.substring(2, 5);
  if (v.length > 5) formatted += ' ' + v.substring(5, 7);
  if (v.length > 7) formatted += ' ' + v.substring(7, 9);
  e.target.value = formatted;
});

/* ============================================================
   14. ORDERS HISTORY
   ============================================================ */
function showOrders() {
  document.getElementById('orders-section').classList.add('active');
  document.getElementById('favorites-section').classList.remove('active');
  renderOrders();
  document.getElementById('orders-section').scrollIntoView({ behavior: 'smooth' });
}

function renderOrders() {
  const list = document.getElementById('ordersList');
  if (!state.orders.length) {
    list.innerHTML = `<div class="empty-state">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>
      <h3>Hali buyurtmalar yo‘q</h3>
      <p>Birinchi buyurtmangizni bering!</p>
    </div>`;
    return;
  }
  list.innerHTML = state.orders.map(o => {
    const date = new Date(o.date).toLocaleDateString('uz-UZ', { day: 'numeric', month: 'long', year: 'numeric', hour: '2-digit', minute: '2-digit' });
    const itemsStr = o.items.map(i => `${i.name} ×${i.qty}`).join(', ');
    return `<div class="order-card">
      <div class="order-card-header">
        <span class="oid">${escapeHtml(o.id)}</span>
        <span class="status">Yetkazildi</span>
      </div>
      <div class="date">${date}</div>
      <div class="items">${escapeHtml(itemsStr)}</div>
      <div class="total-row">
        <strong>${formatPrice(o.total)}</strong>
        <button class="btn btn-secondary btn-sm" onclick="reorder('${o.id}')">Qayta buyurtma</button>
      </div>
    </div>`;
  }).join('');
}

function reorder(orderId) {
  const order = state.orders.find(o => o.id === orderId);
  if (!order) return;
  order.items.forEach(item => {
    const existing = state.cart.find(c => c.id === item.id && c.customKey === item.customKey);
    if (existing) existing.qty += item.qty;
    else state.cart.push({ ...item });
  });
  persistState();
  updateCartUI();
  showToast('Buyurtma savatga qo‘shildi');
  openCart();
}

/* ============================================================
   15. PROMOTIONS
   ============================================================ */
function renderPromos() {
  const combo = PRODUCTS.find(p => p.id === 15);
  const grid = document.getElementById('promosGrid');
  grid.innerHTML = `
    <div class="promo-card" onclick="openProductModal(15)">
      <img src="${combo.image}" alt="Combo" loading="lazy" onerror="this.style.background='var(--bg-tertiary)'">
      <div class="promo-badge">-17%</div>
      <div class="promo-overlay">
        <h3>YULDUZCHA COMBO</h3>
        <p>2 Lavash + 1 Fri + 2 Ichimlik</p>
        <div class="promo-price"><span class="new">${formatPrice(79000)}</span><span class="old">${formatPrice(95000)}</span></div>
      </div>
    </div>
    <div class="promo-card" onclick="setCategory('Lavash');scrollToSection('menu')">
      <img src="https://images.unsplash.com/photo-1529006557810-274b9b2fc783?w=600&q=80" alt="Lavash" loading="lazy">
      <div class="promo-badge">HIT</div>
      <div class="promo-overlay">
        <h3>Lavashlar</h3>
        <p>Klassikdan achchiqgacha</p>
        <div class="promo-price"><span class="new">32 000 so‘mdan</span></div>
      </div>
    </div>
    <div class="promo-card" onclick="document.getElementById('couponInput').value='YULDUZ10';openCart()">
      <img src="https://images.unsplash.com/photo-1565299624946-b28f40a0ae38?w=600&q=80" alt="Promo" loading="lazy">
      <div class="promo-badge">-10%</div>
      <div class="promo-overlay">
        <h3>YULDUZ10</h3>
        <p>Promo kod bilan 10% chegirma</p>
        <div class="promo-price"><span class="new">Kodni qo‘llang</span></div>
      </div>
    </div>
  `;
}

/* ============================================================
   16. REVIEWS
   ============================================================ */
function sortReviews(sort) {
  state.reviewSort = sort;
  document.querySelectorAll('.reviews-sort button').forEach(b => b.classList.toggle('active', b.dataset.sort === sort));
  renderReviews();
}

function renderReviews() {
  let list = REVIEWS_DATA.slice();
  if (state.reviewSort === 'helpful') list.sort((a, b) => b.helpful - a.helpful);
  else if (state.reviewSort === 'highest') list.sort((a, b) => b.rating - a.rating);
  else list.sort((a, b) => new Date(b.date) - new Date(a.date));
  document.getElementById('reviewsList').innerHTML = list.map(r => {
    const initials = r.name.split(' ').map(w => w[0]).join('');
    const date = new Date(r.date).toLocaleDateString('uz-UZ', { day: 'numeric', month: 'short' });
    return `<div class="review-card">
      <div class="review-header">
        <div class="review-avatar">${initials}</div>
        <div class="review-meta"><div class="name">${escapeHtml(r.name)}</div><div class="date">${date}</div></div>
        <div class="review-stars">${'★'.repeat(r.rating)}${'☆'.repeat(5 - r.rating)}</div>
      </div>
      <p class="review-text">${escapeHtml(r.text)}</p>
      <div class="review-helpful" onclick="this.classList.toggle('active')">👍 Foydali (${r.helpful})</div>
    </div>`;
  }).join('');
}

/* ============================================================
   17. LOYALTY & CONTACT
   ============================================================ */
function updateLoyaltyUI() {
  document.getElementById('loyaltyPoints').textContent = state.loyaltyPoints;
  const needed = 100 - (state.loyaltyPoints % 100);
  document.getElementById('loyaltyMsg').textContent = `${needed} ball yig‘sangiz 10 000 so‘mlik chegirmaga ega bo‘lasiz.`;
}

function renderContact() {
  const c = RESTAURANT_CONFIG;
  document.getElementById('contactGrid').innerHTML = `
    <div class="contact-card"><div class="icon">📞</div><h4>Telefon</h4><a href="tel:${c.phone.replace(/\s/g,'')}">${c.phone}</a></div>
    <div class="contact-card"><div class="icon">✈️</div><h4>Telegram</h4><p>${c.telegram}</p></div>
    <div class="contact-card"><div class="icon">📷</div><h4>Instagram</h4><p>${c.instagram}</p></div>
    <div class="contact-card"><div class="icon">🕐</div><h4>Ish vaqti</h4><p>${c.workingHours}</p></div>
  `;
}

/* ============================================================
   18. SEARCH
   ============================================================ */
document.getElementById('searchInput').addEventListener('input', function(e) {
  state.searchQuery = e.target.value.trim();
  renderProducts();
});

document.addEventListener('keydown', function(e) {
  if ((e.ctrlKey || e.metaKey) && e.key === 'k') {
    e.preventDefault();
    focusSearch();
  }
});

/* ============================================================
   19. SCROLL EFFECTS
   ============================================================ */
window.addEventListener('scroll', function() {
  const nav = document.getElementById('navbar');
  nav.classList.toggle('scrolled', window.scrollY > 50);
  const progress = document.getElementById('navProgress');
  const h = document.documentElement.scrollHeight - window.innerHeight;
  progress.style.width = (h > 0 ? (window.scrollY / h) * 100 : 0) + '%';
}, { passive: true });

/* Intersection Observer for reveals & stats */
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
      if (entry.target.id === 'statsRow') animateStats();
      if (entry.target.classList.contains('rating-overview')) animateBars();
    }
  });
}, { threshold: 0.15 });

function animateStats() {
  document.querySelectorAll('#statsRow .num').forEach(el => {
    if (el.dataset.animated) return;
    el.dataset.animated = '1';
    const target = parseFloat(el.dataset.target);
    const decimal = el.dataset.decimal ? parseInt(el.dataset.decimal) : 0;
    const duration = 1500;
    const start = performance.now();
    function tick(now) {
      const t = Math.min(1, (now - start) / duration);
      const eased = 1 - Math.pow(1 - t, 3);
      el.textContent = decimal ? (target * eased).toFixed(decimal) : Math.floor(target * eased).toLocaleString();
      if (t < 1) requestAnimationFrame(tick);
      else el.textContent = decimal ? target.toFixed(decimal) : target.toLocaleString() + (target >= 1000 ? '+' : '');
    }
    requestAnimationFrame(tick);
  });
}

function animateBars() {
  document.querySelectorAll('.rating-bar-fill').forEach(el => {
    el.style.width = el.dataset.width + '%';
  });
}

/* ============================================================
   20. BUTTON RIPPLE
   ============================================================ */
document.addEventListener('click', function(e) {
  const btn = e.target.closest('.btn');
  if (!btn) return;
  const ripple = document.createElement('span');
  ripple.className = 'ripple';
  const rect = btn.getBoundingClientRect();
  const size = Math.max(rect.width, rect.height);
  ripple.style.width = ripple.style.height = size + 'px';
  ripple.style.left = (e.clientX - rect.left - size / 2) + 'px';
  ripple.style.top = (e.clientY - rect.top - size / 2) + 'px';
  btn.appendChild(ripple);
  setTimeout(() => ripple.remove(), 600);
});

/* ============================================================
   21. HERO PARTICLES
   ============================================================ */
function createParticles() {
  const container = document.getElementById('heroParticles');
  for (let i = 0; i < 20; i++) {
    const p = document.createElement('div');
    p.className = 'particle';
    p.style.left = Math.random() * 100 + '%';
    p.style.top = Math.random() * 100 + '%';
    p.style.animationDelay = Math.random() * 8 + 's';
    p.style.animationDuration = (6 + Math.random() * 6) + 's';
    container.appendChild(p);
  }
}

/* ============================================================
   22. INIT
   ============================================================ */
function init() {
  loadState();
  applyTheme();
  renderCategories();
  renderProducts();
  renderPromos();
  renderReviews();
  renderContact();
  updateCartUI();
  updateFavBadge();
  updateLoyaltyUI();
  createParticles();

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
  const stats = document.getElementById('statsRow');
  if (stats) observer.observe(stats);
  const ratingOv = document.querySelector('.rating-overview');
  if (ratingOv) observer.observe(ratingOv);

  // Loader
  setTimeout(() => {
    document.getElementById('loader').classList.add('hide');
  }, 2000);
}

document.addEventListener('DOMContentLoaded', init);
</script>
</body>
</html>
