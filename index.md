<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
<script>
  window.MathJax = {
    tex: { inlineMath: [['$', '$'], ['\\(', '\\)']] }
  };
</script>

# 🌊 DongGun's Shader Lab
> **Real-time Rendering & Graphics Researcher**
> *Master's Student @ Chonnam National Univ.*

---

## 🎯 Portfolio Highlights
펄어비스 셰이더 디자이너 직무를 목표로 **이론(Math/Physics), 구현(HLSL), 최적화(C++)** 세 가지 역량을 쌓고 있습니다.

### 📚 1. Graphics Theory & Math
단순 구현을 넘어 **"왜 이렇게 렌더링 되는가?"**에 대한 수학적/물리적 원리를 탐구합니다.
- [📂 Real-Time Rendering 4.e Study Log](./01_Graphics_Theory/README.md)
- [📂 Linear Algebra for Graphics](./01_Graphics_Theory/Math_Physics.md)

### 🎨 2. Shader Implementation (HLSL/GLSL)
수식을 코드로 옮겨 시각적 결과를 만들어낸 기록입니다.
- [📂 Unity/Unreal Shader Sketches](./02_Shader_Lab/README.md)
- [📂 Procedural Rendering Tests](./02_Shader_Lab/Procedural.md)

### ⚙️ 3. C++ & Engine Architecture
로우 레벨 최적화와 엔진 구조 이해를 위한 C++ 연구 기록입니다.
- [📂 C++ Memory Management & Optimization](./03_Engine_CPP/CPP_DeepDive.md)
- [📂 Unreal Engine Source Analysis](./03_Engine_CPP/UE5_Analysis.md)

---

## 🔥 Daily Dev Log (Recent Commits)
> *매일 공부한 내용을 정리하여 지속적으로 업데이트하고 있습니다.*

### [2025-11-27] PBR Lighting Model Refactoring
- **Topic:** Cook-Torrance BRDF 최적화
- **Summary:** `pow()` 연산을 줄이기 위해 근사식(Approximation)을 적용하여 FPS를 5% 향상시킴.
- **Code:**
  ```hlsl
  // 최적화 전: pow(nH, power)
  // 최적화 후: 근사식 사용
  float DistributionGGX(float3 N, float3 H, float roughness) { ... }
