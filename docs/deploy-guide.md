# 🖥️ 部署指南（按机器配置选型 · 2026-10-29 更新）

先确认你的硬件，再选方案。

## 1. 先自查
- 有没有独显？型号？（任务管理器 / `nvidia-smi`）
- 显存多大？（≥12G 能跑小模型，≥24G 跑 Wan2.2 5B 较舒服）
- 系统内存多大？（视频模型会大量 offload 到内存，建议 ≥64G 配 16G+ 显存）
- 有没有可用的云 API 额度？（阿里云 DashScope、MiniMax、即梦 Seedance 等）

## 2. 方案 A：无独显 / 有 API 额度（最易上手）
- 选 **AID Studio** / **LumenX Studio** / **Toonflow**（见 README 路线 A）。
- 部署：Docker 一键 / 官方脚本（AID Studio 仅 Linux；LumenX/Toonflow 看各自文档）。
- 配置：管理后台填模型 API Key。
- 成本：免费额度起步，量大按量。
- **更轻量替代**：直接用 `awesome-short-drama-skills` 里的 Skill，让 Agent 写剧本+分镜，再接一个云端视频 API 出片。

## 3. 方案 B：有 4090 级独显（本地零持续成本）
1. 装 [ComfyUI](https://github.com/comfyanonymous/ComfyUI) + 显卡驱动/CUDA。
2. 下载权重：**Wan2.2 5B（TI2V，8GB 起 / 24GB 流畅，Apache-2.0 可商用）** 或 HunyuanVideo 1.5（14GB 量化）。
3. 角色一致性：装 IP-Adapter / PuLID 节点。
4. 配音：本地跑 CosyVoice / GPT-SoVITS / Index-TTS。
5. 对口型：MuseTalk / LivePortrait。
6. 合成：ffmpeg 拼接 + 字幕。

## 4. 方案 C：中端独显（3060/3070 8-12G）
- 跑小模型：**Wan2.2 1.3B**、**LTX-Video**、**CogVideoX 1.5-5B（7GB INT8）**、量化版 HunyuanVideo。
- 分辨率降档、步数降低换速度。

## 5. 方案 D：纯 CPU / 笔记本
- 不建议本地跑视频模型。直接走云端 API（方案 A）。

## 6. 通用建议
- 角色一致性是短剧最大坑：固定参考图 + IP-Adapter + 固定 seed；平台类已内置三视图资产锁。
- API Key / Token 妥善保管，别提交到仓库。
- 先拿一个 30 秒小样跑通整条链路，再量产。
- 模型许可证看清：Wan2.2、Mochi 1 全 Apache-2.0 可商用；LTX-2.3 收入 <$10M 免费；HunyuanVideo 有社区许可约束。
