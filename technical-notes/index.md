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
  
  .markdown-body {
    max-width: 100% !important; margin: 0 !important; width: 100% !important; padding: 0;
  }
  
/* ================= Main Page Container (중앙 정렬로 수정) ================= */
.page-container {
  max-width: 1250px; /* ⭐ 콘텐츠 최대 너비 조정 */
  
  /* 🔥 FIX 1: 왼쪽 밀림 현상 해결 (중앙 정렬 활성화) */
  margin: 40px auto; /* 상하 40px, 좌우 자동(중앙 정렬) */
  
  /* 좌우 패딩을 기본 레이아웃과 동일하게 50px로 설정하여 여백 불일치 해결 */
  padding: 0 50px; 
    
    background-color: transparent;
    box-shadow: none;
    border-radius: 0;
    
    text-align: left; 
  }

  /* 페이지 설명 */
  .page-intro {
    font-size: 1.2em; font-weight: 400; color: #424245; line-height: 1.6;
    
    /* ⭐ FIX 2: 텍스트 블록 중앙 정렬 */
    margin: 0 auto 40px auto; 
    
    word-break: keep-all; 
    max-width: 800px;
  }
  .highlight-text { color: #1d1d1f; font-weight: 600; }

  /* ================= Filter Buttons ================= */
  .filter-container { 
    margin-bottom: 40px; display: flex; gap: 12px; flex-wrap: wrap; 
    /* ⭐ FIX 3: 버튼 중앙 정렬 */
    justify-content: center; 
  }
  .filter-btn {
    padding: 10px 20px; border-radius: 24px;
    border: 1px solid #d2d2d7;
    background: #ffffff; 
    font-size: 0.95em; font-weight: 600; color: #666; cursor: pointer; transition: all 0.2s ease;
  }
  .filter-btn:hover { background: #f5f5f7; color: #1d1d1f; border-color: #86868b; }
  .filter-btn.active { background: #1d1d1f; color: #fff; border-color: #1d1d1f; }

  /* ================= Grid Layout (4열 고정 & 중앙 정렬) ================= */
  .bento-grid {
    display: grid;
    /* ⭐ FIX 4: 5열 대신 4열로 조정하여 카드 크기 확장 */
    grid-template-columns: repeat(4, 1fr); 
    gap: 30px;
    margin-bottom: 60px;
    /* justify-content: start; 삭제됨 - 중앙 정렬은 page-container가 담당 */
  }

  /* 반응형 미디어 쿼리 */
  @media (max-width: 1400px) { .bento-grid { grid-template-columns: repeat(4, 1fr); } }
  @media (max-width: 1100px) { .bento-grid { grid-template-columns: repeat(3, 1fr); } }
  @media (max-width: 800px)  { .bento-grid { grid-template-columns: repeat(2, 1fr); } }
  @media (max-width: 500px)  { .bento-grid { grid-template-columns: 1fr; } }


  /* ================= Card Style (Clean White UI) ================= */
  .bento-card {
    background: #ffffff; 
    border: 1px solid #eaeaea; 
    border-radius: 20px; 
    overflow: hidden; 
    position: relative; transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    display: flex; flex-direction: column;
    box-shadow: 0 4px 12px rgba(0,0,0,0.05);
  }
  .bento-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 15px 35px rgba(0,0,0,0.12); 
    border-color: transparent; 
    z-index: 10;
  }
  .bento-card.hidden { display: none; }

  /* 썸네일 (흰색 배경) */
  .card-thumb {
    width: 100%; 
    /* ⭐ FIX 5: 이미지 높이 확장 */
    height: 240px; 
    background-color: #ffffff; 
    position: relative; 
    border-bottom: 1px solid rgba(0,0,0,0.05); 
  }
  .card-thumb img {
    width: 100%; height: 100%; object-fit: cover; transition: transform 0.6s ease;
  }
  .bento-card:hover .card-thumb img { transform: scale(1.08); }

  /* 텍스트 내용 */
  .card-info { 
    padding: 24px; background: #fff; flex-grow: 1; display: flex; flex-direction: column;
  }
  
  /* ... (나머지 스타일 유지) ... */
</style>

<div class="page-container">

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
        <img src="https://images.unsplash.com/photo-1635070041078-e363dbe005cb?q=80&w=500" alt="PBR">
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
