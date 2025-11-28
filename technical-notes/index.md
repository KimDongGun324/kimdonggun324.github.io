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
  }

  /* 페이지 설명 (조금 더 작게) */
  .page-intro {
    font-size: 1.1em; font-weight: 400; color: #424245; line-height: 1.6;
    margin-bottom: 30px; word-break: keep-all;
  }
  .highlight-text { color: #1d1d1f; font-weight: 600; }

  /* ================= Filter Buttons (통일감 유지) ================= */
  .filter-container { margin-bottom: 40px; display: flex; gap: 8px; flex-wrap: wrap; }
  .filter-btn {
    padding: 6px 14px; border-radius: 18px; border: 1px solid #eaeaea; background: #fff;
    font-size: 0.85em; font-weight: 600; color: #666; cursor: pointer; transition: all 0.2s;
  }
  .filter-btn:hover { background: #f5f5f7; color: #1d1d1f; border-color: #d2d2d7; }
  .filter-btn.active { background: #1d1d1f; color: #fff; border-color: #1d1d1f; }

  /* ================= Compact Grid Layout ================= */
  .bento-grid {
    display: grid;
    /* 기본 3열 (화면 좁으면 2열, 1열로 자동 줄어듬) */
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px; /* 간격도 조금 줄임 */
    margin-bottom: 80px;
  }

  /* 카드 스타일 (컴팩트 버전) */
  .bento-card {
    background: #ffffff;
    border: 1px solid #eaeaea; border-radius: 16px; overflow: hidden;
    position: relative; transition: all 0.2s ease;
    display: flex; flex-direction: column;
    /* 높이 제한 없음 (내용물만큼만) */
  }
  .bento-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 10px 25px rgba(0,0,0,0.08); border-color: #0066cc;
    z-index: 10;
  }
  /* 필터링 숨김 클래스 */
  .bento-card.hidden { display: none; }

  /* 썸네일 (높이를 200px -> 160px로 줄임) */
  .card-thumb {
    width: 100%; height: 160px; background-color: #f5f5f7;
    position: relative; overflow: hidden; border-bottom: 1px solid #f0f0f0;
  }
  .card-thumb img {
    width: 100%; height: 100%; object-fit: cover; transition: transform 0.5s ease;
  }
  .bento-card:hover .card-thumb img { transform: scale(1.05); }

  /* 텍스트 내용 (패딩 축소) */
  .card-info { padding: 20px; background: #fff; flex-grow: 1; display: flex; flex-direction: column; }

  .bento-tag {
    font-size: 0.7em; font-weight: 700; color: #0066cc;
    text-transform: uppercase; letter-spacing: 0.05em; margin-bottom: 8px; display: block;
  }
  
  .bento-title {
    font-size: 1.1em; font-weight: 700; color: #1d1d1f; margin-bottom: 8px; line-height: 1.3;
  }

  .bento-desc {
    font-size: 0.85em; color: #666; line-height: 1.5; margin-bottom: 15px;
    display: -webkit-box; -webkit-line-clamp: 3; -webkit-box-orient: vertical; overflow: hidden;
    flex-grow: 1; /* 설명이 짧아도 버튼을 바닥으로 밀어줌 */
  }
  
  .read-link {
    font-size: 0.85em; font-weight: 600; color: #1d1d1f; text-decoration: none;
    display: inline-flex; align-items: center; margin-top: auto; /* 바닥에 붙이기 */
  }
  .read-link::after { content: '→'; margin-left: 4px; transition: margin-left 0.2s; }
  .bento-card:hover .read-link::after { margin-left: 8px; }

  /* 전체 카드 클릭 링크 */
  .card-link-overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 5; opacity: 0; }

</style>

<div class="page-intro">
  그래픽스 이론, 셰이더 구현, 엔진 최적화 등 <br>
  <span class="highlight-text">기술적 문제 해결 과정</span>과 <span class="highlight-text">심층 분석 기록</span>을 정리한 엔지니어링 노트입니다.
</div>

<div class="filter-container">
  <button class="filter-btn active" onclick="filterNotes('all')">All</button>
  <button class="filter-btn" onclick="filterNotes('graphics')">Graphics Theory</button>
  <button class="filter-btn" onclick="filterNotes('shader')">Shader Implementation</button>
  <button class="filter-btn" onclick="filterNotes('engine')">C++ & Engine Core</button>
  <button class="filter-btn" onclick="filterNotes('tools')">TA Tools & Pipeline</button>
</div>

<div class="bento-grid">

  <article class="bento-card" data-tags="shader graphics">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=600" alt="Ocean">
    </div>
    <div class="card-info">
      <span class="bento-tag">Shader Implementation</span>
      <h3 class="bento-title">Ocean Simulation with Gerstner Wave</h3>
      <p class="bento-desc">
        파도의 물리적 움직임을 HLSL로 구현하고 최적화한 연구입니다. 버텍스 오프셋 연산을 최적화하여 프레임 드랍을 15% 개선했습니다.
      </p>
      <span class="read-link">Read Case Study</span>
    </div>
    <a href="#" class="card-link-overlay"></a>
  </article>

  <article class="bento-card" data-tags="engine">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1605810230434-7631ac76ec81?q=80&w=600" alt="UE5">
    </div>
    <div class="card-info">
      <span class="bento-tag">C++ & Engine Core</span>
      <h3 class="bento-title">UE5 Rendering Pipeline Analysis</h3>
      <p class="bento-desc">
        언리얼 엔진 5의 나나이트(Nanite) 소스 코드를 분석하고, 커스텀 렌더 패스를 추가하여 스타일라이즈드 렌더링을 구현했습니다.
      </p>
      <span class="read-link">Read Case Study</span>
    </div>
    <a href="#" class="card-link-overlay"></a>
  </article>

  <article class="bento-card" data-tags="graphics math">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1635070041078-e363dbe005cb?q=80&w=600" alt="PBR">
    </div>
    <div class="card-info">
      <span class="bento-tag">Graphics Theory</span>
      <h3 class="bento-title">Physically Based Rendering Math</h3>
      <p class="bento-desc">
        Cook-Torrance BRDF 모델의 수학적 원리를 이해하고 직접 구현해봅니다. 미세면 분포 함수(D)와 기하학적 감쇠(G)를 분석합니다.
      </p>
      <span class="read-link">Read Case Study</span>
    </div>
    <a href="#" class="card-link-overlay"></a>
  </article>

  <article class="bento-card" data-tags="engine">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?q=80&w=600" alt="C++">
    </div>
    <div class="card-info">
      <span class="bento-tag">C++ & Engine Core</span>
      <h3 class="bento-title">Memory Optimization & DOD</h3>
      <p class="bento-desc">
        데이터 지향 설계(DOD)를 통한 캐시 히트율 최적화 연구. AoS vs SoA 구조의 성능 차이를 벤치마킹했습니다.
      </p>
      <span class="read-link">Read Case Study</span>
    </div>
    <a href="#" class="card-link-overlay"></a>
  </article>

  <article class="bento-card" data-tags="tools">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?q=80&w=600" alt="Python">
    </div>
    <div class="card-info">
      <span class="bento-tag">TA Tools & Pipeline</span>
      <h3 class="bento-title">Python Automation Tool</h3>
      <p class="bento-desc">
        3D 에셋의 네이밍 컨벤션을 검사하고 자동으로 수정해주는 파이썬 툴을 제작하여 작업 효율을 높였습니다.
      </p>
      <span class="read-link">Read Case Study</span>
    </div>
    <a href="#" class="card-link-overlay"></a>
  </article>

</div>

<script>
  // 필터링 기능 (카드 숨기기/보이기)
  function filterNotes(tag) {
    // 버튼 활성화 스타일
    document.querySelectorAll('.filter-btn').forEach(btn => btn.classList.remove('active'));
    event.target.classList.add('active');

    // 카드 필터링
    const cards = document.querySelectorAll('.bento-card');
    cards.forEach(card => {
      if (tag === 'all') {
        card.classList.remove('hidden');
      } else {
        const cardTags = card.getAttribute('data-tags');
        // 태그가 포함되어 있으면 보이고, 없으면 숨김
        if (cardTags && cardTags.includes(tag)) {
          card.classList.remove('hidden');
        } else {
          card.classList.add('hidden');
        }
      }
    });
  }
</script>
