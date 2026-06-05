---
name: threejs-textures
description: >-
  three.js textures: Texture, DataTexture, CubeTexture, CompressedTexture variants, DepthTexture, VideoTexture, CanvasTexture, 3D/array textures, Source; sampling parameters, mipmaps, anisotropy, wrap/mag/min filters; PMREMGenerator in Extras for environment map prefiltering.
  Use when configuring GPU texture objects and PMREM; for Draco/KTX2 transcoder file paths use threejs-loaders; for material map slots use threejs-materials; for output color pipeline use threejs-renderers.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- `texture.wrapS` / `wrapT`, `minFilter`, `magFilter`, `generateMipmaps`, `anisotropy`
- `colorSpace` / correct handling of sRGB vs linear data maps
- Creating `DataTexture`, `CubeTexture`, compressed GPU formats, video/canvas driven textures
- `PMREMGenerator` from environment maps for IBL

**IMPORTANT: textures vs loaders**

| Step | Skill |
|------|--------|
| Decode file / HTTP | **threejs-loaders** |
| Configure GPU `Texture` | **threejs-textures** |

**Trigger phrases include:**

- "Texture", "CubeTexture", "PMREM", "colorSpace", "mipmap", "各向异性"
- "环境贴图", "数据纹理", "压缩纹理"

## How to use this skill

1. **Classify** texture dimensionality and format (2D, cube, depth, compressed, data).
2. **Color pipeline**: set `colorSpace` appropriately; normal/roughness maps are non-color data.
3. **Sampling**: choose filters; enable mipmaps when minification occurs; consider max anisotropy.
4. **PMREM**: feed env map through `PMREMGenerator` per docs; assign result to scene/env/intensity paths as required.
5. **Video/canvas**: understand update needs each frame for `VideoTexture` / `CanvasTexture`.
6. **Disposal**: `dispose()` textures when replacing to free GPU memory.
7. **KTX2/Basis**: transcoder wiring belongs in **threejs-loaders** before this step.

See [examples/workflow-pmrem-env.md](examples/workflow-pmrem-env.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Textures | https://threejs.org/docs/Texture.html |
| Cube | https://threejs.org/docs/CubeTexture.html |
| Data | https://threejs.org/docs/DataTexture.html |
| PMREM | https://threejs.org/docs/PMREMGenerator.html |

## Scope

- **In scope:** Core Textures + PMREMGenerator; sampling and color pipeline at texture level.
- **Out of scope:** Loader configuration; post-processing passes that sample buffers (threejs-postprocessing).

## Common pitfalls and best practices

- sRGB albedo in linear workflow without proper colorSpace looks wrong next to renderer output.
- Non-power-of-two textures have mip/wrap limitations unless padded.
- Forgetting texture disposal on hot reload leaks VRAM.

## Documentation and version

Texture classes and `PMREMGenerator` are documented under [Textures](https://threejs.org/docs/#Textures) and [PMREMGenerator](https://threejs.org/docs/PMREMGenerator.html) in [three.js docs](https://threejs.org/docs/). Compressed and KTX2 paths often depend on **threejs-loaders** for transcoder setup before this skill applies.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link `Texture`, `DataTexture`, `CubeTexture`, or `PMREMGenerator` as appropriate.
2. Tie `colorSpace` / filtering to **threejs-renderers** output and **threejs-materials** maps.
3. Send Draco/KTX2 **decoder wiring** questions to **threejs-loaders** first.
4. Emphasize `dispose()` when replacing env maps or large atlases.
5. Mention [Global](https://threejs.org/docs/#Global) constants only when wrapping/filter enums matter.

## References

- https://threejs.org/docs/#Textures
- https://threejs.org/docs/Texture.html
- https://threejs.org/docs/PMREMGenerator.html

## Keywords

**English:** texture, cubemap, pmrem, mipmap, colorspace, compressed texture, data texture, three.js

**中文：** 纹理、立方体贴图、PMREM、mipmap、色彩空间、压缩纹理、three.js

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
