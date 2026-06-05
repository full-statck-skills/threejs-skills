---
name: threejs-webxr
description: >-
  WebXR integration for three.js: WebXRManager and XRManager on the renderer, session initialization patterns, VRButton and ARButton helpers, XRControllerModelFactory and hand model families, XREstimatedLight, XRPlanes, and related addon Webxr utilities.
  Use for immersive sessions and controller/hand tracking—not for standard desktop camera projection (threejs-camera) or composer post effects (threejs-postprocessing).
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- Entering VR/AR, `navigator.xr`, reference spaces, session `requestAnimationFrame` loop via renderer
- `VRButton`, `ARButton`, `XRButton` creation patterns from examples
- Controller models, hand tracking meshes, estimated real-world lighting probes

**IMPORTANT: webxr vs renderers vs camera**

| Topic | Skill |
|-------|--------|
| Enable XR on renderer, sizing | **threejs-renderers** (basics) + **threejs-webxr** (session) |
| Desktop projection | **threejs-camera** |

**Trigger phrases include:**

- "WebXR", "VRButton", "ARButton", "XRControllerModelFactory", "hand tracking"
- "虚拟现实", "增强现实", "沉浸式"

## How to use this skill

1. **HTTPS** requirement and feature detection for XR availability.
2. **Buttons**: use official button factories to create DOM entry points; handle session end.
3. **Renderer**: call `renderer.xr.enabled = true` patterns per docs; prefer `setAnimationLoop` for XR loops.
4. **Controllers**: attach models via factories; read gamepad axes/buttons carefully with fallbacks.
5. **Hands**: opt-in hand models when runtime supports; performance implications.
6. **Lighting**: `XREstimatedLight` for AR realism—combine with **threejs-lights** cautiously.
7. **Exit**: restore non-XR render loop and resize handling on session end.

See [examples/workflow-xr-button.md](examples/workflow-xr-button.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Renderer XR | https://threejs.org/docs/WebXRManager.html |
| Webxr addons | https://threejs.org/docs/VRButton.html |
| Webxr addons | https://threejs.org/docs/ARButton.html |
| Webxr addons | https://threejs.org/docs/XRControllerModelFactory.html |

## Scope

- **In scope:** Documented WebXR manager + listed addons for buttons/controllers/hands/planes.
- **Out of scope:** Store submission, OpenXR runtime specifics, custom native layers.

## Common pitfalls and best practices

- Desktop testing requires XR emulation or hardware; fail gracefully.
- Mismatched reference space causes floor offset—validate stage vs local-floor.
- Heavy post chains may not meet VR frame time—profile aggressively.

## Documentation and version

WebXR entry points span **Addons → Webxr** and renderer [`WebXRManager`](https://threejs.org/docs/WebXRManager.html) in [three.js docs](https://threejs.org/docs/). Browser and device capabilities vary—answers should cite the official example name and three.js version when possible.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link `WebXRManager`, `VRButton`, `ARButton`, or controller factories as relevant.
2. Use `setAnimationLoop` patterns with **threejs-renderers** for XR render loops.
3. Avoid duplicating desktop **threejs-camera** projection advice for XR eyes.
4. Mention reference space choice (local-floor, etc.) at a high level with docs link.
5. Flag performance interaction with **threejs-postprocessing** in VR.

## References

- https://threejs.org/docs/WebXRManager.html
- https://threejs.org/docs/VRButton.html
- https://threejs.org/docs/ARButton.html
- https://threejs.org/docs/XRControllerModelFactory.html

## Keywords

**English:** webxr, vr, ar, xr session, controller, hand tracking, three.js

**中文：** WebXR、VR、AR、VRButton、手柄、手部追踪、沉浸式、three.js

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
