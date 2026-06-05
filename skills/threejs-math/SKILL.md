---
name: threejs-math
description: >-
  three.js math library: Vector2/3/4, Matrix3/4, Quaternion, Euler, Color, Box2/Box3, Sphere, Plane, Ray, Line3, Triangle, Frustum, Cylindrical/Spherical coords, MathUtils, and Interpolant base classes; addon math utilities such as OBB, Octree, Capsule, ConvexHull, MeshSurfaceSampler.
  Use for transforms, intersection tests, and spatial queries; for keyframe interpolation tied to AnimationMixer use threejs-animation; for picking implementation use threejs-objects with Raycaster.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- Vector/matrix math order, `applyQuaternion`, `lookAt`, world vs local transforms
- Bounding volumes `Box3`/`Sphere`, containment/intersection tests
- `Ray` vs `Plane` vs `Frustum` tests (without full picking pipeline)

**IMPORTANT: math vs objects vs animation**

| Need | Skill |
|------|--------|
| Raw math types | **threejs-math** |
| `Raycaster` + layers picking | **threejs-objects** |
| QuaternionKeyframeTrack playback | **threejs-animation** |

**Trigger phrases include:**

- "Vector3", "Matrix4", "Quaternion", "Box3", "Ray", "Frustum"
- "向量", "矩阵", "四元数", "包围盒"

## How to use this skill

1. **Conventions**: multiply vectors by matrices on the left as three.js examples show; call `updateMatrixWorld` before world-space queries (**threejs-objects**).
2. **Bounding**: `Box3().setFromObject(object)` for rough bounds; refine per need.
3. **Collision-ish checks**: `ray.intersectBox`, `sphere.containsPoint`, etc., per docs.
4. **Addon structures**: `Octree`/`OBB` for games—cite addon pages, avoid copying full API tables here.
5. **Color**: `Color` conversions relate to materials/textures—cross-link.
6. **Random sampling**: `MeshSurfaceSampler` for distributing points on meshes.

See [examples/workflow-ray-aabb.md](examples/workflow-ray-aabb.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Math | https://threejs.org/docs/Vector3.html |
| Math | https://threejs.org/docs/Matrix4.html |
| Math | https://threejs.org/docs/Quaternion.html |
| Math | https://threejs.org/docs/Ray.html |

## Scope

- **In scope:** Core Math types; addon math entries as pointers.
- **Out of scope:** Keyframe track evaluation beyond type references (animation skill).

## Common pitfalls and best practices

- Euler gimbal lock—prefer quaternions for arbitrary rotations.
- Reusing temporary vectors reduces GC thrash in hot loops.
- Frustum culling helpers vary—verify against your three version.

## Documentation and version

Core math types are listed under [Math](https://threejs.org/docs/#Math); addon utilities (`Octree`, `OBB`, …) appear under **Addons → Math** in [three.js docs](https://threejs.org/docs/). [Global](https://threejs.org/docs/#Global) also lists constants (e.g. wrapping, blending) sometimes needed alongside materials.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link the concrete type (`Vector3`, `Matrix4`, `Quaternion`, …) from the docs.
2. Send `AnimationMixer` / track math to **threejs-animation** when time-sampled.
3. Send `Raycaster` picking flows to **threejs-objects** when interaction is the goal.
4. Mention numeric stability (epsilon) where comparisons matter.
5. Point to **Addons → Math** for game-oriented structures when users need spatial acceleration.

## References

- https://threejs.org/docs/#Math
- https://threejs.org/docs/MathUtils.html
- https://threejs.org/docs/Ray.html

## Keywords

**English:** vector, matrix, quaternion, euler, box3, sphere, ray, frustum, three.js

**中文：** 向量、矩阵、四元数、欧拉角、包围盒、射线、three.js

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
