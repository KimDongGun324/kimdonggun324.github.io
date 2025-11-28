---
layout: page
title: Technical Notes
permalink: /technical-notes/
---

<style>
  /* 🔥 FIX 1: Daily Study Log와 동일하게, 충돌하는 모든 전역 정렬 CSS 제거 */
  /* 이 페이지에서는 페이지 콘텐츠만 스타일링하고, 레이아웃 정렬은 default.html에 의존합니다. */
  
  /* 페이지 설명 (수직 정렬 Fix) */
  .page-intro {
    font-size: 1.2em; font-weight: 400; color: #424245; line-height: 1.6;
    /* 제목 아래 수직 정렬을 위해 마진 조정 */
    margin: 0 0 15px 0; 
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

  /* ================= Grid Layout (4열 안정화 및 크기 확장) ================= */
  .bento-grid {
    display: grid;
    /* ⭐ FIX 4: 4열로 안정화 및 갭 조정 */
    grid-template-columns: repeat(4, 1fr); 
    gap: 20px; 
    margin-bottom: 60px;
  }

  /* 반응형 미디어 쿼리 (4열을 기준으로 재설정) */
  @media (max-width: 1400px) { .bento-grid { grid-template-columns: repeat(4, 1fr); } }
  @media (max-width: 1100px) { .bento-grid { grid-template-columns: repeat(3, 1fr); } } 
  @media (max-width: 800px)  { .bento-grid { grid-template-columns: repeat(2, 1fr); } } 
  @media (max-width: 500px)  { .bento-grid { grid-template-columns: 1fr; } }


  /* ================= Card Style (크기 확장 및 이미지 높이 조정) ================= */
  .bento-card {
    background: #ffffff; 
    border: 1px solid #eaeaea; 
    border-radius: 16px; 
    overflow: hidden; 
    position: relative; 
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    display: flex; 
    flex-direction: column;
    box-shadow: 0 2px 8px rgba(0,0,0,0.03); 
  }
  .bento-card:hover {
    transform: translateY(-5px); 
    box-shadow: 0 10px 25px rgba(0,0,0,0.1); 
    border-color: transparent; 
    z-index: 10;
  }
  .bento-card.hidden { display: none; }

  /* 썸네일 (이미지 영역) */
  .card-thumb {
    width: 100%; 
    height: 180px; /* 4열에 맞게 이미지 높이 안정화 */
    background-color: #ffffff; 
    position: relative; 
    border-bottom: 1px solid rgba(0,0,0,0.05); 
  }
  .card-thumb img {
    width: 100%; height: 100%; object-fit: cover; transition: transform 0.6s ease;
  }
  .bento-card:hover .card-thumb img { transform: scale(1.05); }

  /* 텍스트 내용 */
  .card-info { 
    padding: 18px; 
    background: #fff; 
    flex-grow: 1; 
    display: flex; 
    flex-direction: column;
  }
  .bento-tag {
    font-size: 0.7em; 
    font-weight: 700;
    text-transform: uppercase; 
    letter-spacing: 0.05em; 
    margin-bottom: 8px; 
  }

  .bento-title {
    font-size: 1.15em; 
    font-weight: 700; 
    color: #1d1d1f; 
    margin-bottom: 6px; 
    line-height: 1.35;
    letter-spacing: -0.01em;
  }

  .bento-desc {
    font-size: 0.85em; 
    color: #86868b; 
    line-height: 1.5; 
    margin-bottom: 15px; 
  }
  
  /* Read Note 링크 */
  .read-link {
    font-size: 0.9em; 
    font-weight: 600; 
    color: #1d1d1f; 
    text-decoration: none;
    display: inline-flex; 
    align-items: center; 
    margin-top: auto;
    opacity: 0.8; 
    transition: all 0.2s;
  }
  .read-link::after { content: '→'; margin-left: 5px; transition: margin-left 0.2s; }
  .bento-card:hover .read-link { opacity: 1; color: #0071e3; }
  .bento-card:hover .read-link::after { margin-left: 8px; }
</style>

<div class="page-container">

  <h1 style="margin-top: 0;">Technical Notes</h1>   <div class="page-intro">
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

  <div class="bento-grid">

    <article class="bento-card" data-tags="implementation">
      <div class="card-thumb">
        <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=500" alt="Ocean">
      </div>
      <div class="card-info">
        <span class="bento-tag tag-impl">Implementation</span>
        <h3 class="bento-title">Ocean Simulation</h3>
        <p class="bento-desc">Gerstner Wave 공식을 HLSL로 구현하여 물리적인 파도 움직임을 표현했습니다.</p>
        <span class="read-link">Read Note</span>
      </div>
      <a href="#" class="card-link-overlay"></a>
    </article>

    <article class="bento-card" data-tags="analysis">
      <div class="card-thumb">
        <img src="https://images.unsplash.com/photo-1605810230434-7631ac76ec81?q=80&w=500" alt="UE5">
      </div>
      <div class="card-info">
        <span class="bento-tag tag-analysis">Deep Analysis</span>
        <h3 class="bento-title">UE5 Nanite Analysis</h3>
        <p class="bento-desc">나나이트 소스 코드를 분석하고 커스텀 패스를 추가하는 과정을 기록했습니다.</p>
        <span class="read-link">Read Note</span>
      </div>
      <a href="#" class="card-link-overlay"></a>
    </article>

    <article class="bento-card" data-tags="optimization">
      <div class="card-thumb">
        <img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?q=80&w=500" alt="C++">
      </div>
      <div class="card-info">
        <span class="bento-tag tag-opt">Optimization</span>
        <h3 class="bento-title">Memory DOD Pattern</h3>
        <p class="bento-desc">데이터 지향 설계(DOD)로 캐시 히트율을 높인 최적화 사례입니다.</p>
        <span class="read-link">Read Note</span>
      </div>
      <a href="#" class="card-link-overlay"></a>
    </article>

    <article class="bento-card" data-tags="workflow">
      <div class="card-thumb">
        <img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?q=80&w=500" alt="Python">
      </div>
      <div class="card-info">
        <span class="bento-tag tag-workflow">Workflow</span>
        <h3 class="bento-title">Asset Tool</h3>
        <p class="bento-desc">에셋 네이밍을 검사하는 파이썬 자동화 툴 개발 기록입니다.</p>
        <span class="read-link">Read Note</span>
      </div>
      <a href="#" class="card-link-overlay"></a>
    </article>

     <article class="bento-card" data-tags="analysis implementation">
      <div class="card-thumb">
        <img src="https://images.unsplash.com/photo-1635070041078-e338af.jpg?q=80&w=500" alt="PBR">
      </div>
      <div class="card-info">
        <span class="bento-tag tag-analysis">Deep Analysis</span>
        <h3 class="bento-title">PBR Math Artifacts</h3>
        <p class="bento-desc">BRDF 모델 수식을 분석하여 렌더링 아티팩트를 해결했습니다.</p>
        <span class="read-link">Read Note</span>
      </div>
      <a href="#" class="card-link-overlay"></a>
    </article>

  </div>

</div>

<script>
  function filterNotes(tag) {
    document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
    event.target.classList.add('active');

    const cards = document.querySelectorAll('.bento-card');
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
