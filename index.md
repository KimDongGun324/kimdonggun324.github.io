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
  }

  /* 상단 래퍼 */
  .apple-wrapper {
    max-width: 1200px;
    margin: 0 auto;
    padding: 40px 0 80px 0;
    box-sizing: border-box;
  }

  /* 헤더 텍스트 */
  .apple-header {
    margin-bottom: 40px;
    padding-left: 10px;
  }
  .apple-headline {
    font-size: 2.8rem;
    font-weight: 700;
    line-height: 1.15;
    letter-spacing: -0.02em;
    color: var(--text-main);
    margin-bottom: 16px;
    word-break: keep-all;
  }
  .apple-subhead {
    font-size: 1.1rem;
    color: var(--text-sub);
    font-weight: 500;
    line-height: 1.5;
  }

  /* 벤토 그리드 레이아웃 */
  .bento-grid {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    grid-auto-rows: minmax(280px, auto);
    gap: var(--bento-gap);
  }

  /* 카드 공통 디자인 */
  .bento-item {
    background: #fff;
    border-radius: var(--card-radius);
    padding: 32px;
    position: relative;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    box-shadow: 0 4px 24px rgba(0,0,0,0.04);
    border: 1px solid rgba(0,0,0,0.03);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    text-decoration: none !important;
    color: inherit;
    box-sizing: border-box;
  }
  .bento-item:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 32px rgba(0,0,0,0.08);
  }

  /* 그리드 크기 조절 클래스 */
  .col-span-12 { grid-column: span 12; }
  .col-span-7  { grid-column: span 7; }
  .col-span-5  { grid-column: span 5; }
  .col-span-6  { grid-column: span 6; }

  /* 텍스트 스타일 */
  .bento-label {
    font-size: 0.75rem;
    font-weight: 700;
    text-transform: uppercase;
    color: var(--text-sub);
    margin-bottom: 10px;
    letter-spacing: 0.05em;
  }
  .bento-title {
    font-size: 1.8rem;
    font-weight: 700;
    line-height: 1.1;
    color: var(--text-main);
    margin-bottom: 8px;
    letter-spacing: -0.02em;
  }
  .bento-desc {
    font-size: 1rem;
    color: #424245;
    line-height: 1.45;
    font-weight: 400;
  }

  /* 다크 모드 카드 (강조) */
  .bento-dark {
    background: #1d1d1f;
    color: #fff;
  }
  .bento-dark .bento-title, 
  .bento-dark .bento-desc { color: #f5f5f7; }
  .bento-dark .bento-label { color: #a1a1a6; }

  /* 화살표 아이콘 */
  .icon-arrow {
    font-size: 1.4rem;
    align-self: flex-end;
    margin-top: auto;
    font-weight: 300;
  }

  /* 배경 그라데이션 */
  .bg-gradient-purple {
    position: absolute; inset: 0; 
    background: linear-gradient(135deg, #e0c3fc 0%, #8ec5fc 100%);
    opacity: 0.2; z-index: 0;
  }

  /* 반응형 처리 */
  @media (max-width: 900px) {
    .bento-grid { display: flex; flex-direction: column; }
    .bento-item { min-height: 240px; }
    .apple-headline { font-size: 2.2rem; }
  }
</style>


<div class="apple-wrapper reveal-on-scroll">
  
  <header class="apple-header">
    <h1 class="apple-headline">
      수식과 코드로 구현하는<br>
      <span style="color: #6e6e73;">빛의 논리.</span>
    </h1>
    <p class="apple-subhead">
      그래픽스 이론부터 엔진 최적화까지,<br>
      깊이 있게 연구하고 매일 기록합니다.
    </p>
  </header>

  <div class="bento-grid">
    <a href="/daily-study/" class="bento-item col-span-7 bento-dark">
      <div style="position:absolute; top:-50%; right:-20%; width:100%; height:200%; background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 60%); pointer-events:none;"></div>
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <div>
          <div class="bento-label">Development Log</div>
          <div class="bento-title">Daily Study Log</div>
          <div class="bento-desc" style="opacity:0.8;">
            "I never saved anything for the swim back."<br>
            매일 기록하는 성장과 끈기의 증명.
          </div>
        </div>
        <div class="icon-arrow">→</div>
      </div>
    </a>

    <a href="https://github.com" target="_blank" class="bento-item col-span-5">
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <div>
          <div class="bento-label">Source Code</div>
          <div class="bento-title">GitHub</div>
          <div class="bento-desc">
            모든 연구 프로젝트의<br>소스코드를 공개합니다.
          </div>
        </div>
        <div class="icon-arrow">↗</div>
      </div>
    </a>

    <a href="/technical-notes/" class="bento-item col-span-6">
      <div class="bg-gradient-purple"></div>
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <div>
          <div class="bento-label">Deep Dive</div>
          <div class="bento-title">Technical Notes</div>
          <div class="bento-desc">
            DirectX, Vulkan 및<br>렌더링 파이프라인 심층 분석.
          </div>
        </div>
        <div class="icon-arrow">→</div>
      </div>
    </a>

    <a href="/about.md" class="bento-item col-span-6" style="background:#f5f5f7;">
      <div style="position:relative; z-index:1; height:100%; display:flex; flex-direction:column;">
        <div>
          <div class="bento-label">Researcher</div>
          <div class="bento-title">DongGun Kim</div>
          <div class="bento-desc">
            M.S. Student @ CNU<br>
            Pearl Abyss TA를 목표로 정진합니다.
          </div>
        </div>
        <div class="icon-arrow">→</div>
      </div>
    </a>
  </div>
</div>


<div class="section-header reveal-on-scroll">
    <h2 class="section-title">Technical Notes</h2>
</div>

<div class="notes-grid">
    <a href="/technical-notes/" class="note-card reveal-on-scroll delay-1">
        <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=600" class="note-bg">
        <div class="note-content">
            <span class="note-category">Implementation</span>
            <h3 class="note-title">Shader & Rendering</h3>
            <p class="note-desc">논문과 이론을 바탕으로 직접 구현한 그래픽스 기술</p>
        </div>
    </a>
    <a href="/technical-notes/" class="note-card reveal-on-scroll delay-2">
        <img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?q=80&w=600" class="note-bg">
        <div class="note-content">
            <span class="note-category">Optimization</span>
            <h3 class="note-title">C++ & Performance</h3>
            <p class="note-desc">메모리와 연산 효율을 극대화하는 엔진 최적화 기록</p>
        </div>
    </a>
    <a href="/technical-notes/" class="note-card reveal-on-scroll delay-3">
        <img src="https://images.unsplash.com/photo-1605810230434-7631ac76ec81?q=80&w=600" class="note-bg">
        <div class="note-content">
            <span class="note-category">Deep Analysis</span>
            <h3 class="note-title">Engine Deep Dive</h3>
            <p class="note-desc">언리얼 엔진 소스 코드 분석 및 트러블슈팅</p>
        </div>
    </a>
    <a href="/technical-notes/" class="note-card reveal-on-scroll delay-4">
        <img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?q=80&w=600" class="note-bg">
        <div class="note-content">
            <span class="note-category">Workflow</span>
            <h3 class="note-title">TA Tools & Pipeline</h3>
            <p class="note-desc">효율을 높이는 자동화 툴과 파이프라인 구축</p>
        </div>
    </a>
</div>


<div class="section-header reveal-on-scroll">
    <h2 class="section-title">Research</h2>
</div>

<div class="research-grid">
    <a href="#" class="research-item reveal-on-scroll delay-1">
        <div class="research-thumb"><img src="https://images.unsplash.com/photo-1635070041078-e363dbe005cb?q=80&w=400"></div>
        <div class="research-info">
            <div class="research-title">Graphics Theory</div>
            <div class="research-sub">Math & Physics Base</div>
        </div>
    </a>
    <a href="#" class="research-item reveal-on-scroll delay-2">
        <div class="research-thumb"><img src="https://images.unsplash.com/photo-1550684848-fac1c5b4e853?q=80&w=400"></div>
        <div class="research-info">
            <div class="research-title">Shader Implementation</div>
            <div class="research-sub">HLSL / GLSL</div>
        </div>
    </a>
    <a href="#" class="research-item reveal-on-scroll delay-3">
        <div class="research-thumb"><img src="https://images.unsplash.com/photo-1518770660439-4636190af475?q=80&w=400"></div>
        <div class="research-info">
            <div class="research-title">C++ & Engine Core</div>
            <div class="research-sub">Architecture & Memory</div>
        </div>
    </a>
    <a href="#" class="research-item reveal-on-scroll delay-4">
        <div class="research-thumb"><img src="https://images.unsplash.com/photo-1558655146-d09347e92766?q=80&w=400"></div>
        <div class="research-info">
            <div class="research-title">TA Tools</div>
            <div class="research-sub">Python & Houdini</div>
        </div>
    </a>
</div>


<div class="section-header reveal-on-scroll" style="margin-top: 100px;">
    <h2 class="section-title">Projects</h2>
</div>

<span class="section-subtitle reveal-on-scroll">Engine & Tech Demo</span>
<div class="projects-grid">
    
    <a href="#" class="project-card-block reveal-on-scroll delay-1">
        <div class="project-img-wrapper">
            <img src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?q=80&w=800" class="project-bg">
            <div class="tech-badges-corner">
                <span class="tech-badge-style">C++</span><span class="tech-badge-style">Optimization</span>
            </div>
        </div>
        <div class="project-content-below">
            <h3 class="project-title-below">C++ Memory Optimization</h3>
            <p class="project-desc-below">Smart Pointer & Custom Allocator 구현을 통한 캐시 히트율 향상 및 성능 최적화.</p>
        </div>
    </a>

    <a href="#" class="project-card-block reveal-on-scroll delay-2">
        <div class="project-img-wrapper">
            <img src="https://images.unsplash.com/photo-1605810230434-7631ac76ec81?q=80&w=800" class="project-bg">
            <div class="tech-badges-corner">
                <span class="tech-badge-style">UE5</span><span class="tech-badge-style">Rendering</span>
            </div>
        </div>
        <div class="project-content-below">
            <h3 class="project-title-below">UE5 Rendering Pipeline Analysis</h3>
            <p class="project-desc-below">나나이트(Nanite) 및 루멘(Lumen) 소스 코드 심층 분석, 커스텀 렌더 패스 확장.</p>
        </div>
    </a>

</div>

<span class="section-subtitle reveal-on-scroll" style="margin-top: 60px;">Shader & Art R&D</span>
<div class="projects-grid">

    <a href="#" class="project-card-block reveal-on-scroll delay-1">
        <div class="project-img-wrapper">
            <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=800" class="project-bg">
            <div class="tech-badges-corner">
                <span class="tech-badge-style">HLSL</span><span class="tech-badge-style">Simulation</span>
            </div>
        </div>
        <div class="project-content-below">
            <h3 class="project-title-below">Ocean Simulation</h3>
            <p class="project-desc-below">HLSL을 활용한 물리 기반 파도 시뮬레이션. Gerstner Wave 알고리즘 적용.</p>
        </div>
    </a>

    <a href="#" class="project-card-block reveal-on-scroll delay-2">
        <div class="project-img-wrapper">
            <img src="https://images.unsplash.com/photo-1620641788421-7a1c342ea42e?q=80&w=800" class="project-bg">
            <div class="tech-badges-corner">
                <span class="tech-badge-style">PBR</span><span class="tech-badge-style">Material</span>
            </div>
        </div>
        <div class="project-content-below">
            <h3 class="project-title-below">Advanced Ice Material</h3>
            <p class="project-desc-below">Subsurface Scattering(SSS)와 Parallax Occlusion Mapping을 활용한 얼음 질감 표현.</p>
        </div>
    </a>

</div>
