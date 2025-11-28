---
layout: page
title: Technical Notes
permalink: /technical-notes/
---

<style>
  /* ================= Global Layout ================= */
  .markdown-body {
    max-width: 100% !important; margin: 0 !important; width: 100% !important; padding: 0 10px;
    font-family: -apple-system, BlinkMacSystemFont, "Pretendard", "Apple SD Gothic Neo", sans-serif;
    /* 배경색: 컨텐츠와 구분을 위해 아주 연한 회색 적용 */
    background-color: #f5f5f7; 
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

  /* ================= Filter Buttons (목적 중심) ================= */
  .filter-container { margin-bottom: 40px; display: flex; gap: 10px; flex-wrap: wrap; }
  .filter-btn {
    padding: 8px 18px; border-radius: 20px; 
    border: 1px solid rgba(0,0,0,0.05);
    background: #ffffff; box-shadow: 0 2px 5px rgba(0,0,0,0.05);
    font-size: 0.9em; font-weight: 600; color: #666; cursor: pointer; transition: all 0.2s ease;
  }
  .filter-btn:hover { transform: translateY(-1px); color: #1d1d1f; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
  .filter-btn.active { background: #1d1d1f; color: #fff; border-color: #1d1d1f; }

  /* ================= Grid Layout ================= */
  .bento-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
    gap: 24px; margin-bottom: 80px;
  }

  /* 카드 스타일 (Depth감 강화) */
  .bento-card {
    background: #ffffff;
    border: none; /* 테두리 대신 그림자로 구분 */
    border-radius: 18px; 
    overflow: hidden;
    position: relative; transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    display: flex; flex-direction: column;
    /* 둥둥 떠 있는 느낌의 그림자 */
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
    width: 100%; height: 180px; background-color: #f0f0f2;
    position: relative; overflow: hidden;
    border-bottom: 1px solid rgba(0,0,0,0.05); /* 미세한 경계선 */
  }
  .card-thumb img {
    width: 100%; height: 100%; object-fit: cover; transition: transform 0.6s ease;
  }
  .bento-card:hover .card-thumb img { transform: scale(1.08); }

  /* 텍스트 내용 */
  .card-info { padding: 24px; background: #fff; flex-grow: 1; display: flex; flex-direction: column; }

  .bento-tag {
    font-size: 0.7em; font-weight: 700;
    text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 10px; display: inline-block;
  }
  
  /* 태그별 색상 구분 */
  .tag-impl { color: #0071e3; }       /* Implementation (Blue) */
  .tag-opt { color: #ff3b30; }        /* Optimization (Red) */
  .tag-analysis { color: #af52de; }   /* Deep Analysis (Purple) */
  .tag-workflow { color: #28cd41; }   /* Workflow (Green) */

  .bento-title {
    font-size: 1.25em; font-weight: 700; color: #1d1d1f; margin-bottom: 10px; line-height: 1.35;
    letter-spacing: -0.01em;
  }

  .bento-desc {
    font-size: 0.9em; color: #86868b; line-height: 1.6; margin-bottom: 20px;
    display: -webkit-box; -webkit-line-clamp: 3; -webkit-box-orient: vertical; overflow: hidden;
    flex-grow: 1; 
  }
  
  .read-link {
    font-size: 0.9em; font-weight: 600; color: #1d1d1f; text-decoration: none;
    display: inline-flex; align-items: center; margin-top: auto;
    opacity: 0.8; transition: opacity 0.2s;
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
        <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=600" alt="Ocean">
      </div>
      <div class="card-info">
        <span class="bento-tag tag-impl">Implementation</span>
        <h3 class="bento-title">Ocean Simulation with Gerstner Wave</h3>
        <p class="bento-desc">
          파도의 물리적 움직임을 HLSL로 구현한 연구입니다. 단순한 Sin 파형의 한계를 넘어 Gerstner Wave 공식을 적용하여 날카로운 파도 끝을 표현했습니다.
        </p>
        <span class="read-link">Read Note</span>
      </div>
      <a href="#" class="card-link-overlay"></a>
    </article>

    <article class="bento-card" data-tags="analysis">
      <div class="card-thumb">
        <img src="https://images.unsplash.com/photo-1605810230434-7631ac76ec81?q=80&w=600" alt="UE5">
      </div>
      <div class="card-info">
        <span class="bento-tag tag-analysis">Deep Analysis</span>
        <h3 class="bento-title">UE5 Rendering Pipeline Analysis</h3>
        <p class="bento-desc">
          언리얼 엔진 5의 나나이트(Nanite) 소스 코드를 심층 분석하고, 커스텀 렌더 패스를 추가하는 과정에서 발생한 이슈와 해결책을 정리했습니다.
        </p>
        <span class="read-link">Read Note</span>
      </div>
      <a href="#" class="card-link-overlay"></a>
    </article>

    <article class="bento-card" data-tags="analysis implementation">
      <div class="card-thumb">
        <img src="https://images.unsplash.com/photo-1635070041078-e363dbe005cb?q=80&w=600" alt="PBR">
      </div>
      <div class="card-info">
        <span class="bento-tag tag-analysis">Deep Analysis</span>
        <h3 class="bento-title">PBR Math: Solving Rendering Artifacts</h3>
        <p class="bento-desc">
          Cook-Torrance BRDF 모델의 수식을 분석하여 특정 각도에서 발생하는 렌더링 아티팩트(Artifact)의 원인을 규명하고 해결했습니다.
        </p>
        <span class="read-link">Read Note</span>
      </div>
      <a href="#" class="card-link-overlay"></a>
    </article>

    <article class="bento-card" data-tags="optimization">
      <div class="card-thumb">
        <img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?q=80&w=600" alt="C++">
      </div>
      <div class="card-info">
        <span class="bento-tag tag-opt">Optimization</span>
        <h3 class="bento-title">Memory Optimization & DOD Pattern</h3>
        <p class="bento-desc">
          데이터 지향 설계(DOD)를 도입하여 캐시 히트율을 높이고 메모리 파편화를 줄인 최적화 사례입니다. AoS vs SoA 벤치마킹 결과를 포함합니다.
        </p>
        <span class="read-link">Read Note</span>
      </div>
      <a href="#" class="card-link-overlay"></a>
    </article>

    <article class="bento-card" data-tags="workflow">
      <div class="card-thumb">
        <img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?q=80&w=600" alt="Python">
      </div>
      <div class="card-info">
        <span class="bento-tag tag-workflow">Workflow</span>
        <h3 class="bento-title">Automating Asset Validation Tool</h3>
        <p class="bento-desc">
          3D 에셋의 네이밍 컨벤션을 검사하고 자동으로 수정해주는 파이썬 툴을 개발하여, 팀 전체의 에셋 임포트 시간을 30% 단축했습니다.
        </p>
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
