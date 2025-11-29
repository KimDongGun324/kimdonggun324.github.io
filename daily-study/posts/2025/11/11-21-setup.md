---
layout: page
title: 블로그 개설 및 Jekyll 테마 커스텀
permalink: /daily-study/posts/2025/11/11-21-setup/
---

(여기에 기존 블로그 개설 관련 내용이 있다면 남겨두세요. 없다면 이 줄을 지우세요.)

---

## 🎨 WebGL Shader: Interactive Neon Circle

블로그에 생동감을 더하기 위해 직접 GLSL로 작성한 WebGL 셰이더를 임베딩했습니다. 단순한 이미지가 아니라, 실시간으로 연산 되며 마우스 입력에 반응하는 절차적(Procedural) 그래픽입니다.

### Technical Breakdown: SDF & Glow

이 셰이더의 핵심은 이미지 텍스처를 전혀 사용하지 않고, 수학적 공식을 통해 형태를 그려내는 **SDF(Signed Distance Field)** 기법입니다.

원형의 빛 번짐(Glow) 효과를 물리적으로 표현하기 위해, 중심점으로부터의 거리에 반비례하는 역수 함수를 활용했습니다. 픽셀이 원의 경계(Radius)에 가까워질수록 분모가 0에 수렴하며 빛의 강도가 급격히 강해지는 원리입니다.

**핵심 수식 (The Glow Formula):**

> **Glow(d, r) = k / |d - r|**

여기서:
* **d**: 원점(중심)에서 현재 픽셀까지의 거리 (`length(uv)`)
* **r**: 원의 현재 반지름 (시간에 따라 변함)
* **k**: 빛의 강도 계수

이 수식을 통해 경계면이 칼같이 잘리는 것이 아니라, 빛이 부드럽게 퍼져나가는 물리 기반(Physically Based) 느낌의 감쇠를 구현했습니다.

### Interactive Demo

아래 캔버스에 마우스를 올리고 움직여보세요. (모바일에서는 터치)
* **마우스 Y축(상하):** 원의 기본 크기가 변합니다.
* **마우스 X축(좌우):** 빛의 색상(Red 채널)이 변합니다.

<div align="center" style="margin-top: 30px;">
    <canvas class="glslCanvas" data-fragment="
#ifdef GL_ES
precision mediump float;
#endif
uniform vec2 u_resolution;
uniform float u_time;
uniform vec2 u_mouse;
void main() {
    vec2 uv = (gl_FragCoord.xy - 0.5 * u_resolution.xy) / min(u_resolution.y, u_resolution.x);
    vec2 mouseNorm = u_mouse.xy / u_resolution.xy;
    float baseRadius = (u_mouse.x <= 0.0 && u_mouse.y <= 0.0) ? 0.3 : 0.1 + 0.4 * mouseNorm.y;
    float radius = baseRadius + 0.02 * sin(u_time * 5.0);
    float dist = length(uv);
    float glow = 0.015 / abs(dist - radius);
    vec3 baseColor = vec3(0.2, 0.5, 1.0);
    baseColor.r += mouseNorm.x * 0.8;
    vec3 color = baseColor * glow;
    gl_FragColor = vec4(color, 1.0);
}" width="500" height="500" style="cursor: crosshair; box-shadow: 0 0 20px rgba(0, 100, 255, 0.3); border-radius: 8px;"></canvas>
    
    <script type="text/javascript" src="https://rawgit.com/patriciogonzalezvivo/glslCanvas/master/dist/GlslCanvas.js"></script>
    <p style="font-size: 0.8em; color: gray;">Powered by glslCanvas & WebGL</p>
</div>
