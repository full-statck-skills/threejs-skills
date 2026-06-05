---
name: threejs-lights
description: >-
  three.js lighting: AmbientLight, HemisphereLight, DirectionalLight, PointLight, SpotLight, RectAreaLight, LightProbe, IESSpotLight, ProjectorLight, shadow subtypes, and addon helpers such as RectAreaLightUniformsLib, RectAreaLightTexturesLib, LightProbeGenerator, TiledLighting.
  Use when configuring direct/indirect light, shadows, probes, or area lights; for IES file loading use threejs-loaders; for node-based light graphs use threejs-node-tsl; for debug helpers use threejs-helpers.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- Enabling `castShadow` / `receiveShadow`, shadow map size, bias, normal bias, camera frusta for shadow casters
- Physical lights: intensity, distance/decay, angle/penumbra for spots, rect area setup
- `LightProbe` for irradiance-style probes; `IESSpotLight` with IES data

**IMPORTANT: lights vs loaders vs node-tsl**

| Topic | Skill |
|-------|--------|
| Light classes and shadows | **threejs-lights** |
| Loading IES/HDR files | **threejs-loaders** |
| LightNode / TSL lighting | **threejs-node-tsl** |

**Trigger phrases include:**

- "DirectionalLight", "SpotLight", "RectAreaLight", "castShadow", "shadow map"
- "阴影", "点光源", "面光源", "LightProbe"

## How to use this skill

1. **Base recipe**: ambient/hemisphere fill + directional sun + local points/spots.
2. **Shadows**: enable on renderer, mark casters/receivers, tune map size vs performance, adjust bias to remove acne/peter-panning.
3. **RectArea**: initialize addon libs per docs page before using light type.
4. **Probes**: place probes; generate data via addon generator when applicable; relate to materials env reflections (**threejs-materials**, **threejs-textures**).
5. **IES**: load profile via loader skill, attach to `IESSpotLight` per docs.
6. **Performance**: limit shadow-casting lights; use layers (**threejs-objects**) to exclude objects.

See [examples/workflow-directional-shadow.md](examples/workflow-directional-shadow.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Lights | https://threejs.org/docs/Light.html |
| Directional | https://threejs.org/docs/DirectionalLight.html |
| Spot | https://threejs.org/docs/SpotLight.html |
| Rect area | https://threejs.org/docs/RectAreaLight.html |

## Scope

- **In scope:** Core lights, shadow maps, probes, listed addons for rect area and probe generation.
- **Out of scope:** CSM deep theory (see addon Csm docs if user names it); baked lightmaps in DCC.

## Common pitfalls and best practices

- Shadow map resolution must match scene scale—tiny shadows on huge worlds look blocky.
- Point light shadows are six-face expensive—use wisely.
- `RectAreaLight` without required libs yields black or wrong shading—verify init.
- Mismatched physical units (intensity vs exposure) with **threejs-renderers** tone mapping causes blown or dim scenes.
- Shadow **bias** / **normalBias** trade-offs: acne vs peter-paning—tune with helper frusta (**threejs-helpers**).

## Documentation and version

Light and shadow classes live under [Lights](https://threejs.org/docs/#Lights) in [three.js docs](https://threejs.org/docs/). `RectAreaLight` and probe addons depend on extra init from **Addons → Lights**; IES profiles require **threejs-loaders** for file fetch before the light API is usable.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link the concrete light type (`DirectionalLight`, `SpotLight`, …) and shadow pages when shadows are on.
2. Separate **IES loading** to **threejs-loaders** and **LightNode** topics to **threejs-node-tsl**.
3. Give practical shadow map size / bias guidance with **threejs-helpers** for frustum visualization.
4. Mention `renderer.shadowMap.enabled` alongside light `castShadow` (see **threejs-renderers**).
5. Note performance cost of multiple shadow-casting lights.

## References

- https://threejs.org/docs/#Lights
- https://threejs.org/docs/DirectionalLight.html
- https://threejs.org/docs/SpotLight.html
- https://threejs.org/docs/LightShadow.html

## Keywords

**English:** lights, shadows, directional, spotlight, rectarea, lightprobe, three.js

**中文：** 灯光、阴影、平行光、聚光灯、面光源、LightProbe、three.js

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
