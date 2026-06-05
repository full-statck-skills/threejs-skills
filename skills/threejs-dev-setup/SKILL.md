---
name: threejs-dev-setup
description: >-
  Bootstrap and toolchain guidance for three.js applications using npm, Vite/Webpack/Rollup, bare ESM import maps, and TypeScript.
  Covers canonical import paths for `three` core versus `three/addons/` (examples/jsm re-exports), version alignment with https://threejs.org/docs/, and fixing "module not found" for loaders and controls.
  Use when scaffolding a new 3D project, migrating bundler, or debugging resolution of addons—do not use for rendering API details (see threejs-renderers) or asset loading logic (see threejs-loaders).
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- Creating or configuring a new three.js project, Vite/Webpack/Rollup entry, or browser `importmap`
- Installing the `three` package, aligning version with documentation, or TypeScript setup (`@types/three` where applicable)
- Import errors for `three/addons/...`, `examples/jsm`, ESM vs CJS interop, or bare specifier resolution

**IMPORTANT: this skill vs runtime topics**

- **threejs-dev-setup** = install paths, bundler, module graph, and where to import addons from.
- **threejs-renderers** = `WebGLRenderer` / `WebGPURenderer`, canvas, pixel ratio, render loop—after the project loads.
- **threejs-loaders** = `GLTFLoader`, `DRACOLoader`, progress callbacks—after imports resolve.

**Trigger phrases include:**

- "vite three.js", "webpack three", "import map", "three/addons", "cannot find module", "jsm"
- "新建项目", "安装 three", "找不到模块", "ESM", "TypeScript three"

## How to use this skill

1. **Confirm delivery model**: SPA bundler (Vite/Webpack), Node tooling, or static HTML with `importmap`—each affects how `three/addons/` resolves.
2. **Pin `three` version** to a release compatible with the docs the user cites; note that addon paths follow the published package layout.
3. **Show canonical imports**: core from `three`; controls/loaders/effects from `three/addons/...` (mapped to `examples/jsm` in source tree). See [examples/workflow-scaffold.md](examples/workflow-scaffold.md).
4. **Minimal loop**: create renderer + scene + camera + one mesh; `requestAnimationFrame`—enough to verify toolchain without duplicating threejs-renderers depth.
5. **TypeScript**: enable `moduleResolution` appropriate for bundler; reference types from `three` package typings; avoid duplicating global script tag patterns unless user targets no-bundler HTML.
6. **On failure**: distinguish missing dependency vs wrong path vs SSR context (no `window`/`document`).
7. **Deepening**: link user to [three.js manual](https://threejs.org/manual/) first chapter after scaffold works.

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Manual (getting started) | https://threejs.org/manual/ |
| Docs index | https://threejs.org/docs/ |
| Package / install context | https://www.npmjs.com/package/three |

## Scope

- **In scope:** npm/install, bundlers, import maps, TypeScript basics for three, addon import paths, minimal verification snippet.
- **Out of scope:** WebGL theory, full render target or post stack (threejs-renderers, threejs-postprocessing), physics, deployment beyond "build runs".

## Common pitfalls and best practices

- Mixing multiple `three` copies in one page breaks singletons; dedupe with bundler aliases.
- Importing addons from deep `node_modules/.../examples/jsm` paths is fragile; prefer package exports `three/addons/...` when available.
- Always match **r152+** style color management docs when giving snippet defaults (output color space)—point to threejs-renderers/textures for details.
- SSR frameworks need dynamic import or client-only components for WebGL context.

## Documentation and version

Toolchain and import paths follow the **three** npm package version the user installs. The [Manual](https://threejs.org/manual/) and [docs](https://threejs.org/docs/) are updated with the library; addon paths (`three/addons/...`) must match the package layout for that release—when in doubt, cite the version number and the exact import line from the current docs.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Name the bundler or runtime (Vite, Webpack, bare ESM, `importmap`) and the intended `three` version.
2. Link https://threejs.org/manual/ and/or https://threejs.org/docs/ for authoritative setup context.
3. Distinguish **threejs-dev-setup** (resolution) from **threejs-renderers** (runtime API) failures.
4. Never assume global script tags unless the user explicitly uses CDN/no-bundler HTML.
5. Recommend deduplicating `three` in `package.json` / lockfile when duplicate singleton issues appear.

## References

- https://threejs.org/manual/
- https://threejs.org/docs/
- https://www.npmjs.com/package/three

## Keywords

**English:** three.js, vite, webpack, rollup, import map, typescript, npm, three/addons, examples jsm, module resolution, scaffold

**中文：** three.js 安装、构建、importmap、模块解析、three/addons、脚手架、Vite、Webpack

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
