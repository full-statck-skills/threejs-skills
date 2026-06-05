---
name: threejs-audio
description: >-
  three.js audio spatialization: AudioListener attached to camera rig, Audio and PositionalAudio sources, AudioAnalyser for FFT/time-domain data, and integration with Web Audio API contexts; AudioLoader is referenced from threejs-loaders for file decoding.
  Use when placing 3D sound, configuring panner parameters, or visualization; not a replacement for full game audio middleware.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- `AudioListener` on `Camera`, `Audio` vs `PositionalAudio`, distance models, refDistance/maxDistance/rolloff
- `AudioAnalyser` for visualization bars/spectrum
- Browser autoplay policies blocking audio start

**IMPORTANT: audio vs loaders**

| Step | Skill |
|------|--------|
| Decode mp3/ogg buffer | **threejs-loaders** (`AudioLoader`) |
| Spatial playback API | **threejs-audio** |

**Trigger phrases include:**

- "PositionalAudio", "AudioListener", "AudioAnalyser", "panner"
- "空间音频", "音量衰减", "频谱"

## How to use this skill

1. **Attach listener** to camera object so head-related audio follows view.
2. **Create context** compatible with user gesture unlock patterns in browsers.
3. **PositionalAudio**: set `refDistance`, `maxDistance`, `rolloffFactor`, `distanceModel` per docs.
4. **Load buffer** via `AudioLoader` (**threejs-loaders**), then `positionalAudio.setBuffer`.
5. **Analyser**: connect graph `listener.context.createAnalyser()` pathways per examples; watch performance.
6. **Update**: audio nodes usually need no per-frame update unless following moving sources manually.

See [examples/workflow-positional-audio.md](examples/workflow-positional-audio.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Audio | https://threejs.org/docs/AudioListener.html |
| Audio | https://threejs.org/docs/Audio.html |
| Audio | https://threejs.org/docs/PositionalAudio.html |
| Audio | https://threejs.org/docs/AudioAnalyser.html |

Extended list: [references/official-sections.md](references/official-sections.md).

## Scope

- **In scope:** Core Audio classes, spatialization parameters, analyser usage overview.
- **Out of scope:** FMOD/Wwise-style authoring tools.

## Common pitfalls and best practices

- Autoplay restrictions require user interaction to resume AudioContext.
- Too many positional sources hurt CPU—pool or LOD audio.
- Ensure world units match distance model expectations.

## Documentation and version

Audio classes are under [Audio](https://threejs.org/docs/#Audio) in [three.js docs](https://threejs.org/docs/). Decoding buffers uses `AudioLoader`—see **threejs-loaders**. Browser Web Audio policies are external but must be mentioned when `AudioContext` is suspended.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link `AudioListener`, `PositionalAudio`, or `AudioAnalyser` as relevant.
2. Delegate file loading of sound buffers to **threejs-loaders** (`AudioLoader`).
3. Note autoplay / user-gesture requirements for resuming context.
4. Relate distance attenuation to world units and **threejs-objects** placement.
5. Avoid promising DAW-level mixing—stay within three.js audio scope.

## References

- https://threejs.org/docs/#Audio
- https://threejs.org/docs/AudioListener.html
- https://threejs.org/docs/PositionalAudio.html

## Keywords

**English:** audio, positional audio, listener, analyser, spatial sound, web audio, three.js

**中文：** 音频、空间音频、AudioListener、PositionalAudio、Web Audio、three.js

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
