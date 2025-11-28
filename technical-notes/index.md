---
layout: page
title: Technical Notes
permalink: /technical-notes/
---

<style>
  /* 레이아웃 초기화 */
  .markdown-body {
    max-width: 100% !important; margin: 0 !important; width: 100% !important; padding: 0 10px;
  }
  
  .page-desc {
    font-size: 1.1em; color: #666; margin-bottom: 40px; line-height: 1.6;
  }

  /* 그리드 레이아웃 */
  .research-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(380px, 1fr)); /* 카드 너비 */
    gap: 30px;
    margin-bottom: 60px;
  }

  /* 연구 카드 스타일 */
  .research-card {
    background: #ffffff;
    border: 1px solid #eaeaea;
    border-radius: 16px;
    overflow: hidden;
    transition: all 0.3s ease;
    display: flex;
    flex-direction: column;
    height: 100%;
  }
  
  .research-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 15px 30px rgba(0,0,0,0.1);
    border-color: #0066cc;
  }

  /* 썸네일 영역 */
  .card-thumb {
    width: 100%;
    height: 200px;
    background-color: #f5f5f7;
    overflow: hidden;
    border-bottom: 1px solid #eaeaea;
  }
  .card-thumb img {
    width: 100%; height: 100%; object-fit: cover;
    transition: transform 0.5s ease;
  }
  .research-card:hover .card-thumb img {
    transform: scale(1.05);
  }

  /* 텍스트 내용 */
  .card-content { padding: 25px; flex-grow: 1; display: flex; flex-direction: column; }
  
  .card-tags { margin-bottom: 12px; display: flex; gap: 8px; flex-wrap: wrap; }
  .tech-tag {
    font-size: 0.75em; font-weight: 700; padding: 4px 10px; border-radius: 20px;
    background: #f0f0f2; color: #555; text-transform: uppercase;
  }
  /* 태그별 컬러 포인트 */
  .tag-shader { color: #9c27b0; background: #f3e5f5; }
  .tag-engine { color: #e65100; background: #fff3e0; }

  .card-title {
    font-size: 1.4em; font-weight: 700; color: #1d1d1f; margin-bottom: 10px;
    line-height: 1.3;
  }
  .card-desc {
    font-size: 0.95em; color: #666; line-height: 1.6; margin-bottom: 20px;
    flex-grow: 1; /* 내용을 위로 밀고 버튼을 바닥에 붙임 */
  }

  .read-btn {
    font-weight: 600; color: #0066cc; text-decoration: none;
    display: inline-flex; align-items: center; align-self: flex-start;
  }
  .read-btn::after { content: '→'; margin-left: 6px; transition: margin-left 0.2s; }
  .research-card:hover .read-btn::after { margin-left: 12px; }

</style>

<p class="page-desc">
  그래픽스 이론, 셰이더 구현, 엔진 최적화 등 기술적 문제 해결 과정과 심층 분석 기록을 정리한 엔지니어링 노트입니다.
</p>

<div class="research-grid">

  <article class="research-card">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?q=80&w=600" alt="Ocean">
    </div>
    <div class="card-content">
      <div class="card-tags">
        <span class="tech-tag tag-shader">HLSL</span>
        <span class="tech-tag">Vertex Offset</span>
      </div>
      <h3 class="card-title">Ocean Simulation with Gerstner Wave</h3>
      <p class="card-desc">
        파도의 물리적 움직임을 HLSL로 구현하고 최적화한 연구입니다. 
        단순한 Sin 파형의 한계를 넘어 Gerstner Wave 공식을 적용하여 날카로운 파도 끝을 표현했습니다.
      </p>
      <a href="#" class="read-btn">Read Case Study</a>
    </div>
  </article>

  <article class="research-card">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1605810230434-7631ac76ec81?q=80&w=600" alt="UE5">
    </div>
    <div class="card-content">
      <div class="card-tags">
        <span class="tech-tag tag-engine">UE5 Core</span>
        <span class="tech-tag">C++</span>
      </div>
      <h3 class="card-title">UE5 Rendering Pipeline Analysis</h3>
      <p class="card-desc">
        언리얼 엔진 5의 나나이트(Nanite) 소스 코드를 분석하고, 커스텀 렌더 패스를 추가하여 스타일라이즈드 렌더링을 구현했습니다.
      </p>
      <a href="#" class="read-btn">Read Case Study</a>
    </div>
  </article>

  <article class="research-card">
    <div class="card-thumb">
      <img src="https://images.unsplash.com/photo-1635070041078-e363dbe005cb?q=80&w=600" alt="Math">
    </div>
    <div class="card-content">
      <div class="card-tags">
        <span class="tech-tag">Math</span>
        <span class="tech-tag tag-shader">PBR</span>
      </div>
      <h3 class="card-title">Physically Based Rendering Math</h3>
      <p class="card-desc">
        Cook-Torrance BRDF 모델의 수학적 원리를 이해하고 직접 구현해봅니다. 미세면 분포 함수(D), 기하학적 감쇠(G), 프레넬(F) 항을 분석합니다.
      </p>
      <a href="#" class="read-btn">Read Case Study</a>
    </div>
  </article>

</div>
