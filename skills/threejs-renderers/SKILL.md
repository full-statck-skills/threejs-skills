---
name: threejs-renderers
description: >-
  Core rendering pipeline for three.js using WebGLRenderer and WebGPURenderer, canvas sizing, device pixel ratio, color space and tone mapping, output encoding, WebGL/WebGPU render targets, Info statistics, and addon overlay renderers (CSS2D/CSS3D/SVG).
  Use when tuning the draw loop, performance, or switching WebGPU vs WebGL; for EffectComposer passes use threejs-postprocessing; for XR session lifecycle use threejs-webxr; for shader graphs use threejs-node-tsl.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- `WebGLRenderer` or `WebGPURenderer` creation, `setSize`, `setPixelRatio`, `setAnimationLoop`
- Color management: `outputColorSpace`, `toneMapping`, exposure-like behavior via renderer properties
- `WebGLRenderTarget`, `WebGLCubeRenderTarget`, MRT, readback, or render-to-texture setup at renderer level
- `Info` (`render`, `triangles`, `calls`) for profiling; `CanvasTarget` / storage textures when working from docs index

**IMPORTANT: this skill vs neighbors**

| Topic | Use skill |
|-------|-----------|
| Fullscreen passes, bloom, SSAO, composer chain | **threejs-postprocessing** |
| VR/AR session, `XRButton`, hand models | **threejs-webxr** |
| Node-based frame graph / TSL post stack | **threejs-node-tsl** + renderer enablement |
| Loading assets | **threejs-loaders** |

**Trigger phrases include:**

- "WebGLRenderer", "WebGPURenderer", "setPixelRatio", "toneMapping", "WebGLRenderTarget"
- "渲染器", "像素比", "色调映射", "离屏渲染"

## How to use this skill

1. **Choose API**: `WebGLRenderer` for widest compatibility; `WebGPURenderer` when targeting WebGPU and node/TSL stack per project rules.
2. **Size**: match drawing buffer to canvas CSS size × `devicePixelRatio` with a sane cap (performance).
3. **Color**: set `outputColorSpace` / `toneMapping` consistently with textures and materials (cross-link threejs-textures, threejs-materials).
4. **Loop**: prefer `setAnimationLoop` for WebXR-friendly loops; otherwise `requestAnimationFrame`.
5. **Render targets**: pick `WebGLRenderTarget` vs cube/3D/array variants per environment/reflection needs; document dispose when recreating.
6. **Overlay UI**: import `CSS2DRenderer` / `CSS3DRenderer` from addons; sync size with main renderer.
7. **Profiling**: read `renderer.info` in dev builds only; explain cost of high pixel ratio and overdraw.
8. **WebXR hook**: enable XR on renderer but delegate session to **threejs-webxr**.

See [examples/workflow-renderer-resize.md](examples/workflow-renderer-resize.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Core Renderers | https://threejs.org/docs/WebGLRenderer.html |
| WebGPU | https://threejs.org/docs/WebGPURenderer.html |
| Render targets | https://threejs.org/docs/WebGLRenderTarget.html |
| Core PostProcessing (class) | https://threejs.org/docs/PostProcessing.html |
| Addons renderers | https://threejs.org/docs/CSS2DRenderer.html |

More class links: [references/official-sections.md](references/official-sections.md).

## Scope

- **In scope:** Renderer construction, sizing, color/tone, targets, Info, addon CSS/SVG renderers, high-level XR enable only.
- **Out of scope:** Individual composer passes (threejs-postprocessing); XR input (threejs-webxr); file IO (threejs-loaders).

## Common pitfalls and best practices

- Uncapped DPR burns fill rate; cap `setPixelRatio(Math.min(devicePixelRatio, 2))` on dense scenes.
- Mixing sRGB textures with wrong `outputColorSpace` causes washed or crushed blacks.
- Forgetting `dispose()` on render targets and full-screen quads leaks GPU memory on hot reload.
- `WebGPURenderer` feature set moves quickly—always cite current docs version note in answers.

## Documentation and version

`WebGLRenderer`, `WebGPURenderer`, and color-management defaults evolve across releases. Use the [Renderers](https://threejs.org/docs/#Renderers) section of [three.js docs](https://threejs.org/docs/) for the user’s three.js line; WebGPU and node stacks may require newer minors—link class pages rather than memorizing constructor defaults.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link official renderer or render-target pages (`WebGLRenderer`, `WebGLRenderTarget`, etc.).
2. Relate `outputColorSpace` / `toneMapping` to **threejs-textures** and **threejs-materials** when color looks wrong.
3. Point XR session details to **threejs-webxr** after `renderer.xr.enabled` is mentioned.
4. Mention `dispose()` for render targets and render lists on teardown or hot reload.
5. Cite **Addons → Renderers** (`CSS2DRenderer`, …) when overlays are in scope.

## References

- https://threejs.org/docs/WebGLRenderer.html
- https://threejs.org/docs/WebGPURenderer.html
- https://threejs.org/docs/#Renderers
- https://threejs.org/docs/Info.html

## Keywords

**English:** webglrenderer, webgpurenderer, rendertarget, pixelratio, tonemapping, outputcolorspace, css2d, css3d, three.js

**中文：** WebGLRenderer、WebGPU、渲染目标、像素比、色调映射、输出色彩空间、渲染器、three.js

## 能力边界

### ✅ 适用场景
- 当你需要使用此技能对应的技术栈时
- 当项目需要遵循最佳实践时
- 当需要快速上手或深入理解核心概念时

### ⚠️ 需要注意
- 复杂业务逻辑需要结合具体场景调整
- 性能优化需要根据实际数据量评估

### ❌ 不适用场景
- 不相关的技术栈或框架
- 需要完全自定义的特殊场景

## 常见陷阱 (Gotchas)

1. **版本兼容性**：注意框架版本与依赖库的兼容性，不同版本 API 可能有差异
2. **配置文件格式**：配置文件格式错误是最常见的问题，建议使用编辑器的语法检查
3. **环境变量**：确保所有必要的环境变量已正确设置，敏感信息不要硬编码
4. **依赖冲突**：多版本共存时注意依赖冲突，使用 lock 文件锁定版本
5. **性能陷阱**：大数据量场景下注意性能优化，避免 N+1 查询等常见问题

## 使用流程

### Step 1: 环境准备
确保开发环境已安装必要的依赖和工具。

### Step 2: 配置初始化
根据项目需求进行基础配置。

### Step 3: 核心功能使用
按照示例代码实现核心功能。

### Step 4: 测试验证
运行测试确保功能正常。

### Step 5: 部署上线
完成开发后进行部署和监控。
