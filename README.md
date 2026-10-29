# 🎬 AI 短剧全生产流程 · ai-short-drama-pipeline

免费、开源的 AI 短剧一站式生产流水线资源整合。把「**剧本 → 分镜 → 角色 → 生图 → 视频 → 配音 → 对口型 → 成片**」涉及的优质开源项目汇总到一起，并给出可落地的部署清单与选型建议。

> ⚠️ **关于「免费」的实话**：本项目收录的**软件本身全部免费开源**（MIT / Apache-2.0 等协议）。但「模型推理」要么吃你自己的显卡，要么调用云 API（多数有免费额度、量大按量计费）。想「完全免费」跑全链路，最好有一张能跑开源模型的独显（如 RTX 4090 级别）。

> 🆕 **本仓库持续更新**（最后更新 2026-10-29）：已收录 2026 年爆火的 **Toonflow**（三层 Agent 架构、19k★）、**awesome-short-drama-skills**（短剧 Skill 精选库），并刷新了视频模型对比数据。

---

## 📑 目录
- [两条落地路线](#-两条落地路线)
- [2026 生态新发现](#-2026-生态新发现)
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
| **AID Studio** | [gzxx-2025/aid-studio](https://github.com/gzxx-2025/aid-studio) | 全开源、自托管（Docker/systemd，仅 Linux）。剧本/角色场景/智能分镜/生图/视频/配音/成片预览全覆盖，多模型接入。MIT 协议。最低 2 核 4G 可跑。 |
| **LumenX Studio** | [alibaba/lumenx](https://github.com/alibaba/lumenx) | 阿里星莲团队出品。小说文本→动态视频，集成 Qwen（剧本分析）+ 通义万相 Wanx（视觉生成），本地优先。MIT 协议。 |
| **Toonflow** | [HBAI-Ltd/Toonflow-app](https://github.com/HBAI-Ltd/Toonflow-app) | 🆕 2026 年爆火（19k★，MIT）。三层 Agent 架构（事件图谱抽取→剧本改编分镜→画面/视频生成），无限画布 + 可视化工作流，支持本地部署、自选模型、MCP/插件扩展。 |

> 这三个平台软件免费，但首次使用需在管理后台配置模型供应商的 API Key（或本地模型）。模型调用、服务器、存储可能产生费用。

### 路线 B：ComfyUI 自建（控制力最强，折腾多）
适合想完全掌控每一步、接入任意开源模型的进阶玩家。
- **编排核心**：[ComfyUI](https://github.com/comfyanonymous/ComfyUI)（节点式，免费，几乎所有开源视频/图像模型都能接）
- **剧本/分镜**：任意 LLM（Qwen 本地版或免费 API）
- **角色一致性**：Flux + [IP-Adapter](https://github.com/tencent-ailab/IP-Adapter) / [PuLID](https://github.com/ToTheBeginning/PuLID) / [InstantID](https://github.com/InstantID/InstantID)
- **视频生成（开源权重免费）**：[Wan2.2](https://github.com/Wan-Video/Wan2.2)（阿里，Apache-2.0，5B 可在 4090 跑 720P）、[HunyuanVideo](https://github.com/Tencent/HunyuanVideo)（腾讯）、[LTX-Video](https://github.com/Lightricks/LTX-Video)（原生音视频联合生成）、[CogVideoX](https://github.com/THUDM/CogVideo)、[Mochi](https://github.com/genmoai/mochi)、[SkyReels-V2](https://github.com/SkyworkAI/SkyReels-V2)
- **配音 TTS**：[CosyVoice](https://github.com/FunAudioLLM/CosyVoice)、[GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS)、[Index-TTS](https://github.com/index-tts/index-tts)、[ChatTTS](https://github.com/2noise/ChatTTS)、[Fish Speech](https://github.com/fishaudio/fish-speech)
- **对口型**：[Wan2.2-Animate](https://github.com/Wan-Video/Wan2.2)、[MuseTalk](https://github.com/TMElyralab/MuseTalk)、[LivePortrait](https://github.com/PhyAU/LivePortrait)、[Wav2Lip](https://github.com/Rudrabha/Wav2Lip)
- **合成**：[ffmpeg](https://ffmpeg.org/)

---

## 🆕 2026 生态新发现

### 🤖 awesome-short-drama-skills（短剧 Skill 精选库）
[UnderleveledBuilder/awesome-short-drama-skills](https://github.com/UnderleveledBuilder/awesome-short-drama-skills) —— 一个**汇总数十个 AI 短剧/漫剧 Skill（技能包）**的清单仓库，覆盖剧本、改编、分镜、Seedance/可灵/MiniMax 视频提示词。这些 Skill 可在千问、豆包、WorkBuddy、Claude Code、Codex 等智能体里直接调用，**不用自己搭平台，让 Agent 帮你写剧本拆分镜**。精选：
- `infinite-creation`（★116）：本地 ComfyUI + MiniMax H3 + Agent 自动连续生产视频，不限时长
- `ai-film-skills`（★85）：21 个独立模块（分镜导演、角色资产、国风/科幻视觉风格、3D 预演）
- `ai-short-drama`（★71）：题材调研、故事架构、镜头时间线、连续性校验
- `novel-to-manju`（★63）：小说转漫剧全流程（爆款改文→剧本→三视图→分镜→视频提示词）
- `muse-video-skill`（★46）：虚拟剧组六角色（导演/编剧/摄影/美术/特效/声音）协作
- `Dramake` / `雪风爽剧` 等：文字转短剧、Seedance 2.0 提示词

### 🏭 Toonflow 为什么值得关注
Toonflow 用**三层 Agent 架构**打通「小说→视频」全链路：① 事件图谱抽取（理解故事）；② 剧本改编与分镜（怎么拍）；③ 画面生成与视频转化（用 SDXL/SVD 等）。它通过**角色卡（Character Card）机制**固化角色外貌，解决跨镜头一致性难题。适合想「小说一键转短剧」且愿意本地部署的人。

---

## 🧰 推荐工具清单
完整分类、协议、适用场景、2026 最新模型对比见 [docs/tools-catalog.md](docs/tools-catalog.md)。

---

## 🚀 快速开始

### 想最快出片（无 GPU / 有 API 额度）
1. 选 **路线 A** 的 AID Studio / LumenX / Toonflow，按各自 README 用 Docker / 一键脚本部署。
2. 在管理后台填入模型 API Key（如阿里云 DashScope、MiniMax 等，多数有免费额度）。
3. 新建项目 → 粘贴剧本 → 自动分镜 → 生图 → 视频 → 配音 → 成片预览。
4. **或者更轻量**：直接用 `awesome-short-drama-skills` 里的 Skill，让 Agent（如 WorkBuddy）帮你写剧本+分镜，再接一个视频模型出片。

### 想完全本地跑（有 4090 级独显）
1. 部署 **ComfyUI**，加载 Wan2.2 5B / HunyuanVideo 等模型权重。
2. 用 LLM 生成剧本与分镜（可本地 Qwen）。
3. 用 IP-Adapter/PuLID 锁定角色一致性。
4. 逐镜生视频 → CosyVoice/GPT-SoVITS/Index-TTS 配音 → MuseTalk/LivePortrait 对口型 → ffmpeg 合成。

---

## 🖥️ 按机器配置的部署清单
详见 [docs/deploy-guide.md](docs/deploy-guide.md)。简要：
- **有 RTX 4090 级独显**：本地 Wan2.2 5B（720P）+ CosyVoice，几乎零持续成本。
- **有中端独显（如 3060 12G）**：跑小模型（LTX-Video、Wan2.2 1.3B、CogVideoX 5B）或量化版，质量换速度。
- **无独显**：路线 A 平台 + 云 API 免费额度起步，量大再付费；或纯用 Skill + 云端视频 API。
- **纯 CPU / 笔记本**：不建议本地跑视频模型，走云端 API 最现实。

---

## ❓ 常见问题
- **真的完全免费吗？** 软件免费；本地跑吃电费和显卡，云端跑吃 API 费用。令牌/Key 自己保管。
- **跨镜头角色一致性怎么解决？** 固定角色参考图 + IP-Adapter/PuLID + 固定 seed；平台类（LumenX/Toonflow）已内置三视图资产锁定。
- **GitHub 上的 fork 很多（如 aid-studio、Toonflow-app），以哪个为准？** 优先官方源：AID Studio 以 `gzxx-2025/aid-studio` 为准，Toonflow 以 `HBAI-Ltd/Toonflow-app` 为准，LumenX 以 `alibaba/lumenx` 为准。
- **不想搭平台，只想让 AI 帮我写剧本分镜？** 用 `awesome-short-drama-skills` 里的 Skill 包，配合任意支持 Skill 的智能体即可。

---

## 🔗 参考与致谢
- 一站式平台：[AID Studio](https://github.com/gzxx-2025/aid-studio)、[LumenX Studio](https://github.com/alibaba/lumenx)、[Toonflow](https://github.com/HBAI-Ltd/Toonflow-app)
- 技能包精选：[awesome-short-drama-skills](https://github.com/UnderleveledBuilder/awesome-short-drama-skills)
- 编排与模型：[ComfyUI](https://github.com/comfyanonymous/ComfyUI)、[Wan2.2](https://github.com/Wan-Video/Wan2.2)、[HunyuanVideo](https://github.com/Tencent/HunyuanVideo)、[LTX-Video](https://github.com/Lightricks/LTX-Video)、[SkyReels-V2](https://github.com/SkyworkAI/SkyReels-V2)
- 语音与口型：[CosyVoice](https://github.com/FunAudioLLM/CosyVoice)、[GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS)、[Index-TTS](https://github.com/index-tts/index-tts)、[MuseTalk](https://github.com/TMElyralab/MuseTalk)、[LivePortrait](https://github.com/PhyAU/LivePortrait)

> 本仓库为资源整合与选型指南，所有项目版权归各自作者所有，请遵循其开源协议使用。

---
*由 WorkBuddy 借助 GitHub MCP 协助整理生成，并持续更新。*
