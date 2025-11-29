---
layout: page
title: 블로그 개설 및 Jekyll 테마 커스텀
permalink: /daily-study/posts/2025/11/11-21-setup/
---

<div align="center">
    <h3>Live WebGL Shader Test</h3>
    <canvas class="glslCanvas" data-fragment="
#ifdef GL_ES
precision mediump float;
#endif

uniform vec2 u_resolution;
uniform float u_time;

void main() {
    vec2 uv = (gl_FragCoord.xy - 0.5 * u_resolution.xy) / min(u_resolution.y, u_resolution.x);
    float radius = 0.3 + 0.05 * sin(u_time * 3.0);
    float dist = length(uv);
    float glow = 0.015 / abs(dist - radius);
    vec3 color = vec3(0.2, 0.5, 1.0) * glow;
    color.r += 0.1 * sin(u_time);
    gl_FragColor = vec4(color, 1.0);
}
" width="500" height="500"></canvas>
    
    <script type="text/javascript" src="https://rawgit.com/patriciogonzalezvivo/glslCanvas/master/dist/GlslCanvas.js"></script>
</div>
