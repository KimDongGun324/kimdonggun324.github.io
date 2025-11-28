---
layout: page
title: Daily Study Log
permalink: /daily-study/
---

<style>
  /* ⚡ [문제 해결] 이 페이지에서만 폭 제한을 풀고 왼쪽 정렬로 변경 */
  .markdown-body {
    max-width: 100% !important; /* 폭 제한 해제 */
    margin: 0 !important;       /* 가운데 정렬 해제 (왼쪽 붙임) */
    width: 100% !important;     /* 전체 너비 사용 */
    padding: 0 10px;            /* 양옆 살짝 여백 */
  }

  /* 연도 제목 스타일 */
  .year-header {
    font-size: 1.8em; font-weight: 700; color: #1d1d1f;
    margin-top: 60px; margin-bottom: 20px;
    border-bottom: 2px solid #1d1d1f; padding-bottom: 10px;
    letter-spacing: -0.02em;
  }

  /* 🔥 그리드 시스템: 화면 크기에 따라 카드 자동 배치 */
  .year-grid {
    display: grid;
    /* 최소 300px 크기의 카드를 화면에 꽉 차게 채움 */
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px; 
    margin-bottom: 60px;
    width: 100%; 
  }

  /* 월별 토글 카드 */
  details.month-card {
    background: #ffffff; border: 1px solid #eaeaea; border-radius: 12px;
    transition: all 0.2s ease;
    overflow: hidden; 
    height: fit-content;
  }
  details.month-card:hover {
    border-color: #d2d2d7; box-shadow: 0 4px 12px rgba(0,0,0,0.08);
  }
  
  /* 토글 헤더 */
  summary {
    padding: 15px 20px; cursor: pointer; font-weight: 600; font-size: 1.05em;
    color: #1d1d1f; list-style: none; 
    display: flex; justify-content: space-between; align-items: center;
    background-color: #fbfbfd;
  }
  summary::after {
    content: '+'; font-size: 1.2em; color: #86868b; transition: transform 0.2s;
  }
  /* 열렸을 때 아이콘 변경 */
  details[open] summary::after {
    content: '−'; color: #0066cc;
  }
  
  /* 내부 리스트 */
  .study-list {
    padding: 0 20px 20px 20px; margin: 0; border-top: 1px solid #eaeaea;
    background-color: #fff;
  }
  .study-list li {
    padding: 12px 0; border-bottom: 1px dashed #eaeaea;
    font-size: 0.9em; color: #424245; display: flex; gap: 12px; align-items: baseline;
  }
  .study-list li:last-child { border-bottom: none; }
  
  .date-badge {
    font-family: monospace; font-weight: 600; color: #555;
    background: #f0f0f2; padding: 2px 8px; border-radius: 4px;
    font-size: 0.85em; white-space: nowrap;
  }
  
  .study-link { 
    color: #1d1d1f; text-decoration: none; 
    line-height: 1.4; display: block;
  }
  .study-link:hover { color: #0066cc; text-decoration: underline; }
</style>

<h2 class="year-header">2025</h2>

<div class="year-grid">
  
  <details class="month-card">
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

  <details class="month-card">
    <summary>December</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> 기록 없음</li>
    </ul>
  </details>

</div>


<h2 class="year-header">2026</h2>

<div class="year-grid">
  
  <details class="month-card">
    <summary>January</summary>
    <ul class="study-list">
      <li><span class="date-badge">01.01</span> 새해 목표 수립</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>February</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>March</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>April</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>May</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>June</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>July</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>August</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>September</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>October</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>November</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

  <details class="month-card">
    <summary>December</summary>
    <ul class="study-list">
      <li><span class="date-badge">Coming</span> ...</li>
    </ul>
  </details>

</div>
