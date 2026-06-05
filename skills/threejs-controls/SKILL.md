---
name: threejs-controls
description: >-
  Addon camera and object manipulation controls: OrbitControls, MapControls, FlyControls, FirstPersonControls, TrackballControls, ArcballControls, DragControls, PointerLockControls, TransformControls; damping, target focal point, and integration with the animation loop.
  Use for editor-style navigation and gizmos—not a full game character controller stack; pair with Raycaster selection patterns in threejs-objects when transforming selections.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- Orbiting/panning/dolly around a target, inertia/damping, min/max distance/polar angles
- Map-like pan (MapControls) or flying (FlyControls)
- Transform gizmo translate/rotate/scale with `TransformControls`
- Dragging objects in plane (DragControls), pointer lock FPS (PointerLockControls)

**IMPORTANT: controls vs webxr**

| Context | Skill |
|---------|--------|
| Desktop/browser camera nav | **threejs-controls** |
| XR controller poses | **threejs-webxr** |

**Trigger phrases include:**

- "OrbitControls", "TransformControls", "MapControls", "PointerLockControls"
- "轨道", "变换控制器", "漫游"

## How to use this skill

1. **Import** from addons path (**threejs-dev-setup**).
2. **Construct** with `(camera, domElement)`; for `TransformControls` also attach to renderer events.
3. **Animation loop**: when `enableDamping`, call `controls.update()` each frame.
4. **TransformControls**: wire `dragging-changed` to disable Orbit temporarily; sync with selection from **threejs-objects**.
5. **Constraints**: set min/max distance/angles to avoid flipping or underground views.
6. **Dispose**: `controls.dispose()` when tearing down.

See [examples/workflow-orbit-damping.md](examples/workflow-orbit-damping.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Controls | https://threejs.org/docs/OrbitControls.html |
| Controls | https://threejs.org/docs/TransformControls.html |
| Controls | https://threejs.org/docs/MapControls.html |
| Controls (index) | https://threejs.org/docs/#Controls |

## Scope

- **In scope:** Official addons controls usage patterns.
- **Out of scope:** Full physics character motor; mobile gesture frameworks.

## Common pitfalls and best practices

- Forgetting `update()` with damping enabled causes drift never settling.
- TransformControls fighting with Orbit—pause one while using the other.
- Pointer lock requires user gesture and exit handling.

## Documentation and version

Controls are under [Controls](https://threejs.org/docs/#Controls) (Addons) in [three.js docs](https://threejs.org/docs/). API details (`enableDamping`, events) evolve—link `OrbitControls` / `TransformControls` pages for the user’s three.js version.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link the specific controls class from the docs.
2. State `controls.update()` when damping is on, every frame.
3. Coordinate `TransformControls` with selection / **threejs-objects** raycasting.
4. Separate desktop navigation from **threejs-webxr** locomotion.
5. Call `dispose()` on controls when unmounting canvas.

## References

- https://threejs.org/docs/#Controls
- https://threejs.org/docs/OrbitControls.html
- https://threejs.org/docs/TransformControls.html

## Keywords

**English:** orbitcontrols, transformcontrols, mapcontrols, damping, camera controls, three.js

**中文：** OrbitControls、轨道、TransformControls、变换控制器、阻尼、three.js

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
