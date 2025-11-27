<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
<script>
  window.MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']]
    }
  };
</script>

# 🌊 DongGun's Shader Lab
> **Real-time Rendering & Graphics Researcher**
> *Master's Student @ Chonnam National Univ.*

---

## 👨‍💻 About Me
안녕하세요, **셰이더 디자이너**를 꿈꾸는 김동건입니다.
**HLSL, PBR, Linear Algebra**를 중점적으로 연구하며, 펄어비스의 엔진 개발 문화에 기여할 수 있는 테크니컬 아티스트가 되기 위해 공부하고 있습니다.

* **Main Tool:** Unreal Engine 5, HLSL/GLSL, C++
* **Knowledge Management:** Obsidian

---

## 🧪 Research Log: PBR Implementation
*(이곳은 셰이더 코드를 보여주는 예시 영역입니다)*

### 1. Specular Calculation (Cook-Torrance)
물리 기반 렌더링(PBR)을 위한 쿡-토런스 BRDF를 HLSL로 구현한 내용입니다.

$$
f_r = k_d f_{lambert} + k_s \frac{DFG}{4(\omega_o \cdot n)(\omega_i \cdot n)}
$$

<br>

**[HLSL Code Snippet]**

```hlsl
float3 SpecularBRDF(float3 N, float3 V, float3 L, float roughness, float3 F0)
{
    float3 H = normalize(V + L);
    float D = DistributionGGX(N, H, roughness);
    float G = GeometrySmith(N, V, L, roughness);
    float3 F = FresnelSchlick(max(dot(H, V), 0.0), F0);

    float3 numerator = D * G * F;
    float denominator = 4.0 * max(dot(N, V), 0.0) * max(dot(N, L), 0.0) + 0.0001; 
    return numerator / denominator;
}
