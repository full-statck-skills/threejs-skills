---
name: threejs-loaders
description: >-
  three.js asset I/O using LoadingManager, Cache, FileLoader, image and texture loaders, GLTFLoader with DRACOLoader and KTX2Loader, and common format loaders under Addons; symmetric exporters such as GLTFExporter and texture/buffer exporters.
  Use when loading or exporting models, HDR, LUT, fonts, or compressed textures; for runtime Texture object parameters after load use threejs-textures; for scene graph placement use threejs-objects.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- `GLTFLoader`, `DRACOLoader`, `KTX2Loader`, `FBXLoader`, `OBJLoader`, progress and error handling
- `LoadingManager` for global progress, `Cache` for HTTP caching control
- Export: `GLTFExporter`, `OBJExporter`, HDR/KTX2 export pipelines
- IES, UltraHDR, or domain-specific loaders listed under Addons Loaders in docs

**IMPORTANT: loaders vs textures**

- **threejs-loaders** = fetch/decode/parse files into three objects.
- **threejs-textures** = `Texture`/`DataTexture` parameters, sampling, PMREM after you already have image buffers.

**IMPORTANT: loaders vs dev-setup**

- Import path issues belong to **threejs-dev-setup**; this skill assumes imports resolve.

**Trigger phrases include:**

- "GLTFLoader", "DRACO", "KTX2", "LoadingManager", "export gltf"
- "加载模型", "导出", "进度条"

## How to use this skill

1. **Pick loader** by format; prefer glTF for PBR interchange when possible.
2. **Wire LoadingManager** for multi-asset batches; surface `onStart`/`onLoad`/`onProgress`/`onError`.
3. **glTF + Draco**: instantiate `DRACOLoader`, set decoder path, attach to `GLTFLoader.setDRACOLoader` per current docs.
4. **glTF + KTX2**: configure `KTX2Loader` with transcoder path and connect to `GLTFLoader` when using Basis textures.
5. **Export**: use `GLTFExporter` with options matching round-trip needs; note large scenes and binary vs JSON.
6. **Security**: only load user URLs with validation; mention CORS for cross-origin assets.
7. **After load**: traverse scene for materials/meshes—hand off material tuning to **threejs-materials**.

See [examples/workflow-gltf-draco.md](examples/workflow-gltf-draco.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Core Loaders | https://threejs.org/docs/LoadingManager.html |
| Core Loaders | https://threejs.org/docs/GLTFLoader.html |
| Addons Exporters | https://threejs.org/docs/GLTFExporter.html |
| Addons Loaders | https://threejs.org/docs/DRACOLoader.html |

Extended list: [references/official-sections.md](references/official-sections.md).

## Scope

- **In scope:** Loader and exporter classes, manager/cache, format choice, plugin wiring for Draco/KTX2, export basics.
- **Out of scope:** Server-side transcoding pipelines; physics or game engine asset tooling outside three docs.

## Common pitfalls and best practices

- Draco/KTX2 **decoder paths** must match deployed files; broken paths fail silently until onError surfaces.
- Duplicate texture instances after merge—consider `renderer.initTexture` implications when cloning materials.
- Exporters may not round-trip custom shaders; document limitations.
- Always dispose geometries/materials when replacing loaded scenes to avoid GPU leaks.

## Documentation and version

Loader and exporter APIs (especially `GLTFLoader` + `DRACOLoader` / `KTX2Loader` wiring) change between three.js versions. Follow [Loaders](https://threejs.org/docs/#Loaders) and **Addons → Loaders / Exporters** in [three.js docs](https://threejs.org/docs/); decoder WASM paths are deployment-specific, not library-version alone.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link `LoadingManager`, `GLTFLoader`, or the relevant format page on https://threejs.org/docs/.
2. Separate **loading** (this skill) from **texture/material tuning** after decode (**threejs-textures**, **threejs-materials**).
3. Document Draco/KTX2 **decoder path** and CORS when assets fail silently.
4. Mention exporter limitations (custom shaders, extensions) honestly.
5. Encourage `dispose()` when replacing entire loaded scenes.

## References

- https://threejs.org/docs/#Loaders
- https://threejs.org/docs/LoadingManager.html
- https://threejs.org/docs/GLTFLoader.html
- https://threejs.org/docs/GLTFExporter.html

## Keywords

**English:** gltf, gltfloader, dracoloader, ktx2, loadingmanager, cache, exporter, asset pipeline, three.js

**中文：** GLTFLoader、加载器、Draco、KTX2、导出、资源、进度、three.js

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
