---
layout: page
title: Daily Study Log
permalink: /daily-study/
---

<style>
  /* 페이지 레이아웃 설정 (왼쪽 정렬, 폭 제한 해제) */
  .markdown-body {
    max-width: 100% !important; margin: 0 !important; width: 100% !important; padding: 0 10px;
  }

  /* ================= Timeline Section Styles ================= */
  .timeline-section {
    margin-bottom: 60px; padding-bottom: 30px; border-bottom: 1px solid #eaeaea;
  }
  .timeline-title { font-size: 1.2em; font-weight: 700; color: #1d1d1f; margin-bottom: 20px; }
  
  /* 가로 스크롤 가능한 타임라인 컨테이너 */
  .timeline-container {
    display: flex; gap: 20px; overflow-x: auto; padding-bottom: 15px;
    /* 스크롤바 숨기기 (크롬 등) */
    -ms-overflow-style: none; scrollbar-width: none;
  }
  .timeline-container::-webkit-scrollbar { display: none; }

  /* 분기별 블록 */
  .quarter-block {
    min-width: 240px; flex: 1;
    background: #fbfbfd; border: 1px solid #eaeaea; border-radius: 12px;
    padding: 20px; display: flex; flex-direction: column;
  }
  .quarter-label {
    font-weight: 800; font-size: 1.1em; color: #1d1d1f; margin-bottom: 5px;
  }
  .quarter-date {
    font-size: 0.85em; color: #86868b; margin-bottom: 15px; font-weight: 500;
  }
  
  /* 기술 스택 뱃지 컨테이너 */
  .tech-badges { display: flex; flex-wrap: wrap; gap: 8px; }
  
  /* 각 기술 뱃지 디자인 */
  .focus-badge {
    font-size: 0.8em; font-weight: 600; padding: 4px 10px; border-radius: 20px;
    white-space: nowrap;
  }
  /* 주제별 색상 (원하는 대로 커스텀 가능) */
  .bg-shader { background: #e3f2fd; color: #0066cc; } /* 셰이더, 그래픽스 */
  .bg-math { background: #f3e5f5; color: #7b1fa2; }   /* 수학 */
  .bg-engine { background: #fff3e0; color: #e65100; } /* 언리얼, C++ */
  .bg-art { background: #e8f5e9; color: #2e7d32; }    /* 후디니, 아트 툴 */


  /* ================= Existing Log Styles ================= */
  .year-header {
    font-size: 1.8em; font-weight: 700; color: #1d1d1f;
    margin-top: 40px; margin-bottom: 20px;
    border-bottom: 2px solid #1d1d1f; padding-bottom: 10px; letter-spacing: -0.02em;
  }
  .year-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px; margin-bottom: 60px; width: 100%; 
  }
  details.month-card {
    background: #ffffff; border: 1px solid #eaeaea; border-radius: 12px;
    transition: all 0.2s ease; overflow: hidden; height: fit-content;
  }
  details.month-card:hover { border-color: #d2d2d7; box-shadow: 0 4px 12px rgba(0,0,0,0.08); }
  summary {
    padding: 15px 20px; cursor: pointer; font-weight: 600; font-size: 1.05em;
    color: #1d1d1f; list-style: none; display: flex; justify-content: space-between; align-items: center;
    background-color: #fbfbfd;
  }
  summary::after { content: '+'; font-size: 1.2em; color: #86868b; transition: transform 0.2s; }
  details[open] summary::after { content: '−'; color: #0066cc; }
  .study-list { padding: 0 20px 20px 20px; margin: 0; border-top: 1px solid #eaeaea; background-color: #fff; }
  .study-list li {
    padding: 12px 0; border-bottom: 1px dashed #eaeaea; font-size: 0.9em; color: #424245; display: flex; gap: 12px; align-items: baseline;
  }
  .study-list li:last-child { border-bottom: none; }
  .date-badge {
    font-family: monospace; font-weight: 600; color: #555; background: #f0f0f2; padding: 2px 8px; border-radius: 4px; font-size: 0.85em; white-space: nowrap;
  }
  .study-link { color: #1d1d1f; text-decoration: none; line-height: 1.4; display: block; }
  .study-link:hover { color: #0066cc; text-decoration: underline; }
</style>


<section class="timeline-section">
  <div class="timeline-title">Research Roadmap & Milestones</div>
  
  <div class="timeline-container">
    
    <div class="quarter-block" style="border-color: #0066cc; background: #f4faff;">
      <div class="quarter-label" style="color: #0066cc;">2025 Q4</div>
      <div class="quarter-date">Nov - Dec</div>
      <div class="tech-badges">
        <span class="focus-badge bg-shader">HLSL Base</span>
        <span class="focus-badge bg-math">Linear Algebra</span>
        <span class="focus-badge bg-engine">Jekyll Setup</span>
      </div>
    </div>

    <div class="quarter-block">
      <div class="quarter-label">2026 Q1</div>
      <div class="quarter-date">Jan - Mar</div>
      <div class="tech-badges">
        <span class="focus-badge bg-engine">UE5 Material Graph</span>
        <span class="focus-badge bg-shader">PBR Theory</span>
      </div>
    </div>

    <div class="quarter-block">
      <div class="quarter-label">2026 Q2</div>
      <div class="quarter-date">Apr - Jun</div>
      <div class="tech-badges">
        <span class="focus-badge bg-art">Houdini Proc. Gen</span>
        <span class="focus-badge bg-engine">Optimization</span>
      </div>
    </div>
    
    </div>
</section>


<h2 class="year-header">2025</h2>

<div class="year-grid">
  <details class="month-card" open>
    <summary>November</summary>
    <ul class="study-list">
      <li>
        <span class="date-badge">11.21</span>
        <a href="/daily-study/posts/2025/11/11-21-setup/" class="study-link">
          블로그 개설 및 Jekyll 테마 커스텀
        </a>
      </li>
      <li>
        <span class="date-badge">11.22</span>
        <a href="#" class="study-link">HLSL 기초 문법과 렌더링 파이프라인</a>
      </li>
      <li>
        <span class="date-badge">11.23</span>
        <a href="#" class="study-link">선형대수학: 벡터의 내적과 외적</a>
      </li>
    </ul>
  </details>

  <details class="month-card" open>
    <summary>December</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> 기록 없음</li>
    </ul>
  </details>
</div>


<h2 class="year-header">2026</h2>
<div class="year-grid">
  <details class="month-card" open>
    <summary>January</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>February</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>March</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>April</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>May</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>June</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>July</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>August</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>September</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>October</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>November</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
  <details class="month-card" open>
    <summary>December</summary>
    <ul class="study-list"><li><span class="date-badge">Coming</span>...</li></ul>
  </details>
</div>
