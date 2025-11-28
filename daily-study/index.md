---
layout: page
title: Daily Study Log
permalink: /daily-study/
---

<style>
  /* ================= Global Layout ================= */
  .markdown-body {
    max-width: 100% !important; margin: 0 !important; width: 100% !important; padding: 0 10px;
    font-family: 'Pretendard', -apple-system, sans-serif;
  }
  
  /* ================= 1. Contribution Heatmap (잔디) ================= */
  .heatmap-section { margin-bottom: 40px; }
  .heatmap-title { font-size: 0.9em; font-weight: 600; color: #86868b; margin-bottom: 10px; }
  .heatmap-grid {
    display: grid; grid-template-columns: repeat(52, 1fr); grid-template-rows: repeat(7, 1fr);
    gap: 3px; max-width: 100%; overflow-x: auto; padding-bottom: 5px;
  }
  .day-box {
    width: 10px; height: 10px; background-color: #ebedf0; border-radius: 2px;
  }
  /* 잔디 색상 레벨 (JS로 제어) */
  .day-l1 { background-color: #9be9a8; }
  .day-l2 { background-color: #40c463; }
  .day-l3 { background-color: #30a14e; }
  .day-l4 { background-color: #216e39; }

  /* ================= 2. Featured Research (핵심 연구) ================= */
  .featured-section {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
    gap: 20px; margin-bottom: 50px;
  }
  .featured-card {
    background: #fbfbfd; border: 1px solid #eaeaea; border-radius: 12px;
    padding: 24px; transition: transform 0.2s, box-shadow 0.2s; position: relative; overflow: hidden;
  }
  .featured-card:hover { transform: translateY(-3px); box-shadow: 0 10px 30px rgba(0,0,0,0.08); border-color: #0066cc; }
  .featured-tag {
    font-size: 0.75em; font-weight: 700; color: #0066cc; text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 8px; display: block;
  }
  .featured-title { font-size: 1.3em; font-weight: 700; margin-bottom: 10px; line-height: 1.3; }
  .featured-desc { font-size: 0.95em; color: #666; line-height: 1.6; margin-bottom: 20px; }
  .featured-link { font-weight: 600; color: #1d1d1f; text-decoration: none; display: inline-flex; align-items: center; }
  .featured-link::after { content: '→'; margin-left: 5px; transition: margin-left 0.2s; }
  .featured-card:hover .featured-link::after { margin-left: 10px; }

  /* ================= 3. Tech Focus Timeline (기존 유지) ================= */
  .timeline-section { margin-bottom: 40px; padding-bottom: 30px; border-bottom: 1px solid #eaeaea; }
  .timeline-title { font-size: 1.2em; font-weight: 700; color: #1d1d1f; margin-bottom: 20px; }
  .timeline-container {
    display: flex; gap: 20px; overflow-x: auto; padding-bottom: 10px; -ms-overflow-style: none; scrollbar-width: none;
  }
  .timeline-container::-webkit-scrollbar { display: none; }
  .quarter-block {
    min-width: 240px; flex: 1; background: #fff; border: 1px solid #eaeaea; border-radius: 12px; padding: 20px;
  }
  .quarter-label { font-weight: 800; font-size: 1.1em; color: #1d1d1f; margin-bottom: 5px; }
  .quarter-date { font-size: 0.85em; color: #86868b; margin-bottom: 15px; font-weight: 500; }
  .tech-badges { display: flex; flex-wrap: wrap; gap: 6px; }
  .focus-badge { font-size: 0.75em; font-weight: 600; padding: 3px 8px; border-radius: 6px; background: #f5f5f7; color: #333; }
  
  /* ================= 4. Filter & Log List ================= */
  .filter-container { margin-bottom: 30px; display: flex; gap: 10px; flex-wrap: wrap; }
  .filter-btn {
    padding: 8px 16px; border-radius: 20px; border: 1px solid #eaeaea; background: #fff;
    font-size: 0.9em; font-weight: 600; color: #666; cursor: pointer; transition: all 0.2s;
  }
  .filter-btn:hover { background: #f5f5f7; color: #1d1d1f; }
  .filter-btn.active { background: #1d1d1f; color: #fff; border-color: #1d1d1f; }

  .year-header { font-size: 1.8em; font-weight: 700; margin-top: 50px; margin-bottom: 20px; border-bottom: 2px solid #1d1d1f; padding-bottom: 10px; }
  .year-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); gap: 20px; width: 100%; margin-bottom: 60px; }
  
  details.month-card { background: #ffffff; border: 1px solid #eaeaea; border-radius: 12px; overflow: hidden; }
  summary { padding: 15px 20px; cursor: pointer; font-weight: 600; background-color: #fbfbfd; display: flex; justify-content: space-between; }
  summary::after { content: '+'; color: #999; }
  details[open] summary::after { content: '−'; color: #0066cc; }
  
  .study-list { padding: 0 20px 20px 20px; border-top: 1px solid #eaeaea; }
  .study-list li {
    padding: 10px 0; border-bottom: 1px dashed #eaeaea; display: flex; gap: 12px; align-items: center; position: relative;
    transition: opacity 0.3s ease; /* 필터링 효과 */
  }
  .study-list li:last-child { border-bottom: none; }
  .study-list li.hidden { display: none; } /* 필터링 숨김 클래스 */

  .date-badge { font-family: monospace; font-weight: 600; color: #666; background: #f0f0f2; padding: 2px 6px; border-radius: 4px; font-size: 0.85em; min-width: 50px; text-align: center; }
  
  /* 링크 & 호버 프리뷰 */
  .study-link { color: #1d1d1f; text-decoration: none; position: relative; cursor: pointer; }
  .study-link:hover { color: #0066cc; text-decoration: underline; }
  
  /* 🔥 호버 프리뷰 팝업 스타일 */
  .preview-popup {
    position: fixed; pointer-events: none; z-index: 1000;
    width: 280px; background: #fff; border-radius: 8px;
    box-shadow: 0 10px 40px rgba(0,0,0,0.2); border: 1px solid #eaeaea;
    padding: 5px; opacity: 0; transform: translateY(10px); transition: opacity 0.2s, transform 0.2s;
    display: none; /* JS로 제어 */
  }
  .preview-popup img { width: 100%; border-radius: 6px; display: block; }
  .tag-dot { width: 8px; height: 8px; border-radius: 50%; display: inline-block; margin-right: 6px; }
  
  /* 태그별 색상 점 */
  .tag-shader { background-color: #9c27b0; }
  .tag-ue5 { background-color: #ff9800; }
  .tag-math { background-color: #2196f3; }
</style>

<div class="heatmap-section">
  <div class="heatmap-title">2025 Study Activity</div>
  <div class="heatmap-grid" id="heatmap-grid"></div>
</div>

<section class="featured-section">
  <div class="featured-card">
    <span class="featured-tag">Shader R&D</span>
    <div class="featured-title">Ocean Simulation with Gerstner Wave</div>
    <div class="featured-desc">파도의 물리적 움직임을 HLSL로 구현하고 최적화한 연구 기록입니다. 버텍스 오프셋 연산을 최적화하여 프레임 드랍을 15% 개선했습니다.</div>
    <a href="#" class="featured-link">Read Case Study</a>
  </div>
  <div class="featured-card">
    <span class="featured-tag">Engine Core</span>
    <div class="featured-title">UE5 Rendering Pipeline Analysis</div>
    <div class="featured-desc">언리얼 엔진 5의 나나이트(Nanite) 소스 코드를 분석하고, 커스텀 렌더 패스를 추가하여 스타일라이즈드 렌더링을 구현했습니다.</div>
    <a href="#" class="featured-link">Read Case Study</a>
  </div>
</section>

<section class="timeline-section">
  <div class="timeline-title">2025-2026 Roadmap</div>
  <div class="timeline-container">
    <div class="quarter-block" style="border-left: 4px solid #0066cc;">
      <div class="quarter-label">2025 Q4</div>
      <div class="quarter-date">Nov - Dec</div>
      <div class="tech-badges">
        <span class="focus-badge">HLSL Base</span>
        <span class="focus-badge">Linear Algebra</span>
      </div>
    </div>
    <div class="quarter-block">
      <div class="quarter-label">2026 Q1</div>
      <div class="quarter-date">Jan - Mar</div>
      <div class="tech-badges">
        <span class="focus-badge">UE5 Material</span>
        <span class="focus-badge">PBR Theory</span>
      </div>
    </div>
    <div class="quarter-block">
      <div class="quarter-label">2026 Q2</div>
      <div class="quarter-date">Apr - Jun</div>
      <div class="tech-badges">
        <span class="focus-badge">Houdini</span>
        <span class="focus-badge">Tech Art Tools</span>
      </div>
    </div>
  </div>
</section>

<div class="filter-container">
  <button class="filter-btn active" onclick="filterLogs('all')">All</button>
  <button class="filter-btn" onclick="filterLogs('shader')">Shader</button>
  <button class="filter-btn" onclick="filterLogs('ue5')">UE5 / Engine</button>
  <button class="filter-btn" onclick="filterLogs('math')">Math</button>
</div>

<h2 class="year-header">2025</h2>
<div class="year-grid">

  <details class="month-card" open>
    <summary>November</summary>
    <ul class="study-list">
      <li data-tags="ue5" data-image="https://images.unsplash.com/photo-1498050108023-c5249f4df085?q=80&w=300">
        <span class="date-badge">11.21</span>
        <span class="tag-dot tag-ue5"></span>
        <a href="/daily-study/posts/2025/11/11-21-setup/" class="study-link">블로그 개설 및 Jekyll 테마 커스텀</a>
      </li>
      
      <li data-tags="shader" data-image="/assets/images/2025/11/Pasted_image_20251128191707.png">
        <span class="date-badge">11.22</span>
        <span class="tag-dot tag-shader"></span>
        <a href="#" class="study-link">HLSL 기초 문법과 주석의 중요성</a>
      </li>
      
      <li data-tags="math" data-image="https://images.unsplash.com/photo-1635070041078-e363dbe005cb?q=80&w=300">
        <span class="date-badge">11.23</span>
        <span class="tag-dot tag-math"></span>
        <a href="#" class="study-link">선형대수학: 벡터의 내적과 렌더링 응용</a>
      </li>
    </ul>
  </details>

  <details class="month-card" open>
    <summary>December</summary>
    <ul class="study-list">
      <li data-tags="all"><span class="date-badge">Coming</span> 기록 없음</li>
    </ul>
  </details>
</div>

<h2 class="year-header">2026</h2>
<div class="year-grid">
  <details class="month-card" open><summary>January</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>February</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>March</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>April</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>May</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>June</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>July</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>August</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>September</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>October</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>November</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  <details class="month-card" open><summary>December</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
</div>

<div id="preview-popup" class="preview-popup"><img src="" id="preview-img"></div>

<script>
  // 1. 잔디 심기 (Heatmap Generator) - 예시 데이터 생성
  const heatmapGrid = document.getElementById('heatmap-grid');
  // 365개의 칸을 생성 (예시)
  for(let i=0; i<364; i++) {
    const box = document.createElement('div');
    box.className = 'day-box';
    // 랜덤하게 색칠하기 (나중엔 실제 데이터로 연동 가능)
    if(Math.random() > 0.7) {
      const levels = ['day-l1', 'day-l2', 'day-l3', 'day-l4'];
      box.classList.add(levels[Math.floor(Math.random() * 4)]);
    }
    heatmapGrid.appendChild(box);
  }

  // 2. 태그 필터링 기능
  function filterLogs(tag) {
    // 버튼 활성화 스타일 변경
    document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
    event.target.classList.add('active');

    // 리스트 필터링
    const items = document.querySelectorAll('.study-list li');
    items.forEach(item => {
      if (tag === 'all') {
        item.classList.remove('hidden');
      } else {
        const itemTags = item.getAttribute('data-tags');
        if (itemTags && itemTags.includes(tag)) {
          item.classList.remove('hidden');
        } else {
          item.classList.add('hidden');
        }
      }
    });
  }

  // 3. 링크 호버 프리뷰 기능
  const popup = document.getElementById('preview-popup');
  const previewImg = document.getElementById('preview-img');
  const links = document.querySelectorAll('.study-list li');

  links.forEach(link => {
    link.addEventListener('mouseenter', (e) => {
      const imgSrc = link.getAttribute('data-image');
      if (imgSrc) {
        previewImg.src = imgSrc;
        popup.style.display = 'block';
        setTimeout(() => { popup.style.opacity = 1; popup.style.transform = 'translateY(0)'; }, 10);
      }
    });

    link.addEventListener('mousemove', (e) => {
      // 마우스 커서 옆에 팝업 위치시키기
      popup.style.left = (e.clientX + 15) + 'px';
      popup.style.top = (e.clientY + 15) + 'px';
    });

    link.addEventListener('mouseleave', () => {
      popup.style.opacity = 0;
      popup.style.transform = 'translateY(10px)';
      setTimeout(() => { popup.style.display = 'none'; }, 200);
    });
  });
</script>
