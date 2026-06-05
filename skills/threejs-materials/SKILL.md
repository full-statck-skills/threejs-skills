---
name: threejs-materials
description: >-
  Classic three.js materials (non-Node): MeshStandardMaterial, MeshPhysicalMaterial, Phong/Lambert/Toon/Basic, Line/Points/Sprite materials, MeshMatcapMaterial, MeshNormalMaterial, depth/distance materials, ShaderMaterial and RawShaderMaterial.
  Use when tuning PBR maps, transparency, depth write, skinning flags, or writing GLSL in ShaderMaterial; for TSL/NodeMaterial/WebGPU shader graphs use threejs-node-tsl instead—not both for the same authoring path unless migrating.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- Choosing among built-in mesh materials, map slots (albedo, normal, roughness, metalness, ao, emissive), `envMap`
- Transparency sorting issues, `alphaTest`, `depthWrite`, blending modes, side/double-sided rendering
- `ShaderMaterial` / `RawShaderMaterial` uniforms, includes, and compatibility with lights pipeline
- Line, points, sprite materials for vector overlays and particles

**IMPORTANT: classic materials vs node-tsl**

| Need | Skill |
|------|--------|
| Standard PBR with maps, physical clearcoat/sheen | **threejs-materials** |
| TSL nodes, `NodeMaterial`, WebGPU-first shading, compute-style graph | **threejs-node-tsl** |
| Migrating ShaderMaterial → TSL | **threejs-node-tsl** (conceptual), keep ShaderMaterial here until cutover |

**Trigger phrases include:**

- "MeshStandardMaterial", "MeshPhysicalMaterial", "ShaderMaterial", "transparent", "alphaTest"
- "PBR", "物理材质", "透明", "自定义着色器"

## How to use this skill

1. **Select class** by lighting model: `MeshBasic` (unlit), Lambert/Phong (legacy lit), Standard/Physical (PBR).
2. **Assign maps** and ensure **color space** correctness for albedo vs data maps (link threejs-textures).
3. **Environment**: set `envMap` from cube or equirect; align `metalness`/`roughness`; consider `MeshPhysicalMaterial` for transmission/IOR when needed.
4. **Transparency**: order objects or use `alphaTest`/`depthWrite` trade-offs; mention sorting limitations.
5. **ShaderMaterial**: minimize re-lit work unless intentional; document required lights and `lights: true` flag behavior per version docs.
6. **Performance**: share materials across meshes; avoid cloning per frame.
7. **Skinning/morph**: set `skinning`/`morphTargets` where applicable—mesh side in **threejs-objects**.

See [examples/workflow-pbr-transparent.md](examples/workflow-pbr-transparent.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Materials (core) | https://threejs.org/docs/Material.html |
| PBR | https://threejs.org/docs/MeshStandardMaterial.html |
| Physical | https://threejs.org/docs/MeshPhysicalMaterial.html |
| Custom GLSL | https://threejs.org/docs/ShaderMaterial.html |

## Scope

- **In scope:** Non-Node materials listed under Core **Materials** in docs (except `*NodeMaterial`).
- **Out of scope:** Full Nodes catalog (threejs-node-tsl); post pass materials inside composer (threejs-postprocessing).

## Common pitfalls and best practices

- Wrong normal map `normalMapType` or tangent space breaks lighting; verify geometry has tangents or use appropriate mode.
- Premultiplied alpha vs straight alpha mismatches cause fringe halos on foliage.
- `MeshPhysicalMaterial` `transmission` needs thickness and good env—combine with **threejs-textures** / PMREM.
- Too many unique materials hurts sorting and batching—merge where possible.

## Documentation and version

PBR and `ShaderMaterial` behavior track the [Materials](https://threejs.org/docs/#Materials) section in [three.js docs](https://threejs.org/docs/). Color management and default `envMap` handling changed in modern releases—always pair material answers with renderer/output settings from **threejs-renderers** when colors look wrong.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link `MeshStandardMaterial`, `MeshPhysicalMaterial`, or `ShaderMaterial` pages as appropriate.
2. Force a clear choice vs **threejs-node-tsl** when the user asks for “shaders” or “nodes”.
3. Separate map **roles** (albedo vs roughness vs normal) and `colorSpace` expectations with **threejs-textures**.
4. Call out transparency and `depthWrite` trade-offs for sorted rendering.
5. Note that `*NodeMaterial` types belong to the node skill, not this one.

## References

- https://threejs.org/docs/#Materials
- https://threejs.org/docs/MeshStandardMaterial.html
- https://threejs.org/docs/MeshPhysicalMaterial.html
- https://threejs.org/docs/ShaderMaterial.html

## Keywords

**English:** meshstandardmaterial, meshphysicalmaterial, shadermaterial, pbr, transparency, envmap, materials, three.js

**中文：** 材质、PBR、MeshStandardMaterial、物理材质、透明、环境贴图、ShaderMaterial、three.js

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
