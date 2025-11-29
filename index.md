---
layout: default
title: Home
permalink: /
---

<style>
  :root {
    --bento-gap: 20px;
    --card-radius: 24px;
    --text-main: #1d1d1f;
    --text-sub: #86868b;
    --bg-gray-light: #f5f5f7;
    --accent-black: #1d1d1f; 
  }

  /* 전체 래퍼 */
  .apple-wrapper {
    max-width: 1200px;
    margin: 0 auto;
    padding: 60px 0 100px 0;
    box-sizing: border-box;
  }

  /* [수정] 헤더 텍스트: 가운데 정렬 적용 */
  .apple-header {
    margin-bottom: 60px;
    padding: 0 20px;
    text-align: center; /* 가운데 정렬 핵심 */
  }
  .apple-headline {
    font-size: 3.2rem;
    font-weight: 700;
    line-height: 1.2;
    letter-spacing: -0.02em;
    color: var(--text-main);
    margin-bottom: 20px;
    word-break: keep-all;
  }
  .apple-subhead {
    font-size: 1.2rem;
    color: var(--text-sub);
    font-weight: 400;
    line-height: 1.6;
  }

  /* 벤토 그리드 레이아웃 */
  .bento-grid {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    grid-auto-rows: minmax(280px, auto);
    gap: var(--bento-gap);
  }

  /* 카드 디자인 (공통) */
  .bento-item {
    background: #fff;
    border-radius: var(--card-radius);
    padding: 36px;
    position: relative;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    box-shadow: 0 2px 20px rgba(0,0,0,0.04);
    border: 1px solid rgba(0,0,0,0.06); /* 테두리를 조금 더 진하게 */
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    text-decoration: none !important;
    color: inherit;
    box-sizing: border-box;
  }
  .bento-item:hover {
    transform: translateY(-4px);
    box-shadow: 0 15px 40px rgba(0,0,0,0.1);
  }

  /* 그리드 크기 조절 */
  .col-span-12 { grid-column: span 12; }
  .col-span-6  { grid-column: span 6; }

  /* 텍스트 스타일 */
  .bento-label {
    font-size: 0.8rem;
    font-weight: 800; /* 굵게 변경 */
    text-transform: uppercase;
    color: var(--text-main); /* 회색에서 검정으로 변경하여 가독성 확보 */
    margin-bottom: 12px;
    letter-spacing: 0.05em;
    opacity: 0.6;
  }
  .bento-title {
    font-size: 2rem;
    font-weight: 700;
    line-height: 1.1;
    color: var(--text-main);
    margin-bottom: 10px;
    letter-spacing: -0.02em;
  }
  .bento-desc {
    font-size: 1.05rem;
    color: #424245;
    line-height: 1.5;
    font-weight: 400;
  }

  /* 다크 모드 카드 (Portfolio 강조용) */
  .bento-dark {
    background: var(--accent-black);
    color: #fff;
    border: none;
  }
  .bento-dark .bento-title, 
  .bento-dark .bento-desc { color: #f5f5f7; }
  .bento-dark .bento-label { color: #a1a1a6; opacity: 1; }

  /* 화살표 아이콘 */
  .icon-arrow {
    font-size: 1.5rem;
    align-self: flex-end;
    margin-top: auto;
    font-weight: 300;
  }

  /* [신규] 기술 스택 뱃지 스타일 */
  .tech-badge-container {
    display: flex;
    gap: 8px;
    margin-top: 15px;
    flex-wrap: wrap;
  }
  .tech-badge {
    font-size: 0.75rem;
    font-weight: 600;
    padding: 4px 10px;
    border-radius: 6px;
    background: #f5f5f7;
    color: #1d1d1f;
    border: 1px solid #e5e5e5;
  }

  /* [수정] 테크니컬 노트 썸네일 (흑백 처리) */
  .tech-thumb {
    width: 100%;
    height: 180px;
    object-fit: cover;
    border-radius: 12px;
    margin-bottom: 24px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.05);
    filter: grayscale(100%); /* 기본 흑백 */
    transition: filter 0.4s ease; /* 부드러운 전환 */
  }
  /* 호버 시 컬러로 변경 */
  .bento-item:hover .tech-thumb {
    filter: grayscale(0%);
  }

  /* 반응형 */
  @media (max-width: 768px) {
    .bento-grid { display: flex; flex-direction: column; }
    .bento-item { min-height: 260px; }
    .col-span-6 { grid-column: span 12; }
    .apple-headline { font-size: 2.2rem; }
    .apple-header { text-align: left; } /* 모바일은 왼쪽 정렬이 나을 수 있음 */
  }
</style>


<div class="apple-wrapper reveal-on-scroll">
  
  <header class="apple-header">
    <h1 class="apple-headline">
      수식과 코드로 증명하는<br>
      <span style="color: #86868b;">빛의 논리.</span>
    </h1>
    <p class="apple-subhead">
      그래픽스 이론부터 엔진 최적화까지,<br>
      깊이 있게 연구하고 매일 기록합니다.
    </p>
  </header>

  <div class="bento-grid">
    
    <a href="#" class="bento-item col-span-12 bento-dark" style="min-height: 380px;">
      <div style="position:absolute; inset:0; background: linear-gradient(45deg, #000000 0%, #2c2c2e 100%); z-index:0;"></div>
      
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <div>
          <div class="bento-label" style="color:#a1a1a6;">Showcase</div>
          <div class="bento-title" style="font-size: 2.4rem;">Graphics R&D</div>
          <div class="bento-desc" style="max-width: 600px; opacity: 0.9;">
            DirectX/Vulkan API를 활용한 자체 엔진 개발 및<br>
            HLSL 기반의 물리 기반 렌더링(PBR) 구현 결과물.
          </div>
        </div>
        <div class="icon-arrow" style="color: #fff;">View Portfolio →</div>
      </div>
    </a>

    <a href="https://github.com" target="_blank" class="bento-item col-span-6">
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <div>
          <div class="bento-label">Source Code</div>
          <div class="bento-title">GitHub</div>
          <div class="bento-desc">
            모든 연구 프로젝트의 소스코드를<br>투명하게 공개합니다.
          </div>
          <div class="tech-badge-container">
            <span class="tech-badge">C++</span>
            <span class="tech-badge">HLSL</span>
            <span class="tech-badge">Python</span>
            <span class="tech-badge">UE5</span>
          </div>
        </div>
        <div class="icon-arrow">↗</div>
      </div>
    </a>

    <a href="/daily-study/" class="bento-item col-span-6" style="background: #fbfbfd;">
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <div>
          <div class="bento-label">Consistency</div>
          <div class="bento-title">Daily Study Log</div>
          <div class="bento-desc">
            "I never saved anything for the swim back."<br>
            2025년 11월부터 이어온 매일의 연구 기록.
          </div>
        </div>
        <div class="icon-arrow">→</div>
      </div>
    </a>

  </div>
</div>


<div class="apple-wrapper reveal-on-scroll" style="padding-top: 0;">
  
  <header class="apple-header" style="margin-bottom: 30px; margin-top: 20px;">
    <h2 class="apple-headline" style="font-size: 2.2rem;">Technical Notes</h2>
    <p class="apple-subhead">Engine Architecture & Optimization Notes</p>
  </header>

  <div class="bento-grid">
    
    <a href="/technical-notes/" class="bento-item col-span-6">
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=600" class="tech-thumb" alt="Shader">
        <div>
          <div class="bento-label">Implementation</div>
          <div class="bento-title" style="font-size: 1.5rem;">Shader & Rendering</div>
          <div class="bento-desc">
            논문과 이론을 바탕으로 직접 구현한<br>물리 기반 렌더링(PBR) 기술.
          </div>
        </div>
        <div class="icon-arrow">→</div>
      </div>
    </a>

    <a href="/technical-notes/" class="bento-item col-span-6">
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?q=80&w=600" class="tech-thumb" alt="C++">
        <div>
          <div class="bento-label">Optimization</div>
          <div class="bento-title" style="font-size: 1.5rem;">C++ & Performance</div>
          <div class="bento-desc">
            메모리 관리와 캐시 히트율을 고려한<br>엔진 레벨 최적화 기록.
          </div>
        </div>
        <div class="icon-arrow">→</div>
      </div>
    </a>

    <a href="/technical-notes/" class="bento-item col-span-6">
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <img src="https://images.unsplash.com/photo-1605810230434-7631ac76ec81?q=80&w=600" class="tech-thumb" alt="Engine">
        <div>
          <div class="bento-label">Deep Analysis</div>
          <div class="bento-title" style="font-size: 1.5rem;">Engine Deep Dive</div>
          <div class="bento-desc">
            언리얼 엔진 소스 코드 분석 및<br>렌더링 파이프라인 개조.
          </div>
        </div>
        <div class="icon-arrow">→</div>
      </div>
    </a>

    <a href="/technical-notes/" class="bento-item col-span-6">
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?q=80&w=600" class="tech-thumb" alt="Tools">
        <div>
          <div class="bento-label">Workflow</div>
          <div class="bento-title" style="font-size: 1.5rem;">TA Tools & Pipeline</div>
          <div class="bento-desc">
            Python & Houdini를 활용한<br>자동화 툴과 파이프라인 구축.
          </div>
        </div>
        <div class="icon-arrow">→</div>
      </div>
    </a>

  </div>
</div>
