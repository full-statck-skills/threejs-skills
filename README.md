<div align="center">

# threejs-skills

**Three.js 3D graphics skills — scenes, camera, lights, materials, geometries, animation, WebXR**

[![GitHub](https://img.shields.io/badge/github-full--statck--skills%2Fthreejs-skills-green.svg)](https://github.com/full-statck-skills/threejs-skills)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Compatible-purple.svg)](https://agentskills.io)

English | [简体中文](./README.zh-CN.md)

[Introduction](#-introduction) ·
[Install](#-install) ·
[Skills](#-skills) ·
[Supported Agents](#-supported-agents) ·
[Ecosystem](#-ecosystem)

</div>

---

## 📖 Introduction

**Three.js Skills** is a curated collection of Agent Skills for AI coding agents, part of the [Full Stack Skills](https://github.com/partme-ai/full-stack-skills) ecosystem maintained by [PartMe.AI](https://github.com/partme-ai).

This package includes **18 skills** providing specialized knowledge, workflows, and references for building 3D applications with Three.js. Each skill is a self-contained `SKILL.md` file loaded on-demand by AI agents.

## 📦 Install

```bash
npx skills add full-statck-skills/threejs-skills
```

Or install specific skills:

```bash
npx skills add full-statck-skills/threejs-skills --skill <skill-name>
```

## 🎯 Skills (18)

| Skill | Description |
|-------|-------------|
| `threejs-animation` | >- |
| `threejs-audio` | >- |
| `threejs-camera` | >- |
| `threejs-controls` | >- |
| `threejs-dev-setup` | >- |
| `threejs-geometries` | >- |
| `threejs-helpers` | >- |
| `threejs-lights` | >- |
| `threejs-loaders` | >- |
| `threejs-materials` | >- |
| `threejs-math` | >- |
| `threejs-node-tsl` | >- |
| `threejs-objects` | >- |
| `threejs-postprocessing` | >- |
| `threejs-renderers` | >- |
| `threejs-scenes` | >- |
| `threejs-textures` | >- |
| `threejs-webxr` | >- |

## 🤖 Supported Agents

Works with [Claude Code](https://code.claude.com), [Codex](https://developers.openai.com/codex), [Cursor](https://cursor.com), [OpenCode](https://opencode.ai), [Gemini CLI](https://geminicli.com), [GitHub Copilot](https://github.com/features/copilot), [Windsurf](https://codeium.com/windsurf), and [70+ others](https://agentskills.io/clients).

### Claude Code Installation

**Option 1: npx skills CLI (Recommended)**

```bash
npx skills add full-statck-skills/threejs-skills
```

**Option 2: Manual Installation**

```bash
git clone https://github.com/full-statck-skills/threejs-skills.git
cp -r threejs-skills/skills/* .claude/skills/
```

For more details, see the [Claude Code Skills Guide](https://code.claude.com/docs/en/skills) and [Agent Skills Spec](https://agentskills.io/).

## 🌐 Ecosystem

| Resource | Link |
|----------|------|
| **Full Stack Skills** | [github.com/partme-ai/full-stack-skills](https://github.com/partme-ai/full-stack-skills) |
| **All Skill Groups** | [github.com/full-statck-skills](https://github.com/full-statck-skills) |
| **Agent Skills Spec** | [agentskills.io](https://agentskills.io) |
| **Skills CLI** | [github.com/vercel-labs/skills](https://github.com/vercel-labs/skills) |

## 📄 License

Apache 2.0 — see [LICENSE](LICENSE).
