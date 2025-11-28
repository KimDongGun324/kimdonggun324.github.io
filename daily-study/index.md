---
layout: page
title: Daily Study Log
permalink: /daily-study/
---

<style>
  /* 연도 제목 스타일 */
  .year-header {
    font-size: 1.8em; font-weight: 700; color: #1d1d1f;
    margin-top: 60px; margin-bottom: 20px;
    border-bottom: 2px solid #1d1d1f; padding-bottom: 10px;
    letter-spacing: -0.02em;
  }

  /* 월별 토글 카드 스타일 */
  details.month-card {
    background: #ffffff; border: 1px solid #eaeaea; border-radius: 12px;
    margin-bottom: 15px; transition: all 0.2s ease;
    overflow: hidden; /* 내부 리스트가 둥근 모서리를 넘지 않게 */
  }
  details.month-card:hover {
    border-color: #d2d2d7; box-shadow: 0 4px 12px rgba(0,0,0,0.08);
  }
  
  /* 토글 버튼 (요약) */
  summary {
    padding: 20px; cursor: pointer; font-weight: 600; font-size: 1.1em;
    color: #1d1d1f; list-style: none; /* 기본 화살표 제거 */
    display: flex; justify-content: space-between; align-items: center;
  }
  /* 커스텀 화살표 아이콘 */
  summary::after {
    content: '+'; font-size: 1.2em; color: #86868b; transition: transform 0.2s;
  }
  details[open] summary::after {
    content: '−'; color: #0066cc; /* 열렸을 때 색상 변경 */
  }
  
  /* 내부 공부 리스트 */
  .study-list {
    padding: 0 20px 20px 20px; margin: 0; border-top: 1px solid #f5f5f7;
  }
  .study-list li {
    padding: 12px 0; border-bottom: 1px dashed #eaeaea;
    font-size: 0.95em; color: #424245; display: flex; gap: 15px;
  }
  .study-list li:last-child { border-bottom: none; }
  
  .date-badge {
    font-family: monospace; font-weight: 600; color: #86868b;
    background: #f5f5f7; padding: 2px 6px; border-radius: 4px;
    font-size: 0.85em; min-width: 60px; text-align: center;
  }
  .study-link { color: #1d1d1f; text-decoration: none; transition: color 0.2s; }
  .study-link:hover { color: #0066cc; text-decoration: underline; }
</style>

<h2 class="year-header">2025</h2>

<details class="month-card" open>
  <summary>November <span style="font-size:0.8em; color:#999; font-weight:400;">Shaders & Math Base</span></summary>
  <ul class="study-list">
    <li>
      <span class="date-badge">11.21</span>
      <a href="#" class="study-link">블로그 개설 및 Jekyll 테마 커스텀 (Design System)</a>
    </li>
    <li>
      <span class="date-badge">11.22</span>
      <a href="#" class="study-link">HLSL 기초 문법과 렌더링 파이프라인 복습</a>
    </li>
    <li>
      <span class="date-badge">11.23</span>
      <a href="#" class="study-link">선형대수학: 벡터의 내적과 외적의 그래픽스적 의미</a>
    </li>
  </ul>
</details>

<details class="month-card">
  <summary>December</summary>
  <ul class="study-list">
    <li><span class="date-badge">Coming</span> 아직 기록이 없습니다.</li>
  </ul>
</details>


<h2 class="year-header">2026</h2>

<details class="month-card">
  <summary>January</summary>
  <ul class="study-list">
    <li><span class="date-badge">Coming</span> 2026년 1월 공부 계획</li>
  </ul>
</details>

<details class="month-card">
  <summary>February</summary>
  <ul class="study-list">
    <li><span class="date-badge">Coming</span> </li>
  </ul>
</details>
