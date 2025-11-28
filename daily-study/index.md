---
layout: page
title: Daily Study Log
permalink: /daily-study/
---

<style>
  /* ================= Global Layout & Fonts ================= */
  .markdown-body {
    max-width: 100% !important; margin: 0 !important; width: 100% !important; padding: 0 10px;
    font-family: -apple-system, BlinkMacSystemFont, "Mona Sans", "Pretendard", sans-serif;
    color: #1d1d1f;
  }
  
  /* ================= 1. Contribution Heatmap (잔디) ================= */
  .heatmap-section { margin-bottom: 30px; }
  .heatmap-title { font-size: 0.9em; font-weight: 600; color: #86868b; margin-bottom: 10px; }
  /* 2025년은 기간이 짧으므로 플렉스로 배치 */
  #heatmap-grid-2025 {
    display: flex; flex-wrap: wrap; gap: 3px; max-width: 100%; padding-bottom: 5px;
  }
  /* 2026년은 1년치이므로 그리드로 배치 */
  #heatmap-grid-2026 {
    display: grid; grid-template-columns: repeat(53, 1fr); grid-template-rows: repeat(7, 1fr);
    gap: 3px; max-width: 100%; overflow-x: auto; padding-bottom: 5px;
  }
  .day-box {
    width: 10px; height: 10px; background-color: #ebedf0; border-radius: 2px; cursor: pointer;
    transition: transform 0.1s ease-in-out;
  }
  .day-box:hover { transform: scale(1.2); border: 1px solid rgba(0,0,0,0.1); }
  
  /* 잔디 색상 레벨 */
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
    padding: 24px; transition: all 0.2s ease; position: relative; overflow: hidden;
  }
  .featured-card:hover { transform: translateY(-3px); box-shadow: 0 10px 30px rgba(0,0,0,0.08); border-color: #0066cc; }
  .featured-tag {
    font-size: 0.7em; font-weight: 700; color: #0066cc; text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 8px; display: block;
  }
  .featured-title { font-size: 1.25em; font-weight: 700; margin-bottom: 10px; line-height: 1.3; }
  .featured-desc { font-size: 0.9em; color: #666; line-height: 1.5; margin-bottom: 20px; }
  .featured-link { font-size: 0.9em; font-weight: 600; color: #1d1d1f; text-decoration: none; display: inline-flex; align-items: center; }
  .featured-link::after { content: '→'; margin-left: 5px; transition: margin-left 0.2s; }
  .featured-card:hover .featured-link::after { margin-left: 10px; }

  /* ================= 3. Tech Focus Timeline ================= */
  .timeline-section { margin-bottom: 40px; padding-bottom: 30px; border-bottom: 1px solid #eaeaea; }
  .timeline-title { font-size: 1.2em; font-weight: 700; color: #1d1d1f; margin-bottom: 20px; }
  .timeline-container {
    display: flex; gap: 20px; overflow-x: auto; padding-bottom: 10px; -ms-overflow-style: none; scrollbar-width: none;
  }
  .timeline-container::-webkit-scrollbar { display: none; }
  .quarter-block {
    min-width: 240px; flex: 1; background: #fff; border: 1px solid #eaeaea; border-radius: 12px; padding: 20px;
    transition: border-color 0.2s;
  }
  .quarter-block:hover { border-color: #d2d2d7; }
  .quarter-label { font-weight: 800; font-size: 1.1em; color: #1d1d1f; margin-bottom: 5px; }
  .quarter-date { font-size: 0.8em; color: #86868b; margin-bottom: 15px; font-weight: 500; }
  .tech-badges { display: flex; flex-wrap: wrap; gap: 6px; }
  .focus-badge { font-size: 0.75em; font-weight: 600; padding: 3px 8px; border-radius: 6px; background: #f5f5f7; color: #555; }
  
  /* ================= 4. Filter & Log List ================= */
  .filter-container { margin-bottom: 30px; display: flex; gap: 8px; flex-wrap: wrap; }
  .filter-btn {
    padding: 6px 14px; border-radius: 18px; border: 1px solid #eaeaea; background: #fff;
    font-size: 0.85em; font-weight: 600; color: #666; cursor: pointer; transition: all 0.2s;
  }
  .filter-btn:hover { background: #f5f5f7; color: #1d1d1f; border-color: #d2d2d7; }
  .filter-btn.active { background: #1d1d1f; color: #fff; border-color: #1d1d1f; }

  .year-header { font-size: 1.6em; font-weight: 700; margin-top: 50px; margin-bottom: 25px; border-bottom: 2px solid #eaeaea; padding-bottom: 12px; }
  .year-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(320px, 1fr)); gap: 25px; width: 100%; margin-bottom: 60px; }
  
  /* 월별 카드 디자인 개선 */
  details.month-card {
    background: #ffffff; border: 1px solid #eaeaea; border-radius: 14px; overflow: hidden;
    transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
  }
  details.month-card:hover { border-color: #c7c7cc; box-shadow: 0 4px 12px rgba(0,0,0,0.05); }
  
  summary {
    padding: 14px 18px; cursor: pointer; font-weight: 600; font-size: 1em;
    background-color: #fbfbfd; display: flex; justify-content: space-between; align-items: center;
    user-select: none; transition: background-color 0.2s;
  }
  summary:hover { background-color: #f5f5f7; }
  
  /* 닫혀있을 때 아이콘 */
  summary::after { content: '+'; color: #999; font-size: 1.2em; font-weight: 400; }
  /* 열려있을 때 아이콘 */
  details[open] summary::after { content: '−'; color: #0066cc; font-weight: 600; }
  
  /* 닫힌 상태일 때 시각적 표현 강화 (옵션) */
  details:not([open]) summary { color: #555; }

  
  /* 리스트 스타일 개선 (애플 스타일) */
  .study-list { padding: 5px 18px 18px 18px; border-top: 1px solid #eaeaea; }
  .study-list li {
    padding: 12px 0; border-bottom: 1px solid #f0f0f0; display: flex; gap: 10px; align-items: center; position: relative;
    transition: opacity 0.2s ease;
  }
  .study-list li:last-child { border-bottom: none; }
  .study-list li.hidden { display: none !important; } /* 필터링 숨김 클래스 */

  .date-badge {
    font-family: "SF Mono", "Menlo", monospace; font-weight: 500; color: #6e6e73;
    background: #f5f5f7; padding: 3px 7px; border-radius: 5px; font-size: 0.75em; min-width: 48px; text-align: center;
  }
  
  /* 링크 스타일 개선 */
  .study-link {
    font-size: 0.92em; color: #1d1d1f; text-decoration: none; position: relative; cursor: pointer;
    line-height: 1.4; flex-grow: 1; transition: color 0.2s;
  }
  .study-link:hover { color: #0066cc; }
  
  /* 태그별 색상 점 */
  .tag-dot { width: 6px; height: 6px; border-radius: 50%; display: inline-block; flex-shrink: 0; }
  .tag-graphics { background-color: #9c27b0; } /* 셰이더, 디자인 */
  .tag-engine { background-color: #ff9800; }   /* C++, 언리얼 */
  .tag-math { background-color: #2196f3; }     /* 수학, 절차적 생성 */
  
  /* 🔥 호버 프리뷰 팝업 스타일 (안정화) */
  .preview-popup {
    position: fixed; pointer-events: none; z-index: 1000;
    width: 300px; background: #fff; border-radius: 10px;
    box-shadow: 0 15px 40px rgba(0,0,0,0.15); border: 1px solid #eaeaea;
    padding: 6px; opacity: 0; transform: translateY(8px);
    transition: opacity 0.2s cubic-bezier(0.4, 0, 0.2, 1), transform 0.2s cubic-bezier(0.4, 0, 0.2, 1);
    visibility: hidden; /* display:none 대신 visibility 사용으로 안정성 확보 */
  }
  .preview-popup.show { opacity: 1; transform: translateY(0); visibility: visible; }
  .preview-popup img { width: 100%; border-radius: 8px; display: block; }
</style>

<div class="heatmap-section">
  <div class="heatmap-title">2025 Study Activity (From Nov 27)</div>
  <div id="heatmap-grid-2025"></div>
</div>
<div class="heatmap-section">
  <div class="heatmap-title">2026 Study Activity</div>
  <div id="heatmap-grid-2026"></div>
</div>

<section class="featured-section">
  <div class="featured-card">
    <span class="featured-tag">Shader R&D</span>
    <div class="featured-title">Ocean Simulation with Gerstner Wave</div>
    <div class="featured-desc">파도의 물리적 움직임을 HLSL로 구현하고 최적화한 연구 기록입니다. 버텍스 오프셋 연산을 최적화하여 프레임 드랍을 15% 개선했습니다.</div>
    <a href="/technical-notes/" class="featured-link">Read Case Study</a>
  </div>
  <div class="featured-card">
    <span class="featured-tag">Engine Core</span>
    <div class="featured-title">UE5 Rendering Pipeline Analysis</div>
    <div class="featured-desc">언리얼 엔진 5의 나나이트(Nanite) 소스 코드를 분석하고, 커스텀 렌더 패스를 추가하여 스타일라이즈드 렌더링을 구현했습니다.</div>
    <a href="/technical-notes/" class="featured-link">Read Case Study</a>
  </div>
</section>

<section class="timeline-section">
  <div class="timeline-title">Research Roadmap & Milestones</div>
  <div class="timeline-container">
    <div class="quarter-block" style="border-left: 3px solid #0066cc;">
      <div class="quarter-label" style="color: #0066cc;">2025 Q4</div>
      <div class="quarter-date">Nov - Dec</div>
      <div class="tech-badges">
        <span class="focus-badge">HLSL Base</span>
        <span class="focus-badge">Math (Linear Algebra)</span>
        <span class="focus-badge">Jekyll Setup</span>
      </div>
    </div>
    <div class="quarter-block">
      <div class="quarter-label">2026 Q1</div>
      <div class="quarter-date">Jan - Mar</div>
      <div class="tech-badges">
        <span class="focus-badge">UE5 Material Graph</span>
        <span class="focus-badge">PBR Theory</span>
        <span class="focus-badge">C++ Core</span>
      </div>
    </div>
    <div class="quarter-block">
      <div class="quarter-label">2026 Q2</div>
      <div class="quarter-date">Apr - Jun</div>
      <div class="tech-badges">
        <span class="focus-badge">Houdini Proc. Gen</span>
        <span class="focus-badge">Optimization</span>
      </div>
    </div>
  </div>
</section>

<div class="filter-container">
  <button class="filter-btn active" onclick="filterLogs('all')">All</button>
  <button class="filter-btn" onclick="filterLogs('graphics')">Graphics & Shader</button>
  <button class="filter-btn" onclick="filterLogs('engine')">Engine & Core</button>
  <button class="filter-btn" onclick="filterLogs('math')">Math & Proc. Gen</button>
</div>

<h2 class="year-header">2025</h2>
<div class="year-grid">
  
  <details class="month-card" open>
    <summary>November</summary>
    <ul class="study-list">
      <li data-tags="engine" data-image="https://images.unsplash.com/photo-1498050108023-c5249f4df085?q=80&w=300">
        <span class="date-badge">11.21</span>
        <span class="tag-dot tag-engine"></span>
        <a href="/daily-study/posts/2025/11/11-21-setup/" class="study-link">블로그 개설 및 Jekyll 테마 커스텀 (Design System)</a>
      </li>
      
      <li data-tags="graphics" data-image="/assets/images/2025/11/Pasted_image_20251128191707.png">
        <span class="date-badge">11.22</span>
        <span class="tag-dot tag-graphics"></span>
        <a href="#" class="study-link">HLSL 기초 문법과 주석의 중요성 (ShaderLab)</a>
      </li>
      
      <li data-tags="math" data-image="https://images.unsplash.com/photo-1635070041078-e363dbe005cb?q=80&w=300">
        <span class="date-badge">11.23</span>
        <span class="tag-dot tag-math"></span>
        <a href="#" class="study-link">선형대수학: 벡터의 내적과 렌더링 응용</a>
      </li>
    </ul>
  </details>

  <details class="month-card">
    <summary>December</summary>
    <ul class="study-list">
      <li data-tags="all"><span class="date-badge">Coming</span> 기록 없음</li>
    </ul>
  </details>
</div>

<h2 class="year-header">2026</h2>
<div class="year-grid">
  <details class="month-card" open><summary>January</summary><ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul></details>
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

<div id="preview-popup" class="preview-popup"><img src="" id="preview-img"></div>

<script>
  // 1. 잔디 심기 (Heatmap) - 2025년 & 2026년
  function generateHeatmap(elementId, startDateStr, endDateStr, activeDates = []) {
    const grid = document.getElementById(elementId);
    const startDate = new Date(startDateStr);
    const endDate = new Date(endDateStr);
    
    for (let d = new Date(startDate); d <= endDate; d.setDate(d.getDate() + 1)) {
      const box = document.createElement('div');
      box.className = 'day-box';
      
      // 날짜 문자열 생성 (YYYY-MM-DD)
      const dateStr = d.toISOString().split('T')[0];
      box.setAttribute('title', dateStr); // 마우스 오버 시 날짜 표시
      
      // 활동 기록이 있는 날짜인지 확인
      if (activeDates.includes(dateStr)) {
        // 랜덤 색상 부여 (나중엔 실제 데이터 연동)
        const levels = ['day-l1', 'day-l2', 'day-l3', 'day-l4'];
        box.classList.add(levels[Math.floor(Math.random() * 4)]);
      }
      grid.appendChild(box);
    }
  }

  // 2025년 잔디 생성 (11/27 ~ 12/31, 27일과 28일 활성화)
  generateHeatmap('heatmap-grid-2025', '2025-11-27', '2025-12-31', ['2025-11-27', '2025-11-28']);
  
  // 2026년 잔디 생성 (1/1 ~ 12/31, 예시 데이터 몇 개 넣음)
  generateHeatmap('heatmap-grid-2026', '2026-01-01', '2026-12-31', ['2026-01-05', '2026-02-14', '2026-03-01']);


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

  // 3. 호버 프리뷰 (안정화 버전)
  const popup = document.getElementById('preview-popup');
  const previewImg = document.getElementById('preview-img');
  const links = document.querySelectorAll('.study-list li');
  let hideTimeout;

  links.forEach(link => {
    link.addEventListener('mouseenter', (e) => {
      const imgSrc = link.getAttribute('data-image');
      if (!imgSrc) return;

      clearTimeout(hideTimeout); // 숨김 타이머 취소
      previewImg.src = imgSrc;
      popup.classList.add('show'); // 표시 클래스 추가
      
      // 팝업 위치 초기화 (마우스 근처로)
      popup.style.left = (e.clientX + 20) + 'px';
      popup.style.top = (e.clientY + 20) + 'px';
    });

    link.addEventListener('mousemove', (e) => {
      if (!popup.classList.contains('show')) return;
      // 마우스 따라다니기
      popup.style.left = (e.clientX + 20) + 'px';
      popup.style.top = (e.clientY + 20) + 'px';
    });

    link.addEventListener('mouseleave', () => {
      // 잠시 후 숨김 처리 (부드러운 트랜지션 위해)
      hideTimeout = setTimeout(() => {
        popup.classList.remove('show');
      }, 100);
    });
  });
</script>
