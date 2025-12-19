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

  /* 폰트 (Pretendard 적용: 애플 스타일 한글 폰트) */
  @import url("https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.8/dist/web/static/pretendard.css");

  body {
    font-family: "Pretendard", -apple-system, BlinkMacSystemFont, system-ui, Roboto, "Helvetica Neue", "Segoe UI", "Apple SD Gothic Neo", "Noto Sans KR", "Malgun Gothic", sans-serif;
  }

  /* 전체 래퍼 */
  .apple-wrapper {
    max-width: 1200px;
    margin: 0 auto;
    padding: 80px 0 100px 0;
    box-sizing: border-box;
  }

  /* [수정됨] 헤더 텍스트: 크기 축소 및 한 줄 최적화 */
  .apple-header {
    margin-bottom: 120px;
    padding: 0 20px;
    text-align: center;
  }
  .apple-headline {
    font-size: 2.5rem; /* 3.2rem -> 2.5rem 로 축소 (더 세련됨) */
    font-weight: 700;
    line-height: 1.3;
    letter-spacing: -0.03em; /* 자간을 좁혀서 단단한 느낌 */
    color: var(--text-main);
    margin-bottom: 16px;
    word-break: keep-all; /* 단어 중간에 줄바꿈 방지 */
  }
  .apple-subhead {
    font-size: 1.1rem;
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
    border: 1px solid rgba(0,0,0,0.06);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    text-decoration: none !important;
    color: inherit;
    box-sizing: border-box;
  }
  .bento-item:hover {
    transform: translateY(-4px);
    box-shadow: 0 15px 40px rgba(0,0,0,0.1);
  }
  
  /* [수정됨] 화살표 인터랙션 (호버시 오른쪽 이동) */
  .bento-item:hover .icon-arrow {
    transform: translateX(5px); /* 오른쪽으로 5px 이동 */
  }
  .icon-arrow {
    font-size: 1.5rem;
    align-self: flex-end;
    margin-top: auto;
    font-weight: 300;
    transition: transform 0.3s ease; /* 부드러운 움직임 */
  }

  /* 그리드 크기 조절 */
  .col-span-12 { grid-column: span 12; }
  .col-span-6  { grid-column: span 6; }

  /* 텍스트 스타일 */
  .bento-label {
    font-size: 0.8rem;
    font-weight: 800;
    text-transform: uppercase;
    color: var(--text-main);
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

  /* 다크 모드 카드 (Portfolio 강조) */
  .bento-dark {
    background: var(--accent-black);
    color: #fff;
    border: none;
  }
  .bento-dark .bento-title, 
  .bento-dark .bento-desc { color: #f5f5f7; }
  .bento-dark .bento-label { color: #a1a1a6; opacity: 1; }

  /* 기술 스택 뱃지 */
  .tech-badge-container {
    display: flex; gap: 8px; margin-top: 15px; flex-wrap: wrap;
  }
  .tech-badge {
    font-size: 0.75rem; font-weight: 600; padding: 4px 10px;
    border-radius: 6px; background: #f5f5f7; color: #1d1d1f; border: 1px solid #e5e5e5;
  }

  /* 썸네일 이미지 (컬러 유지 + 배경 흰색 강조) */
  .tech-thumb {
    width: 100%; height: 180px; object-fit: cover;
    border-radius: 12px; margin-bottom: 24px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.05);
    /* 흑백 필터 제거: 엔지니어링 결과물은 컬러가 생명 */
  }

  /* 반응형 */
  @media (max-width: 768px) {
    .bento-grid { display: flex; flex-direction: column; }
    .bento-item { min-height: 260px; }
    .col-span-6 { grid-column: span 12; }
    /* 모바일에서는 폰트 크기 더 줄임 */
    .apple-headline { font-size: 1.8rem; } 
  }
</style>


<div class="apple-wrapper reveal-on-scroll">
  
  <header class="apple-header">
    <h1 class="apple-headline">
      수식과 코드로 증명하는 빛의 논리
    </h1>
    <p class="apple-subhead">
      그래픽스 이론부터 엔진 최적화까지, 깊이 있게 연구하고 매일 기록합니다
    </p>
  </header>

  <div class="bento-grid">
    
    <a href="#" class="bento-item col-span-12 bento-dark" style="min-height: 320px;">
      <div style="position:absolute; inset:0; background: #000; z-index:0; overflow:hidden;">
         <img src="/assets/images/Gh.png" style="width:100%; height:100%; object-fit:contain; opacity:0.4;">
      </div>
      
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <div>
          <div class="bento-label" style="color:#a1a1a6;">Showcase</div>
          <div class="bento-title" style="font-size: 2.2rem;">Graphics R&D</div>
          <div class="bento-desc" style="max-width: 600px; opacity: 0.9;">
            DirectX/Vulkan API 자체 엔진 개발 및<br>
            HLSL 기반 물리 기반 렌더링(PBR) 구현.
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
        <div class="icon-arrow">→</div>
      </div>
    </a>

    <a href="/daily-study/" class="bento-item col-span-6" style="background: #fbfbfd;">
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <div>
          <div class="bento-label">Consistency</div>
          <div class="bento-title">Today I Learned</div>
          <div class="bento-desc">
            "I never saved anything for the swim back."<br>
            2025년 12월부터 이어온 매일의 연구 기록.
          </div>
        </div>
        <div class="icon-arrow">→</div>
      </div>
    </a>

  </div>
</div>


<div class="apple-wrapper reveal-on-scroll" style="padding-top: 0;">
  
  <header class="apple-header" style="margin-bottom: 30px; margin-top: 20px;">
    <h2 class="apple-headline" style="font-size: 2.0rem;">Technical Notes</h2>
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
