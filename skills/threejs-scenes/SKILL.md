---
name: threejs-scenes
description: >-
  three.js Scene graph root object, linear Fog and exponential FogExp2, Scene.background for solid colors or textures, and high-level environment background concepts that tie to PMREM and loaders in other skills.
  Use when configuring world container, atmospheric fog, or background; for HDR env map file loading use threejs-loaders; for GPU texture settings after load use threejs-textures; for tone mapping use threejs-renderers.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- `Scene` as root, `scene.background`, environment or skyball setup at scene level
- `Fog` or `FogExp2` parameters (`near`, `far`, `color`, density) and interaction with camera far plane
- Organizing render lists conceptually (children of scene)

**IMPORTANT: scenes vs textures vs loaders**

| Concern | Skill |
|---------|--------|
| Scene + fog API | **threejs-scenes** |
| Texture sampling, PMREM generator usage | **threejs-textures** |
| Fetching HDR/glTF | **threejs-loaders** |

**Trigger phrases include:**

- "Scene", "Fog", "FogExp2", "background", "雾"
- "场景根节点", "线性雾", "指数雾"

## How to use this skill

1. Instantiate `Scene` and add lights/meshes/cameras as children per graph rules (**threejs-objects**).
2. Choose fog: linear `Fog` vs exponential `FogExp2` for outdoor/horizon feel.
3. Tune fog `near`/`far` alongside camera `far` to avoid clipping artifacts.
4. Set `scene.background` to `Color`, `Texture`, or cube map per docs; env lighting still needs matching renderer/material settings.
5. When user wants IBL from HDR file, point to loaders → textures → materials pipeline explicitly.
6. Document that fog does not replace frustum culling for performance.

See [examples/workflow-fog-background.md](examples/workflow-fog-background.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Scenes | https://threejs.org/docs/#Scenes |
| Scenes | https://threejs.org/docs/Scene.html |
| Fog | https://threejs.org/docs/Fog.html |
| FogExp2 | https://threejs.org/docs/FogExp2.html |

## Scope

- **In scope:** `Scene`, fog types, background field semantics at API level.
- **Out of scope:** HDR / glTF file fetch (**threejs-loaders**); PMREM and texture sampling (**threejs-textures**); tone mapping / output color space defaults (**threejs-renderers**); full-screen fog-only post stack (**threejs-postprocessing**) unless tying to scene `Fog`; custom atmospheric scattering shaders beyond core fog API.

## Common pitfalls and best practices

- Fog color should harmonize with background to hide the horizon seam.
- Very large `far` on camera with fog still needs scene scale consistency.
- `background` rotation/intensity features depend on renderer version—cite current docs.

## Documentation and version

`Scene`, `Fog`, and background fields are documented under [Scenes](https://threejs.org/docs/#Scenes) in [three.js docs](https://threejs.org/docs/). Environment-related visuals often combine this skill with **threejs-textures** (PMREM) and **threejs-loaders** (HDR files)—link those pages when the user moves from “fog color” to “HDR sky”.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link `Scene`, `Fog`, or `FogExp2` official pages.
2. Relate fog distances to **threejs-camera** `far` plane and world scale.
3. Defer PMREM/HDR file steps to **threejs-textures** / **threejs-loaders** with one sentence each.
4. Avoid duplicating full color-management tutorials—point to renderer + textures skills.

## References

- https://threejs.org/docs/Scene.html
- https://threejs.org/docs/Fog.html
- https://threejs.org/docs/FogExp2.html

## Keywords

**English:** scene, fog, fogexp2, background, environment, three.js

**中文：** 场景、雾、Fog、背景、环境、three.js

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
