---
layout: page
title: Technical Notes
permalink: /technical-notes/
---

<style>
  /* ================= Global Layout ================= */
  /* 전체 페이지 배경색을 연한 회색으로 깔아서 카드와 분리 */
  body, .markdown-body {
    background-color: #f5f5f7 !important; 
    font-family: -apple-system, BlinkMacSystemFont, "Pretendard", "Apple SD Gothic Neo", sans-serif;
  }
  
  .markdown-body {
    max-width: 100% !important; margin: 0 !important; width: 100% !important; padding: 0;
  }
  
  /* 페이지 컨테이너 */
  .page-container {
    max-width: 1400px; margin: 0 auto; padding: 40px 20px;
  }

  /* 페이지 설명 */
  .page-intro {
    font-size: 1.1em; font-weight: 400; color: #424245; line-height: 1.6;
    margin-bottom: 40px; word-break: keep-all;
  }
  .highlight-text { color: #1d1d1f; font-weight: 600; }

  /* ================= Filter Buttons ================= */
  .filter-container { margin-bottom: 40px; display: flex; gap: 10px; flex-wrap: wrap; }
  .filter-btn {
    padding: 8px 18px; border-radius: 20px; 
    border: 1px solid rgba(0,0,0,0.05);
    background: #ffffff; box-shadow: 0 2px 5px rgba(0,0,0,0.05);
    font-size: 0.9em; font-weight: 600; color: #666; cursor: pointer; transition: all 0.2s ease;
  }
  .filter-btn:hover { transform: translateY(-1px); color: #1d1d1f; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
  .filter-btn.active { background: #1d1d1f; color: #fff; border-color: #1d1d1f; }

  /* ================= Grid Layout (5열 목표) ================= */
  .bento-grid {
    display: grid;
    /* 최소 너비를 줄여서 한 줄에 5개까지 들어가게 조정 (반응형) */
    grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 24px; margin-bottom: 80px;
    justify-content: start; /* 왼쪽 정렬 */
  }

  /* 카드 스타일 (애플 스타일 레이어) */
  .bento-card {
    background: #ffffff; /* 카드는 완전 흰색 */
    border: none; 
    border-radius: 18px; /* 둥근 모서리 유지 */
    overflow: hidden;
    position: relative; transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    display: flex; flex-direction: column;
    /* 배경과 분리되는 부드러운 그림자 */
    box-shadow: 0 4px 6px rgba(0,0,0,0.02), 0 12px 24px rgba(0,0,0,0.06);
  }
  .bento-card:hover {
    transform: translateY(-6px) scale(1.01);
    box-shadow: 0 20px 40px rgba(0,0,0,0.12);
    z-index: 10;
  }
  .bento-card.hidden { display: none; }

  /* 썸네일 */
  .card-thumb {
    width: 100%; height: 160px; /* 높이를 살짝 줄여서 컴팩트하게 */
    background-color: #f0f0f2;
    position: relative; overflow: hidden;
    border-bottom: 1px solid rgba(0,0,0,0.05);
  }
  .card-thumb img {
    width: 100%; height: 100%; object-fit: cover; transition: transform 0.6s ease;
  }
  .bento-card:hover .card-thumb img { transform: scale(1.08); }

  /* 텍스트 내용 */
  .card-info { padding: 20px; background: #fff; flex-grow: 1; display: flex; flex-direction: column; }

  .bento-tag {
    font-size: 0.65em; font-weight: 700;
    text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 8px; display: inline-block;
  }
  
  /* 태그별 색상 */
  .tag-impl { color: #0071e3; }
  .tag-opt { color: #ff3b30; }
  .tag-analysis { color: #af52de; }
  .tag-workflow { color: #28cd41; }

  .bento-title {
    font-size: 1.1em; font-weight: 700; color: #1d1d1f; margin-bottom: 8px; line-height: 1.35;
    letter-spacing: -0.01em;
  }

  .bento-desc {
    font-size: 0.85em; color: #86868b; line-height: 1.6; margin-bottom: 16px;
    display: -webkit-box; -webkit-line-clamp: 3; -webkit-box-orient: vertical; overflow: hidden;
    flex-grow: 1; 
  }
  
  /* Read Note 링크 (호버 효과 유지) */
  .read-link {
    font-size: 0.85em; font-weight: 600; color: #1d1d1f; text-decoration: none;
    display: inline-flex; align-items: center; margin-top: auto;
    opacity: 0.8; transition: all 0.2s;
  }
  .read-link::after { content: '→'; margin-left: 6px; transition: margin-left 0.2s; }
  /* 호버 시 파란색으로 변경 */
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
        <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=400" alt="Ocean">
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
        <img src="https://images.unsplash.com/photo-1605810230434-7631ac76ec81?q=80&w=400" alt="UE5">
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
        <img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?q=80&w=400" alt="C++">
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
        <img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?q=80&w=400" alt="Python">
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
        <img src="https://images.unsplash.com/photo-1635070041078-e363dbe005cb?q=80&w=400" alt="PBR">
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
