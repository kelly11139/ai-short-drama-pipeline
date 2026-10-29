# 🎬 AI 短剧全生产流程 · ai-short-drama-pipeline

免费、开源的 AI 短剧一站式生产流水线资源整合。把「**剧本 → 分镜 → 角色 → 生图 → 视频 → 配音 → 对口型 → 成片**」涉及的优质开源项目汇总到一起，并给出可落地的部署清单与选型建议。

> ⚠️ **关于「免费」的实话**：本项目收录的**软件本身全部免费开源**（MIT / Apache-2.0 等协议）。但「模型推理」要么吃你自己的显卡，要么调用云 API（多数有免费额度、量大按量计费）。想「完全免费」跑全链路，最好有一张能跑开源模型的独显（如 RTX 4090 级别）。

---

## 📑 目录
- [两条落地路线](#-两条落地路线)
- [推荐工具清单](#-推荐工具清单)
- [快速开始](#-快速开始)
- [按机器配置的部署清单](#-按机器配置的部署清单)
- [常见问题](#-常见问题)
- [参考与致谢](#-参考与致谢)

---

## 🛤️ 两条落地路线

### 路线 A：一站式开源平台（最省事，推荐先试）
开箱即用，整条流水线已串好，你只需接入模型（本地或 API）。

| 项目 | 仓库 | 说明 |
|---|---|---|
| **AID Studio** | [gzxx-2025/aid-studio](https://github.com/gzxx-2025/aid-studio) | 全开源、自托管（Docker/systemd）。剧本/角色场景/智能分镜/生图/视频/配音/成片预览全覆盖，多模型接入。MIT 协议。 |
| **LumenX Studio** | [alibaba/lumenx](https://github.com/alibaba/lumenx) | 阿里星莲团队出品。小说文本→动态视频，集成 Qwen（剧本分析）+ 通义万相 Wanx（视觉生成），本地优先。MIT 协议。 |

> 这两个平台软件免费，但首次使用需在管理后台配置模型供应商的 API Key（或本地模型）。模型调用、服务器、存储可能产生费用。

### 路线 B：ComfyUI 自建（控制力最强，折腾多）
适合想完全掌控每一步、接入任意开源模型的进阶玩家。
- **编排核心**：[ComfyUI](https://github.com/comfyanonymous/ComfyUI)（节点式，免费，几乎所有开源视频/图像模型都能接）
- **剧本/分镜**：任意 LLM（Qwen 本地版或免费 API）
- **角色一致性**：Flux + [IP-Adapter](https://github.com/tencent-ailab/IP-Adapter) / [PuLID](https://github.com/ToTheBeginning/PuLID) / [InstantID](https://github.com/InstantID/InstantID)
- **视频生成（开源权重免费）**：[Wan2.2](https://github.com/Wan-Video/Wan2.2)（阿里，5B 可在 4090 跑 720P）、[HunyuanVideo](https://github.com/Tencent/HunyuanVideo)（腾讯）、[LTX-Video](https://github.com/Lightricks/LTX-Video)、[CogVideoX](https://github.com/THUDM/CogVideo)、[Mochi](https://github.com/genmoai/mochi)
- **配音 TTS**：[CosyVoice](https://github.com/FunAudioLLM/CosyVoice)、[GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS)、[ChatTTS](https://github.com/2noise/ChatTTS)、[Fish Speech](https://github.com/fishaudio/fish-speech)
- **对口型**：[Wan2.2-Animate](https://github.com/Wan-Video/Wan2.2)、[MuseTalk](https://github.com/TMElyralab/MuseTalk)、[LivePortrait](https://github.com/PhyAU/LivePortrait)、[Wav2Lip](https://github.com/Rudrabha/Wav2Lip)
- **合成**：[ffmpeg](https://ffmpeg.org/)

---

## 🧰 推荐工具清单
完整分类、协议、适用场景见 [docs/tools-catalog.md](docs/tools-catalog.md)。

---

## 🚀 快速开始

### 想最快出片（无 GPU / 有 API 额度）
1. 选 **路线 A** 的 AID Studio 或 LumenX Studio，按各自 README 用 Docker / 一键脚本部署。
2. 在管理后台填入模型 API Key（如阿里云 DashScope、MiniMax 等，多数有免费额度）。
3. 新建项目 → 粘贴剧本 → 自动分镜 → 生图 → 视频 → 配音 → 成片预览。

### 想完全本地跑（有 4090 级独显）
1. 部署 **ComfyUI**，加载 Wan2.2 5B / HunyuanVideo 等模型权重。
2. 用 LLM 生成剧本与分镜（可本地 Qwen）。
3. 用 IP-Adapter/PuLID 锁定角色一致性。
4. 逐镜生视频 → CosyVoice/GPT-SoVITS 配音 → MuseTalk/LivePortrait 对口型 → ffmpeg 合成。

---

## 🖥️ 按机器配置的部署清单
详见 [docs/deploy-guide.md](docs/deploy-guide.md)。简要：
- **有 RTX 4090 级独显**：本地 Wan2.2 5B（720P）+ CosyVoice，几乎零持续成本。
- **有中端独显（如 3060 12G）**：跑小模型（LTX-Video、Wan2.2 1.3B）或量化版，质量换速度。
- **无独显**：路线 A 平台 + 云 API 免费额度起步，量大再付费。
- **纯 CPU / 笔记本**：不建议本地跑视频模型，走云端 API 最现实。

---

## ❓ 常见问题
- **真的完全免费吗？** 软件免费；本地跑吃电费和显卡，云端跑吃 API 费用。令牌/Key 自己保管。
- **跨镜头角色一致性怎么解决？** 固定角色参考图 + IP-Adapter/PuLID + 固定 seed；平台类（LumenX）已内置三视图资产锁定。
- **GitHub 上的 fork 很多（如 aid-studio），以哪个为准？** 优先官方源：AID Studio 以 `gzxx-2025/aid-studio` 为准，LumenX 以 `alibaba/lumenx` 为准。

---

## 🔗 参考与致谢
- 一站式平台：[AID Studio](https://github.com/gzxx-2025/aid-studio)、[LumenX Studio](https://github.com/alibaba/lumenx)
- 编排与模型：[ComfyUI](https://github.com/comfyanonymous/ComfyUI)、[Wan2.2](https://github.com/Wan-Video/Wan2.2)、[HunyuanVideo](https://github.com/Tencent/HunyuanVideo)
- 语音与口型：[CosyVoice](https://github.com/FunAudioLLM/CosyVoice)、[GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS)、[MuseTalk](https://github.com/TMElyralab/MuseTalk)、[LivePortrait](https://github.com/PhyAU/LivePortrait)

> 本仓库为资源整合与选型指南，所有项目版权归各自作者所有，请遵循其开源协议使用。

---
*由 WorkBuddy 借助 GitHub MCP 协助整理生成。*
