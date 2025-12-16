---
layout: default
title: Today I Learned
permalink: /daily-study/
---

<style>
  /* [수정됨] 페이지 전체 래퍼: 사이드바 옆에 내용이 오도록 함 */ 
  /* 중요: margin-left를 주지 않고 padding만 줍니다. (default 레이아웃이 알아서 처리함) */
  .page-content-wrapper {
    padding: 60px 40px 100px 40px; 
    max-width: 1200px;
    margin: 0 auto;
    box-sizing: border-box;
  }

  /* [수정됨] 충돌 방지를 위해 width: 100% 제거 */
  .markdown-body {
    box-sizing: border-box;
    font-family: "Pretendard", -apple-system, BlinkMacSystemFont, sans-serif;
    color: #1d1d1f;
  }
  
  /* ================= 1. Heatmap (잔디) ================= */
  .heatmap-section { margin-bottom: 40px; }
  .heatmap-title { font-size: 0.9em; font-weight: 600; color: #86868b; margin-bottom: 15px; }
  
  #heatmap-grid-2025 { display: flex; flex-wrap: wrap; gap: 4px; padding-bottom: 5px; }
  #heatmap-grid-2026 { display: grid; grid-template-columns: repeat(53, 1fr); grid-template-rows: repeat(7, 1fr); gap: 4px; overflow-x: auto; padding-bottom: 5px; }
  
  .day-box {
    width: 11px; height: 11px; background-color: #ebedf0; border-radius: 2px; cursor: pointer;
    transition: transform 0.1s;
  }
  .day-box:hover { transform: scale(1.3); border: 1px solid rgba(0,0,0,0.2); }
  
  .day-l1 { background-color: #9be9a8; }
  .day-l2 { background-color: #40c463; }
  .day-l3 { background-color: #30a14e; }
  .day-l4 { background-color: #216e39; }

  /* ================= 2. Featured Research ================= */
  .featured-section {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
    gap: 24px; margin-bottom: 60px;
  }
  .featured-card {
    background: #fff; border: 1px solid #eaeaea; border-radius: 16px;
    padding: 30px; transition: all 0.2s ease; position: relative; overflow: hidden;
    box-shadow: 0 4px 12px rgba(0,0,0,0.02);
  }
  .featured-card:hover { transform: translateY(-3px); box-shadow: 0 12px 30px rgba(0,0,0,0.08); }
  
  .featured-tag {
    font-size: 0.75em; font-weight: 700; color: #1d1d1f; opacity: 0.6; text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 12px; display: block;
  }
  .featured-title { font-size: 1.4em; font-weight: 700; margin-bottom: 10px; line-height: 1.2; color: #1d1d1f; }
  .featured-desc { font-size: 1em; color: #424245; line-height: 1.5; margin-bottom: 24px; }
  .featured-link { font-size: 0.95em; font-weight: 600; color: #1d1d1f; text-decoration: none; display: inline-flex; align-items: center; }
  .featured-link::after { content: '→'; margin-left: 6px; transition: margin-left 0.2s; }
  .featured-card:hover .featured-link::after { margin-left: 10px; }

  /* ================= 3. Tech Timeline ================= */
  .timeline-section { margin-bottom: 60px; padding-bottom: 40px; border-bottom: 1px solid #eaeaea; }
  .timeline-title { font-size: 1.3em; font-weight: 700; color: #1d1d1f; margin-bottom: 25px; }
  
  .timeline-container {
    display: flex; gap: 20px; overflow-x: auto; padding-bottom: 10px; 
    -ms-overflow-style: none; scrollbar-width: none;
  }
  .timeline-container::-webkit-scrollbar { display: none; }
  
  .quarter-block {
    min-width: 260px; flex: 1; background: #fff; border: 1px solid #eaeaea; border-radius: 14px; padding: 24px;
    transition: border-color 0.2s;
  }
  .quarter-block:hover { border-color: #d2d2d7; }
  
  .quarter-label { font-weight: 800; font-size: 1.1em; color: #1d1d1f; margin-bottom: 6px; }
  .quarter-date { font-size: 0.85em; color: #86868b; margin-bottom: 16px; font-weight: 500; }
  
  .tech-badges { display: flex; flex-wrap: wrap; gap: 6px; }
  .focus-badge { font-size: 0.75em; font-weight: 600; padding: 4px 10px; border-radius: 6px; background: #f5f5f7; color: #1d1d1f; border: 1px solid #e5e5e5; }
  
  /* ================= 4. Filter Buttons ================= */
  .filter-container { margin-bottom: 40px; display: flex; gap: 10px; flex-wrap: wrap; }
  .filter-btn {
    padding: 8px 16px; border-radius: 20px; border: 1px solid #eaeaea; background: #fff;
    font-size: 0.9em; font-weight: 500; color: #666; cursor: pointer; transition: all 0.2s;
  }
  .filter-btn:hover { background: #f5f5f7; color: #1d1d1f; }
  .filter-btn.active { background: #1d1d1f; color: #fff; border-color: #1d1d1f; font-weight: 600; }

  /* ================= 5. Daily Logs Layout ================= */
  .year-header { font-size: 1.8em; font-weight: 700; margin-top: 60px; margin-bottom: 30px; border-bottom: 2px solid #eaeaea; padding-bottom: 15px; }
  
  .year-grid { 
    display: grid; 
    grid-template-columns: repeat(auto-fill, minmax(340px, 1fr)); 
    gap: 24px; 
    width: 100%; 
    margin-bottom: 80px;
    align-items: start;
  }
  
  details.month-card {
    background: #ffffff; border: 1px solid #eaeaea; border-radius: 16px; overflow: hidden;
    transition: all 0.2s ease;
  }
  details.month-card:hover { border-color: #c7c7cc; box-shadow: 0 4px 16px rgba(0,0,0,0.06); }
  
  summary {
    padding: 16px 20px; cursor: pointer; font-weight: 600; font-size: 1.05em;
    background-color: #fbfbfd; display: flex; justify-content: space-between; align-items: center;
    user-select: none; transition: background-color 0.2s;
  }
  summary:hover { background-color: #f5f5f7; }
  summary::after { content: '+'; color: #999; font-size: 1.2em; font-weight: 400; }
  details[open] summary::after { content: '−'; color: #1d1d1f; font-weight: 600; }
  
  .study-list { padding: 5px 20px 20px 20px; border-top: 1px solid #eaeaea; }
  .study-list li {
    padding: 14px 0; border-bottom: 1px solid #f0f0f0; display: flex; gap: 14px; align-items: center; position: relative;
    transition: opacity 0.2s ease;
  }
  .study-list li:last-child { border-bottom: none; }
  .study-list li.hidden { display: none !important; }

  .date-badge {
    font-family: "Pretendard", -apple-system, sans-serif; 
    font-weight: 600; color: #1d1d1f;
    background: #f2f2f7; 
    padding: 4px 8px; border-radius: 6px; 
    font-size: 0.85em; min-width: 48px; text-align: center;
    letter-spacing: -0.02em;
  }
  
  .study-link {
    font-size: 0.95em; color: #1d1d1f; text-decoration: none; position: relative; cursor: pointer;
    line-height: 1.4; flex-grow: 1; transition: color 0.2s;
  }
  .study-link:hover { color: #0071e3; }
  
  .tag-dot { width: 6px; height: 6px; border-radius: 50%; display: inline-block; flex-shrink: 0; }
  
  /* 호버 프리뷰 */
  .preview-popup {
    position: fixed; pointer-events: none; z-index: 1000;
    width: 320px; background: #fff; border-radius: 12px;
    box-shadow: 0 20px 50px rgba(0,0,0,0.15); border: 1px solid #eaeaea;
    padding: 8px; opacity: 0; transform: translateY(10px);
    transition: opacity 0.2s, transform 0.2s;
    visibility: hidden;
  }
  .preview-popup.show { opacity: 1; transform: translateY(0); visibility: visible; }
  .preview-popup img { width: 100%; border-radius: 8px; display: block; }
</style>

<div class="page-content-wrapper">

 <header style="margin-bottom: 50px;">
    <h1 style="font-size: 2.8em; font-weight: 700; margin-bottom: 10px; letter-spacing: -0.02em;">Today I Learned</h1>
    <p style="color: #86868b; font-size: 1.1em;">매일의 성장과 연구 기록</p>
  </header>

  <div class="heatmap-section">
    <div class="heatmap-title">2025 Activity (Since Dec 09)</div>
    <div id="heatmap-grid-2025"></div>
  </div>
  <div class="heatmap-section">
    <div class="heatmap-title">2026 Activity</div>
    <div id="heatmap-grid-2026"></div>
  </div>

  <section class="timeline-section">
    <div class="timeline-title">Research Roadmap & Milestones</div>
    <div class="timeline-container">
      <div class="quarter-block" style="border-left: 3px solid #0066cc;">
        <div class="quarter-label" style="color: #0066cc;">2025 Q4</div>
        <div class="quarter-date">Nov - Dec</div>
        <div class="tech-badges">
          <span class="focus-badge">C++</span>
          <span class="focus-badge">Basic CS</span>
          <span class="focus-badge">Algorithms & DS</span>
        </div>
      </div>
      <div class="quarter-block">
        <div class="quarter-label">2026 Q1</div>
        <div class="quarter-date">Jan - Mar</div>
        <div class="tech-badges">
          <span class="focus-badge">UE5 Material Graph</span>
          <span class="focus-badge">PBR Theory</span>
          <span class="focus-badge">Computer Graphics</span>
        </div>
      </div>
      <div class="quarter-block">
        <div class="quarter-label">2026 Q2</div>
        <div class="quarter-date">Apr - Jun</div>
        <div class="tech-badges">
          <span class="focus-badge">Houdini Proc. Gen</span>
          <span class="focus-badge">Substance Designer</span>
        </div>
      </div>
    </div>
  </section>

  <div class="filter-container">
    <button class="filter-btn active" onclick="filterLogs('all')">All</button>
    <button class="filter-btn" onclick="filterLogs('graphics')">Graphics Theory</button>
    <button class="filter-btn" onclick="filterLogs('shader')">Shader Implementation</button>
    <button class="filter-btn" onclick="filterLogs('engine')">C++ & Engine Core</button>
    <button class="filter-btn" onclick="filterLogs('tools')">TA Tools & Pipeline</button>
  </div>

  <h2 class="year-header">2025</h2>
  <div class="year-grid">


<details class="month-card" open>
<summary>December</summary>
<ul class="study-list">
  
<li data-tags="tools">
<span class="date-badge">12.09</span>
<span class="tag-dot" style="background:#2e7d32;"></span>
<a href="https://github.com/KimDongGun324/kimdonggun324.github.io/blob/main/daily-study/posts/2025/12/09.md" class="study-link" target="_blank">
C++ - Stack Memory and Literal Optimization Study
</a>
</li>

<li data-tags="tools">
<span class="date-badge">12.10</span>
<span class="tag-dot" style="background:#2e7d32;"></span>
<a href="https://github.com/KimDongGun324/kimdonggun324.github.io/blob/main/daily-study/posts/2025/12/10.md" class="study-link" target="_blank">
Building a Researcher's Pipeline: Reflections on the First Semester
</a>
</li>

<li data-tags="tools">
<span class="date-badge">12.11</span>
<span class="tag-dot" style="background:#2e7d32;"></span>
<a href="https://github.com/KimDongGun324/kimdonggun324.github.io/blob/main/daily-study/posts/2025/12/11.md" class="study-link" target="_blank">
A Farewell and A New Resolve
</a>
</li>

<li data-tags="tools">
<span class="date-badge">12.12</span>
<span class="tag-dot" style="background:#2e7d32;"></span>
<a href="https://github.com/KimDongGun324/kimdonggun324.github.io/blob/main/daily-study/posts/2025/12/12.md" class="study-link" target="_blank">
Daily Log 2025_12_12
</a>
</li>

<li data-tags="tools">
<span class="date-badge">12.13</span>
<span class="tag-dot" style="background:#2e7d32;"></span>
<a href="https://github.com/KimDongGun324/kimdonggun324.github.io/blob/main/daily-study/posts/2025/12/13.md" class="study-link" target="_blank">
Daily Log 2025_12_13
</a>
</li>

<li data-tags="tools">
<span class="date-badge">12.14</span>
<span class="tag-dot" style="background:#2e7d32;"></span>
<a href="https://github.com/KimDongGun324/kimdonggun324.github.io/blob/main/daily-study/posts/2025/12/14.md" class="study-link" target="_blank">
Daily Log 2025_12_14
</a>
</li>

<li data-tags="tools">
<span class="date-badge">12.15</span>
<span class="tag-dot" style="background:#2e7d32;"></span>
<a href="https://github.com/KimDongGun324/kimdonggun324.github.io/blob/main/daily-study/posts/2025/12/15.md" class="study-link" target="_blank">
Daily Log 2025_12_15
</a>
</li>

<li data-tags="tools">
<span class="date-badge">12.16</span>
<span class="tag-dot" style="background:#2e7d32;"></span>
<a href="https://github.com/KimDongGun324/kimdonggun324.github.io/blob/main/daily-study/posts/2025/12/16.md" class="study-link" target="_blank">
Daily Log 2025_12_16
</a>
</li>


  
</ul>
</details>
  </div>



  <h2 class="year-header">2026</h2>
  <div class="year-grid">
    <details class="month-card"><summary>January</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>February</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>March</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>April</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>May</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>June</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>July</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>August</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>September</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>October</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>November</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
    <details class="month-card"><summary>December</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
  </div>

</div>
<div id="preview-popup" class="preview-popup"><img src="" id="preview-img"></div>

<script>
  // 1. 잔디 심기 (Heatmap)
  function generateHeatmap(elementId, startDateStr, endDateStr, studyData = {}) {
    const grid = document.getElementById(elementId);
    const startDate = new Date(startDateStr);
    const endDate = new Date(endDateStr);
    
    for (let d = new Date(startDate); d <= endDate; d.setDate(d.getDate() + 1)) {
      const box = document.createElement('div');
      box.className = 'day-box';
      const dateStr = d.toISOString().split('T')[0];
      box.setAttribute('title', dateStr);
      
      const level = studyData[dateStr]; 
      if (level) {
        box.classList.add('day-l' + level);
        box.setAttribute('title', `${dateStr} (Lv.${level})`);
      }
      
      grid.appendChild(box);
    }
  }

  // 데이터
  const data2025 = {
    '2025-12-09': 3,
    '2025-12-10': 1,
    '2025-12-11': 1,
    '2025-12-12': 1,
    '2025-12-13': 1,
    '2025-12-14': 1,
    '2025-12-15': 1,
    '2025-12-16': 1,
    
  };
  const data2026 = {};

  generateHeatmap('heatmap-grid-2025', '2025-12-09', '2025-12-31', data2025);
  generateHeatmap('heatmap-grid-2026', '2026-01-01', '2026-12-31', data2026);


  // 2. 태그 필터링
  function filterLogs(tag) {
    document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
    event.target.classList.add('active');

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

  // 3. 호버 프리뷰
  const popup = document.getElementById('preview-popup');
  const previewImg = document.getElementById('preview-img');
  const links = document.querySelectorAll('.study-list li');
  let hideTimeout;

  links.forEach(link => {
    link.addEventListener('mouseenter', (e) => {
      const imgSrc = link.getAttribute('data-image');
      if (!imgSrc) return;
      clearTimeout(hideTimeout);
      previewImg.src = imgSrc;
      popup.classList.add('show');
      
      const x = e.clientX + 20;
      const y = e.clientY + 20;
      popup.style.left = x + 'px';
      popup.style.top = y + 'px';
    });

    link.addEventListener('mousemove', (e) => {
      if (!popup.classList.contains('show')) return;
      popup.style.left = (e.clientX + 20) + 'px';
      popup.style.top = (e.clientY + 20) + 'px';
    });

    link.addEventListener('mouseleave', () => {
      hideTimeout = setTimeout(() => { popup.classList.remove('show'); }, 100);
    });
  });
</script>
