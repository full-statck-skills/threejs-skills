---
name: threejs-animation
description: >-
  three.js keyframe animation system: AnimationMixer, AnimationClip, AnimationAction, KeyframeTrack variants, PropertyBinding, PropertyMixer, AnimationObjectGroup, AnimationUtils; mixing and crossfading clips, loop modes, timeScale, weight; addon AnimationClipCreator and CCDIKSolver for procedural rigs.
  Use when playing glTF clips, blending actions, or authoring procedural tracks; for skin deformation rigging on meshes see threejs-objects; for math interpolants without clips see threejs-math only when not tied to AnimationMixer.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- `AnimationMixer.update`, `AnimationAction` play/pause/stop, crossfade, synchronized clips
- `AnimationClip` from glTF or `AnimationClipCreator`, retargeting caveats at API level
- Keyframe tracks: position/rotation/scale/color tracks, boolean/string tracks where applicable
- IK: `CCDIKSolver` / `CCDIKHelper` from addons

**IMPORTANT: animation vs objects**

- **threejs-animation** = time evaluation and tracks.
- **threejs-objects** = `SkinnedMesh`/`Skeleton` attachment, bind pose—mesh side.

**Trigger phrases include:**

- "AnimationMixer", "AnimationAction", "AnimationClip", "crossFade", "KeyframeTrack"
- "动画混合", "骨骼动画", "剪辑", "淡入淡出"

## How to use this skill

1. **Collect clips** from `gltf.animations` or create with utilities / `AnimationClipCreator`.
2. **Create mixer** bound to root object (often `scene` or rig root).
3. **Create actions** per clip via `mixer.clipAction(clip)`; configure loop mode (`LoopOnce`, `LoopRepeat`, `LoopPingPong`).
4. **Per frame**: compute delta seconds (use `Clock` from core—documented under Core in docs index), call `mixer.update(delta)`.
5. **Blending**: adjust `weight`, `crossFadeTo`, `enabled` flags; watch for additive vs full replacement semantics per docs.
6. **PropertyBinding**: understand path strings targeting bones/morphs—errors often from wrong object names.
7. **IK addon**: attach solver after base animation if using CCD IK from examples.

See [examples/workflow-mixer-action.md](examples/workflow-mixer-action.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Animation (index) | https://threejs.org/docs/#Animation |
| Action | https://threejs.org/docs/AnimationAction.html |
| Mixer | https://threejs.org/docs/AnimationMixer.html |
| Clip | https://threejs.org/docs/AnimationClip.html |
| Tracks | https://threejs.org/docs/KeyframeTrack.html |

More: [references/official-sections.md](references/official-sections.md).

## Scope

- **In scope:** Core Animation module, keyframe pipeline, listed addons for clip creation and IK.
- **Out of scope:** DCC export best practices; physics ragdoll; audio sync (link conceptually only).

## Common pitfalls and best practices

- Forgetting `mixer.update` freezes animation; double `update` per frame speeds up.
- Mixing clips with incompatible hierarchies causes violent pops—validate bind pose.
- Root motion must be handled in game logic if not baked—document explicitly.
- Large track counts cost CPU—strip unused tracks in preprocessing when possible.

## Documentation and version

Behavior of `AnimationMixer`, tracks, and glTF animation import can change between three.js majors. Treat the [Animation](https://threejs.org/docs/#Animation) section of the [docs index](https://threejs.org/docs/) as authoritative for the user’s installed version; when upgrading, check the three.js repository release notes and migration notes for renamed properties or loader output.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Cite the exact class (`AnimationMixer`, `AnimationAction`, etc.) or addon (`CCDIKSolver`) from the official docs.
2. Include at least one `https://threejs.org/docs/...` link (e.g. [AnimationAction](https://threejs.org/docs/AnimationAction.html)).
3. Relate clips to `SkinnedMesh` / skeleton via **threejs-objects** when deformation is involved.
4. Mention `mixer.update(delta)` and a stable time source (`Clock`) explicitly.
5. Reference official **examples** by name only (no full file paste).

## References

- https://threejs.org/docs/#Animation
- https://threejs.org/docs/AnimationMixer.html
- https://threejs.org/docs/AnimationAction.html
- https://threejs.org/docs/PropertyBinding.html

## Keywords

**English:** animationmixer, animationaction, animationclip, keyframetrack, crossfade, skinning, propertybinding, three.js

**中文：** 动画混合、AnimationMixer、AnimationAction、关键帧、骨骼动画、剪辑、淡入淡出、three.js

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
