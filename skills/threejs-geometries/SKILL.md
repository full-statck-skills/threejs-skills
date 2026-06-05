---
name: threejs-geometries
description: >-
  three.js geometry authoring: BufferGeometry, typed BufferAttribute and interleaved layouts, InstancedBufferGeometry, primitive Geometries (box/sphere/torus/etc.), ExtrudeGeometry and Shape/Path/Curve from Extras, WireframeGeometry, and addon geometries such as TextGeometry, DecalGeometry, RoundedBoxGeometry.
  Covers merged scope of procedural curves and extrusion formerly split as extras-curves; for animation morph targets see threejs-animation; for merging buffers utilities see official BufferGeometryUtils module in docs Utils addons.
---

## When to use this skill

**ALWAYS use this skill when the user mentions:**

- Building or modifying `BufferGeometry`, attributes, index buffers, draw ranges
- Instancing via `InstancedBufferAttribute` / `InstancedMesh` geometry side (**threejs-objects** for mesh wrapper)
- Extruding `Shape` along paths, `TubeGeometry`, `LatheGeometry`, `ExtrudeGeometry`
- Text or decal addon geometries

**IMPORTANT: geometries vs math**

- **threejs-geometries** = GPU-ready triangle data.
- **threejs-math** = `Box3`, `Sphere`, `Ray` tests without mesh topology.

**Trigger phrases include:**

- "BufferGeometry", "BufferAttribute", "ExtrudeGeometry", "Shape", "Curve"
- "几何体", "缓冲几何", "挤出", "文字几何"

## How to use this skill

1. Prefer built-in primitives when they fit before custom buffers.
2. For custom meshes: create `BufferGeometry`, set `position`, `normal`, `uv`, optional `index`; compute bounding volumes for culling.
3. For instancing attributes, align divisor/count with `InstancedMesh` patterns in **threejs-objects**.
4. For 2D profiles: build `Shape`/`Path`, extrude or lathe per docs; consult Extras **Curve** family for path sampling.
5. For addon NURBS knots, follow Addons **Curves** pages sparingly—cite docs instead of copying full APIs.
6. Dispose geometries when replacing meshes to avoid leaks.

See [examples/workflow-extrude-shape.md](examples/workflow-extrude-shape.md).

## Doc map (official)

| Docs section | Representative links |
|--------------|----------------------|
| Core | https://threejs.org/docs/BufferGeometry.html |
| Geometries | https://threejs.org/docs/BoxGeometry.html |
| Extrude | https://threejs.org/docs/ExtrudeGeometry.html |
| Shape | https://threejs.org/docs/Shape.html |

## Scope

- **In scope:** Core geometries, buffer core, curve/shape/extrusion workflows, selected addon geometries.
- **Out of scope:** Physics collision mesh baking; full CAD import pipelines.

## Common pitfalls and best practices

- Missing normals break lighting; compute or import consistently.
- Wrong winding order flips faces—check side/culling.
- Huge attribute counts need LOD or simplification (modifiers in addons—mention only if user asks).

## Documentation and version

Primitives and `BufferGeometry` live under [Geometries](https://threejs.org/docs/#Geometries) and [BufferGeometry](https://threejs.org/docs/BufferGeometry.html) in [three.js docs](https://threejs.org/docs/). Curve, `Shape`, and extrusion APIs appear under **Extras** and **Geometries**—Addons **Curves** / **Geometries** document NURBS and text meshes; link those instead of copying long signatures.

## Agent response checklist

When answering under this skill, prefer responses that:

1. Link `BufferGeometry`, a primitive, or `ExtrudeGeometry` / `Shape` as appropriate.
2. Point **instancing** usage to **threejs-objects** for `InstancedMesh` patterns.
3. Point morph targets and tracks to **threejs-animation** when deformation is time-driven.
4. Reference `BufferGeometryUtils` (Addons **Utils**) only by name + docs link when merging/splitting.
5. Emphasize `dispose()` when replacing large custom buffers.

## References

- https://threejs.org/docs/#Geometries
- https://threejs.org/docs/BufferGeometry.html
- https://threejs.org/docs/ExtrudeGeometry.html

## Keywords

**English:** buffergeometry, extrude, shape, path, curve, primitives, instancing, three.js

**中文：** 几何体、BufferGeometry、挤出、Shape、曲线、实例化、three.js

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
