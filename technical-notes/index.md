---
layout: page
title: Technical Notes
permalink: /technical-notes/
---

<style>
  /* ================= Global Layout & Reset ================= */
  body, .markdown-body {
    background-color: #f2f2f7 !important; /* 애플 스타일의 더 진한 기본 배경색 */
    font-family: -apple-system, BlinkMacSystemFont, "Pretendard", "Apple SD Gothic Neo", sans-serif;
    color: #1d1d1f;
  }
  
  .markdown-body {
    max-width: 100% !important; margin: 0 !important; width: 100% !important; padding: 0;
  }
  
  /* ================= Main Page Container (Layered Design) ================= */
  .page-container {
    /* 1. 너비 확장 및 왼쪽 정렬 */
    max-width: 1600px; 
    margin: 40px auto; /* 상하 여백, 중앙 정렬 */
    padding: 40px;
    
    /* 2. 배경 디자인 강화 (회색 배경 위에 떠 있는 흰색 패널) */
    background-color: #ffffff;
    border-radius: 24px; /* 더 큰 둥근 모서리 */
    box-shadow: 0 10px 30px rgba(0,0,0,0.05); /* 부드럽고 깊은 그림자 */
    
    /* 텍스트 왼쪽 정렬 */
    text-align: left;
  }

  /* 페이지 제목 (필요 시) */
  /* h1 { margin-top: 0; font-size: 2.2em; letter-spacing: -0.02em; } */

  /* 페이지 설명 */
  .page-intro {
    font-size: 1.2em; font-weight: 400; color: #424245; line-height: 1.6;
    margin-bottom: 40px; word-break: keep-all; max-width: 800px; /* 설명글은 너무 길어지지 않게 제한 */
  }
  .highlight-text { color: #1d1d1f; font-weight: 600; }

  /* ================= Filter Buttons ================= */
  .filter-container { 
    margin-bottom: 40px; display: flex; gap: 12px; flex-wrap: wrap; 
    justify-content: start; /* 버튼도 왼쪽 정렬 */
  }
  .filter-btn {
    padding: 10px 20px; border-radius: 24px; /* 버튼 크기/둥글기 확대 */
    border: 1px solid #d2d2d7;
    background: #ffffff; 
    font-size: 0.95em; font-weight: 600; color: #666; cursor: pointer; transition: all 0.2s ease;
  }
  .filter-btn:hover { background: #f5f5f7; color: #1d1d1f; border-color: #86868b; }
  .filter-btn.active { background: #1d1d1f; color: #fff; border-color: #1d1d1f; }

  /* ================= Grid Layout (5열 고정) ================= */
  .bento-grid {
    display: grid;
    /* 3. 5열 고정 및 왼쪽 정렬 */
    grid-template-columns: repeat(5, 1fr);
    gap: 30px; /* 간격 확대 */
    margin-bottom: 60px;
    justify-content: start;
  }

  /* 반응형 미디어 쿼리 (화면 작아질 때 대응) */
  @media (max-width: 1400px) { .bento-grid { grid-template-columns: repeat(4, 1fr); } }
  @media (max-width: 1100px) { .bento-grid { grid-template-columns: repeat(3, 1fr); } }
  @media (max-width: 800px)  { .bento-grid { grid-template-columns: repeat(2, 1fr); } }
  @media (max-width: 500px)  { .bento-grid { grid-template-columns: 1fr; } }


  /* ================= Card Style (Unified Rounded UI) ================= */
  .bento-card {
    background: #ffffff;
    border: none; 
    border-radius: 20px; /* 카드 전체 둥근 모서리 */
    overflow: visible; /* 그림자가 잘리지 않게 */
    position: relative; transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    display: flex; flex-direction: column;
    /* 기본 상태 그림자 */
    box-shadow: 0 4px 12px rgba(0,0,0,0.08);
  }
  .bento-card:hover {
    transform: translateY(-8px); /* 더 높이 떠오름 */
    box-shadow: 0 15px 35px rgba(0,0,0,0.15); /* 깊은 그림자 */
    z-index: 10;
  }
  .bento-card.hidden { display: none; }

  /* 썸네일 (상단 둥근 모서리 적용) */
  .card-thumb {
    width: 100%; height: 200px; /* 4. 크기 확대 (높이 증가) */
    background-color: #f0f0f2;
    position: relative; overflow: hidden;
    /* 2. 상단만 둥글게 처리하여 하단과 통일감 부여 */
    border-radius: 20px 20px 0 0; 
    border-bottom: 1px solid rgba(0,0,0,0.05);
  }
  .card-thumb img {
    width: 100%; height: 100%; object-fit: cover; transition: transform 0.6s ease;
  }
  .bento-card:hover .card-thumb img { transform: scale(1.08); }

  /* 텍스트 내용 (하단 둥근 모서리) */
  .card-info { 
    padding: 24px; background: #fff; flex-grow: 1; display: flex; flex-direction: column;
    border-radius: 0 0 20px 20px; /* 하단만 둥글게 */
  }

  .bento-tag {
    font-size: 0.7em; font-weight: 700;
    text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 12px; display: inline-block;
  }
  
  /* 태그별 색상 */
  .tag-impl { color: #0071e3; }
  .tag-opt { color: #ff3b30; }
  .tag-analysis { color: #af52de; }
  .tag-workflow { color: #28cd41; }

  .bento-title {
    font-size: 1.2em; font-weight: 700; color: #1d1d1f; margin-bottom: 10px; line-height: 1.35;
    letter-spacing: -0.01em;
  }

  .bento-desc {
    font-size: 0.9em; color: #86868b; line-height: 1.6; margin-bottom: 20px;
    display: -webkit-box; -webkit-line-clamp: 3; -webkit-box-orient: vertical; overflow: hidden;
    flex-grow: 1; 
  }
  
  /* Read Note 링크 */
  .read-link {
    font-size: 0.9em; font-weight: 600; color: #1d1d1f; text-decoration: none;
    display: inline-flex; align-items: center; margin-top: auto;
    opacity: 0.8; transition: all 0.2s;
  }
  .read-link::after { content: '→'; margin-left: 6px; transition: margin-left 0.2s; }
  .bento-card:hover .read-link { opacity: 1; color: #0071e3; }
  .bento-card:hover .read-link::after { margin-left: 10px; }

  .card-link-overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 5; opacity: 0; }

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
