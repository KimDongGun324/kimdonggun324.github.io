---
layout: page
title: Technical Notes
permalink: /technical-notes/
---

<style>
  /* ================= Global Layout & Reset ================= */
  body, .markdown-body {
    background-color: #ffffff !important; 
    font-family: -apple-system, BlinkMacSystemFont, "Pretendard", "Apple SD Gothic Neo", sans-serif;
    color: #1d1d1f;
  }
  
  /* ================= Main Content Container (왼쪽 정렬 강제) ================= */
  .page-container {
    /* Daily Study Log와 동일하게, 중앙 정렬 제거 및 왼쪽 정렬 강제 */
    max-width: 100%; 
    margin: 40px 0; 
    padding: 0 50px; 
    text-align: left; 
  }

  /* 페이지 설명 (수직 정렬 Fix) */
  .page-intro {
    font-size: 1.2em; font-weight: 400; color: #424245; line-height: 1.6;
    margin: 0 0 15px 0; /* H2 제목 바로 아래에 붙도록 마진 조정 */
    word-break: keep-all; 
    max-width: 800px;
  }
  .highlight-text { color: #1d1d1f; font-weight: 600; }

  /* ================= Filter Buttons (왼쪽 정렬) ================= */
  .filter-container { 
    margin-bottom: 30px; 
    display: flex; 
    gap: 10px; 
    flex-wrap: wrap; 
    justify-content: flex-start; /* 왼쪽 정렬 강제 */
  }
  .filter-btn {
    padding: 6px 14px; 
    border-radius: 18px; 
    border: 1px solid #d2d2d7;
    background: #ffffff; 
    font-size: 0.85em; 
    font-weight: 600; 
    color: #666; 
    cursor: pointer; 
    transition: all 0.2s ease;
  }
  .filter-btn:hover { background: #f5f5f7; color: #1d1d1f; border-color: #86868b; }
  .filter-btn.active { background: #1d1d1f; color: #fff; border-color: #1d1d1f; }

  /* ================= Content Grid (2열 안정화 - Daily Log Featured Style) ================= */
  .notes-content-grid {
    display: grid;
    /* Daily Log의 Featured Research처럼 2열을 기본으로 설정하여 안정성 확보 */
    grid-template-columns: 1fr 1fr; 
    gap: 30px; 
    margin-bottom: 60px;
  }

  /* 각 카드 스타일 */
  .simple-card {
    background: #ffffff; 
    border: 1px solid #eaeaea; 
    border-radius: 12px; 
    padding: 20px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.05); 
    transition: all 0.2s;
    height: 100%;
  }
  .simple-card:hover {
    transform: translateY(-3px); 
    box-shadow: 0 10px 20px rgba(0,0,0,0.1); 
  }

  .card-thumb-img {
    width: 100%;
    height: 180px; /* 이미지 높이 통일 */
    object-fit: cover;
    border-radius: 8px;
    margin-bottom: 15px;
  }

  .card-tag {
    font-size: 0.7em; font-weight: 700; color: #0071e3; text-transform: uppercase; margin-bottom: 5px;
  }

  .card-title {
    font-size: 1.15em; font-weight: 700; color: #1d1d1f; margin-bottom: 8px;
  }

  .card-desc {
    font-size: 0.9em; color: #6e6e73; line-height: 1.4;
  }

  .read-link {
    font-size: 0.9em; font-weight: 600; color: #0071e3; text-decoration: none; display: inline-flex; align-items: center; margin-top: 10px;
  }
  .read-link::after { content: '→'; margin-left: 5px; transition: margin-left 0.2s; }
  .simple-card:hover .read-link::after { margin-left: 10px; }

  /* 반응형 조정 */
  @media (max-width: 800px) {
    .notes-content-grid { grid-template-columns: 1fr; }
  }

</style>

<div class="page-container">

  <h1>Technical Notes</h1>
  <div class="page-intro">
    그래픽스 이론, 셰이더, 엔진 최적화 연구 등 <br>
    <span class="highlight-text">기술적 문제 해결(Solution)</span>과 <span class="highlight-text">심층 분석(Deep Dive)</span> 기록을 정리한 엔지니어링 노트입니다.
  </div>

  <div class="filter-container">
    <button class="filter-btn active" onclick="filterNotes('all')">All</button>
    <button class="filter-btn" onclick="filterNotes('implementation')">Implementation</button>
    <button class="filter-btn" onclick="filterNotes('optimization')">Optimization</button>
    <button class="filter-btn" onclick="filterNotes('analysis')">Deep Analysis</button>
    <button class="filter-btn" onclick="filterNotes('workflow')">Workflow</button>
  </div>

    <div class="notes-content-grid">

        <div class="simple-card" data-tags="implementation">
      <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=500" class="card-thumb-img" alt="Ocean Simulation">
      <span class="card-tag">Implementation</span>
      <div class="card-title">Ocean Simulation</div>
      <div class="card-desc">Gerstner Wave 공식을 HLSL로 구현하여 물리적인 파도 움직임을 표현했습니다.</div>
      <a href="#" class="read-link">Read Note</a>
    </div>

        <div class="simple-card" data-tags="analysis">
      <img src="https://images.unsplash.com/photo-1605810230434-7631ac76ec81?q=80&w=500" class="card-thumb-img" alt="UE5 Nanite">
      <span class="card-tag">Deep Analysis</span>
      <div class="card-title">UE5 Nanite Analysis</div>
      <div class="card-desc">나나이트 소스 코드를 분석하고 커스텀 패스를 추가하는 과정을 기록했습니다.</div>
      <a href="#" class="read-link">Read Note</a>
    </div>

        <div class="simple-card" data-tags="optimization">
      <img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?q=80&w=500" class="card-thumb-img" alt="Memory DOD">
      <span class="card-tag">Optimization</span>
      <div class="card-title">Memory DOD Pattern</div>
      <div class="card-desc">데이터 지향 설계(DOD)로 캐시 히트율을 높인 최적화 사례입니다.</div>
      <a href="#" class="read-link">Read Note</a>
    </div>
    
        <div class="simple-card" data-tags="workflow">
      <img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?q=80&w=500" class="card-thumb-img" alt="Asset Tool">
      <span class="card-tag">Workflow</span>
      <div class="card-title">Asset Tool</div>
      <div class="card-desc">에셋 네이밍을 검사하는 파이썬 자동화 툴 개발 기록입니다.</div>
      <a href="#" class="read-link">Read Note</a>
    </div>
    
        <div class="simple-card" data-tags="analysis implementation">
      <img src="https://images.unsplash.com/photo-1635070041078-e338af.jpg?q=80&w=500" class="card-thumb-img" alt="PBR">
      <span class="card-tag">Deep Analysis</span>
      <div class="card-title">PBR Math Artifacts</div>
      <div class="card-desc">BRDF 모델 수식을 분석하여 렌더링 아티팩트를 해결했습니다.</div>
      <a href="#" class="read-link">Read Note</a>
    </div>


  </div>


<script>
  // 필터링 스크립트는 그대로 유지
  function filterNotes(tag) {
    document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
    event.target.classList.add('active');

    const cards = document.querySelectorAll('.simple-card'); // 클래스 이름 변경됨
    cards.forEach(card => {
      if (tag === 'all') {
        card.classList.remove('hidden');
      } else {
        const cardTags = card.getAttribute('data-tags');
        if (cardTags && cardTags.includes(tag)) {
          card.classList.remove('hidden');
        } else {
          card.classList.add('hidden');
        }
      }
    });
  }
</script>
