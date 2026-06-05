---
name: threejs-camera
description: >-
  three.js cameras: Camera base, PerspectiveCamera, OrthographicCamera, CubeCamera, ArrayCamera, StereoCamera; projection matrices, aspect, FOV, orthographic frustum sizes, near/far planes, and dynamic environment maps with CubeCamera.
  Use when placing views, rendering reflections, or multi-view splits; for XR projections and eye matrices use threejs-webxr; for post pass camera tricks use threejs-postprocessing alongside threejs-renderers.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- Switching perspective vs orthographic, `fov`, `aspect`, `zoom`, `near`, `far`
- `CubeCamera` for real-time environment maps or reflections (update rate caveats)
- `ArrayCamera`/`StereoCamera` for multi-view or stereo off-axis projection (non-XR)

**IMPORTANT: camera vs webxr vs post**

| Topic | Skill |
|-------|--------|
| Standard desktop projection | **threejs-camera** |
| XR reference spaces, IPD | **threejs-webxr** |
| Offscreen pass cameras inside composer | **threejs-postprocessing** |

**Trigger phrases include:**

- "PerspectiveCamera", "OrthographicCamera", "CubeCamera", "aspect", "near", "far"
- "透视相机", "正交", "立方体相机"

## How to use this skill

1. **Perspective**: set `aspect` = width/height; update on resize (**threejs-renderers** example workflow).
2. **Orthographic**: define `left/right/top/bottom` in world units for CAD/2.5D views.
3. **Near/far**: balance depth precision vs containing scene bounds; relate to fog (**threejs-scenes**).
4. **CubeCamera**: position at reflection probe; call `update` when scene static enough; use render target outputs per docs.
5. **Stereo/Array**: advanced; cite docs for eye parameters; defer XR to **threejs-webxr**.
6. **Projection matrix**: call `updateProjectionMatrix()` after parameter edits.
7. **Helpers**: `CameraHelper` lives in **threejs-helpers**.

See [examples/workflow-perspective-resize.md](examples/workflow-perspective-resize.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Cameras (index) | https://threejs.org/docs/#Cameras |
| Cameras | https://threejs.org/docs/Camera.html |
| Perspective | https://threejs.org/docs/PerspectiveCamera.html |
| Orthographic | https://threejs.org/docs/OrthographicCamera.html |
| Cube | https://threejs.org/docs/CubeCamera.html |
| Multi-view | https://threejs.org/docs/ArrayCamera.html |
| Stereo (non-XR) | https://threejs.org/docs/StereoCamera.html |

## Scope

- **In scope:** Core camera classes and parameters; cube/array/stereo overview.
- **Out of scope:** WebXR reference spaces, eye matrices, session lifecycle (**threejs-webxr**); shadow map camera tuning (**threejs-lights**); pass-internal cameras in composer (**threejs-postprocessing**).

## Common pitfalls and best practices

- Wrong `aspect` after resize stretches image—always sync with canvas.
- Too small `near` hurts depth precision in large worlds.
- `CubeCamera` every frame is expensive—throttle for performance.

## Documentation and version

Camera parameters and `CubeCamera` update behavior follow the [Cameras](https://threejs.org/docs/#Cameras) section of [three.js docs](https://threejs.org/docs/). WebXR uses different projection paths—hand off to **threejs-webxr** when the user mentions headsets or reference spaces.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link `PerspectiveCamera`, `OrthographicCamera`, or `CubeCamera` as relevant.
2. Pair resize with **threejs-renderers** `setSize` / DPR patterns when relevant.
3. Route `XR`/`WebXRManager` questions to **threejs-webxr** after one-line renderer mention.
4. Mention `updateProjectionMatrix()` after intrinsic changes.
5. Use **threejs-helpers** `CameraHelper` for shadow frustum debug when discussing lights.

## References

- https://threejs.org/docs/#Cameras
- https://threejs.org/docs/PerspectiveCamera.html
- https://threejs.org/docs/CubeCamera.html

## Keywords

**English:** perspectivecamera, orthographiccamera, cubecamera, projection, aspect, near, far, three.js

**中文：** 相机、透视、正交、投影、近裁剪、远裁剪、CubeCamera、three.js

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
