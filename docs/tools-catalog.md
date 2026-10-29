# 🧰 工具清单（分类明细 · 2026-10-29 更新）

> 均指向 GitHub 官方/主流仓库。协议以各仓库 LICENSE 为准（多为 MIT / Apache-2.0）。

## 一、一站式平台（推荐新手）
| 名称 | 仓库 | 协议 | 亮点 | 适合 |
|---|---|---|---|---|
| AID Studio | [gzxx-2025/aid-studio](https://github.com/gzxx-2025/aid-studio) | MIT | 全开源自托管，剧本→分镜→图→视频→配音→成片，多模型接入，Docker/systemd 部署（仅 Linux） | 想一站式、可自托管 |
| LumenX Studio | [alibaba/lumenx](https://github.com/alibaba/lumenx) | MIT | 阿里出品，小说→视频，Qwen+通义万相，本地优先，三视图资产锁一致性 | 小说漫剧、想用大厂生态 |
| Toonflow | [HBAI-Ltd/Toonflow-app](https://github.com/HBAI-Ltd/Toonflow-app) | MIT | 三层 Agent 架构（事件图谱→分镜→视频），无限画布+可视化工作流，19k★，MCP/插件扩展 | 小说一键转短剧、可本地部署 |

## 二、短剧 Skill 精选库（让 Agent 帮你写/拆）
| 名称 | 仓库 | 说明 |
|---|---|---|
| awesome-short-drama-skills | [UnderleveledBuilder/awesome-short-drama-skills](https://github.com/UnderleveledBuilder/awesome-short-drama-skills) | 🆕 汇总数十个短剧/漫剧 Skill：剧本、改编、分镜、Seedance/可灵/MiniMax 视频提示词；千问/豆包/WorkBuddy/Claude Code/Codex 可用 |

> 精选子 Skill：`infinite-creation`（本地 ComfyUI+MiniMax H3 自动连续生产，★116）、`ai-film-skills`（21 模块，★85）、`ai-short-drama`（题材调研+架构，★71）、`novel-to-manju`（小说转漫剧，★63）、`muse-video-skill`（虚拟剧组六角色，★46）、`Dramake`/`雪风爽剧`（文字转短剧+Seedance 提示词）

## 三、编排核心
| 名称 | 仓库 | 说明 |
|---|---|---|
| ComfyUI | [comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI) | 节点式图像/视频编排，免费，生态最大 |

## 四、视频生成（开源权重免费 · 2026 实测对比）
| 名称 | 仓库 | 显存门槛 | 协议 | 亮点 / 定位 |
|---|---|---|---|---|
| Wan2.2 (TI2V-5B) | [Wan-Video/Wan2.2](https://github.com/Wan-Video/Wan2.2) | 8GB 起 / 24GB 流畅 | Apache-2.0 | **商业使用最安全**，5s 720P 约 30s/条（4090） |
| Wan2.2 (T2V/I2V-A14B) | 同上 | 24GB(fp8)–48GB+ | Apache-2.0 | 影视级美学，MoE 架构 |
| LTX-2.3 | [Lightricks/LTX-Video](https://github.com/Lightricks/LTX-Video) | 32GB 量化 | LTX-2 社区/商业 | **唯一原生音视频联合生成**，4K，多镜头一致性 |
| HunyuanVideo 1.5 | [Tencent/HunyuanVideo](https://github.com/Tencent/HunyuanVideo) | 14GB 量化 | 腾讯混元社区 | 中端硬件最佳，人脸稳定 |
| CogVideoX 1.5-5B | [THUDM/CogVideo](https://github.com/THUDM/CogVideo) | 7GB INT8 | CogVideoX 许可 | 低显存首选，中文友好 |
| Mochi 1 | [genmoai/mochi](https://github.com/genmoai/mochi) | ~20GB | Apache-2.0 | 写实、运动真实（略老） |
| SkyReels-V2 | [SkyworkAI/SkyReels-V2](https://github.com/SkyworkAI/SkyReels-V2) | 24GB+ | 自定义协议 | 人物/影视场景首选 |

## 五、角色一致性
| 名称 | 仓库 | 说明 |
|---|---|---|
| IP-Adapter | [tencent-ailab/IP-Adapter](https://github.com/tencent-ailab/IP-Adapter) | 图像参考控制 |
| PuLID | [ToTheBeginning/PuLID](https://github.com/ToTheBeginning/PuLID) | 人脸身份保持 |
| InstantID | [InstantID/InstantID](https://github.com/InstantID/InstantID) | 单图人脸一致 |

## 六、配音 TTS（开源免费）
| 名称 | 仓库 | 说明 |
|---|---|---|
| CosyVoice | [FunAudioLLM/CosyVoice](https://github.com/FunAudioLLM/CosyVoice) | 阿里，多语种、克隆效果好 |
| GPT-SoVITS | [RVC-Boss/GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS) | 少样本克隆，中文强 |
| Index-TTS | [index-tts/index-tts](https://github.com/index-tts/index-tts) | 🆕 高质量零样本克隆 TTS |
| ChatTTS | [2noise/ChatTTS](https://github.com/2noise/ChatTTS) | 自然对话 TTS |
| Fish Speech | [fishaudio/fish-speech](https://github.com/fishaudio/fish-speech) | 多语种克隆 |

## 七、对口型
| 名称 | 仓库 | 说明 |
|---|---|---|
| Wan2.2-Animate | [Wan-Video/Wan2.2](https://github.com/Wan-Video/Wan2.2) | 阿里视频驱动口型 |
| MuseTalk | [TMElyralab/MuseTalk](https://github.com/TMElyralab/MuseTalk) | 实时对话口型 |
| LivePortrait | [PhyAU/LivePortrait](https://github.com/PhyAU/LivePortrait) | 图片/视频驱动表情 |
| Wav2Lip | [Rudrabha/Wav2Lip](https://github.com/Rudrabha/Wav2Lip) | 经典唇形同步 |

## 八、合成与工具
| 名称 | 仓库/地址 | 说明 |
|---|---|---|
| ffmpeg | [ffmpeg.org](https://ffmpeg.org/) | 切片、拼接、加字幕、混音 |
