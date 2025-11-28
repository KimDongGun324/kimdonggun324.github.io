---
layout: page
title: Technical Notes
permalink: /technical-notes/
---

<style>
  /* ================= Global Layout & Typography ================= */
  .markdown-body {
    max-width: 100% !important; margin: 0 !important; width: 100% !important; padding: 0 10px;
    font-family: -apple-system, BlinkMacSystemFont, "Pretendard", "Apple SD Gothic Neo", sans-serif;
  }

  /* 페이지 설명 문구 (애플 스타일로 개선) */
  .page-intro {
    font-size: 1.3em;
    font-weight: 400; /* 너무 두껍지 않게 */
    color: #424245;   /* 완전 검정 대신 진한 회색 (애플 그레이) */
    line-height: 1.5;
    letter-spacing: -0.02em; /* 자간을 살짝 좁혀서 단단한 느낌 */
    margin-bottom: 50px;
    max-width: 800px;
    word-break: keep-all; /* 한글 단어 끊김 방지 */
  }
  .highlight-text {
    color: #1d1d1f; font-weight: 600; /* 강조하고 싶은 단어 */
  }

  /* ================= Bento Grid Layout ================= */
  .bento-grid {
    display: grid;
    /* 기본 3열 그리드 (반응형) */
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: minmax(320px, auto); /* 행 높이 자동 조절 */
    gap: 20px;
    margin-bottom: 80px;
  }

  /* 벤토 카드 공통 스타일 */
  .bento-card {
    background: #ffffff;
    border: 1px solid #d2d2d7; /* 애플 스타일의 은은한 테두리 */
    border-radius: 20px;       /* 둥근 모서리 */
    overflow: hidden;
    position: relative;
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1); /* 부드러운 움직임 */
    display: flex;
    flex-direction: column;
  }

  .bento-card:hover {
    transform: scale(1.015); /* 아주 살짝 커짐 */
    box-shadow: 0 20px 40px rgba(0,0,0,0.08); /* 붕 뜨는 그림자 */
    border-color: rgba(0,0,0,0.1);
    z-index: 10;
  }

  /* ================= Card Variations (핵심!) ================= */
  
  /* [Span 2] 가로로 2칸 차지하는 큰 카드 (강조용) */
  .card-wide {
    grid-column: span 2;
  }
  
  /* [Span 3] 가로 전체 차지 (초대형 하이라이트) */
  .card-full {
    grid-column: span 3;
  }

  /* 모바일 대응: 화면 작으면 무조건 1칸씩 */
  @media (max-width: 900px) {
    .bento-grid { grid-template-columns: 1fr; }
    .card-wide, .card-full { grid-column: span 1; }
  }

  /* ================= Card Content ================= */
  .card-thumb {
    width: 100%;
    flex-grow: 1; /* 남은 공간 다 차지 */
    min-height: 200px;
    background-color: #f5f5f7;
    position: relative;
    overflow: hidden;
  }
  
  .card-thumb img {
    width: 100%; height: 100%; object-fit: cover;
    transition: transform 0.6s ease;
  }
  /* 호버 시 이미지 줌인 효과 */
  .bento-card:hover .card-thumb img { transform: scale(1.05); }

  .card-info {
    padding: 24px;
    background: #fff;
    display: flex; flex-direction: column; justify-content: center;
  }

  /* 태그 뱃지 */
  .bento-tag {
    display: inline-block;
    font-size: 0.75em; font-weight: 700;
    color: #007aff; /* 애플 블루 */
    text-transform: uppercase; letter-spacing: 0.05em;
    margin-bottom: 8px;
  }

  .bento-title {
    font-size: 1.4em; font-weight: 700; color: #1d1d1f;
    margin-bottom: 10px; line-height: 1.25; letter-spacing: -0.02em;
  }

  .bento-desc {
    font-size: 0.95em; color: #86868b; line-height: 1.5;
    display: -webkit-box; -webkit-line-clamp: 3; -webkit-box-orient: vertical; overflow: hidden; /* 3줄 넘어가면 ... 처리 */
  }

  /* 전체 카드 링크 (클릭 영역 확장) */
  .card-link {
    position: absolute; top: 0; left: 0; width: 100%; height: 100%;
    z-index: 5; opacity: 0;
  }

</style>

<div class="page-intro">
  그래픽스 이론, 셰이더 구현, 엔진 최적화 등 <br>
  <span class="highlight-text">기술적 문제 해결 과정</span>과 <span class="highlight-text">심층 분석 기록</span>을 정리한 엔지니어링 노트입니다.
</div>

<div class="bento-grid">

  <article class="bento-card card-wide">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=1200" alt="Ocean">
    </div>
    <div class="card-info">
      <span class="bento-tag">Shader R&D</span>
      <h3 class="bento-title">Ocean Simulation with Gerstner Wave</h3>
      <p class="bento-desc">
        파도의 물리적 움직임을 HLSL로 구현하고 최적화한 연구 기록입니다. 단순한 Sin 파형의 한계를 넘어 Gerstner Wave 공식을 적용하여 날카로운 파도 끝을 표현했으며, 버텍스 오프셋 연산을 최적화하여 모바일 환경에서 프레임을 15% 확보했습니다.
      </p>
    </div>
    <a href="#" class="card-link"></a>
  </article>

  <article class="bento-card">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1635070041078-e363dbe005cb?q=80&w=600" alt="PBR">
    </div>
    <div class="card-info">
      <span class="bento-tag">Graphics Theory</span>
      <h3 class="bento-title">PBR Math Deep Dive</h3>
      <p class="bento-desc">
        Cook-Torrance BRDF 모델의 수학적 원리를 이해하고 직접 구현해봅니다. 미세면 분포 함수(D)와 기하학적 감쇠(G)를 분석합니다.
      </p>
    </div>
    <a href="#" class="card-link"></a>
  </article>

  <article class="bento-card">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1605810230434-7631ac76ec81?q=80&w=600" alt="UE5">
    </div>
    <div class="card-info">
      <span class="bento-tag">Engine Core</span>
      <h3 class="bento-title">UE5 Rendering Pipeline</h3>
      <p class="bento-desc">
        언리얼 엔진 5의 나나이트(Nanite) 소스 코드를 분석하고, 커스텀 렌더 패스를 추가하여 스타일라이즈드 렌더링을 구현했습니다.
      </p>
    </div>
    <a href="#" class="card-link"></a>
  </article>

  <article class="bento-card card-wide">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?q=80&w=1200" alt="Optimization">
    </div>
    <div class="card-info">
      <span class="bento-tag">C++ & Optimization</span>
      <h3 class="bento-title">Memory Management & Data Oriented Design</h3>
      <p class="bento-desc">
        캐시 히트율(Cache Hit Rate)을 높이기 위한 데이터 지향 설계(DOD) 패턴을 연구했습니다. AoS vs SoA 구조의 성능 차이를 벤치마킹하고, 실제 게임 로직에 적용하여 연산 속도를 개선한 사례를 공유합니다.
      </p>
    </div>
    <a href="#" class="card-link"></a>
  </article>

  <article class="bento-card">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?q=80&w=600" alt="Security">
    </div>
    <div class="card-info">
      <span class="bento-tag">TA Tools</span>
      <h3 class="bento-title">Python Automation Tool</h3>
      <p class="bento-desc">
        3D 에셋의 네이밍 컨벤션을 검사하고 자동으로 수정해주는 파이썬 툴을 제작하여 작업 효율을 높였습니다.
      </p>
    </div>
    <a href="#" class="card-link"></a>
  </article>

</div>
