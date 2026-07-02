---
name: recite-tts
description: 中文朗诵 TTS 流水线。给定中文文本/文档，用男声专业朗诵风格合成 MP3（适配喜马拉雅/网易云等平台发布）。基于 edge-tts，支持散文/诗歌/新闻/小说 4 种文体，每种文体有专属语速和停顿处理。
trigger: "朗诵 / 朗读 / 把这段文字念出来 / 配乐朗诵 / 喜马拉雅音频 / 给我朗诵一段 / 诗歌朗读"
---

# recite-tts · 中文朗诵 TTS

把任意中文文本/文档转成男声朗诵风格 MP3，零成本、零风险、直接可上喜马拉雅等平台发布。

## 何时用

- 把一篇散文/诗歌/小说章节转成朗诵音频
- 给喜马拉雅、网易云、荔枝播客做内容创作
- 物流行业文章、读书笔记的"听书版"
- 想要"专业朗诵"风格（沉稳、有情感起伏、有句间气口）

## 何时不要用

- 想要克隆某个特定人的真实声音 → 这是音色克隆，**本 skill 不支持**。参考本文末尾"路线 B 备忘"
- 极短文本（<20 字）→ 直接用内置 `text_to_speech` 工具即可

## 快速开始

```bash
# 1) 一句话
python3 ~/.hermes/skills/recite-tts/scripts/recite_tts.py \
  --text "今晚的月色很美" --out /tmp/test.mp3

# 2) 长文档（散文）
python3 ~/.hermes/skills/recite-tts/scripts/recite_tts.py \
  --file ~/文章/散文.md --out ~/录音/散文01.mp3 --style prose

# 3) 诗歌（按行切分，慢速）
python3 ~/.hermes/skills/recite-tts/scripts/recite_tts.py \
  --file 再别康桥.txt --out ~/录音/再别康桥.mp3 --style poetry

# 4) 小说章节
python3 ~/.hermes/skills/recite-tts/scripts/recite_tts.py \
  --file chapter01.md --out chapter01.mp3 --style novel --voice zh-CN-YunxiNeural
```

## 音色选择

| 音色 | 风格 | 适合 |
|---|---|---|
| `zh-CN-YunjianNeural`（**推荐**） | 男声·沉稳大气 | 散文、诗歌朗诵、纪录片旁白 |
| `zh-CN-YunxiNeural` | 男声·青年温和 | 小说叙述、对话、年轻作家 |
| `zh-CN-YunyangNeural` | 男声·新闻播报 | 新闻、报告、正式场合 |
| `zh-CN-YunhanNeural` | 男声·浑厚磁性 | 文学评论、深度长文 |
| `zh-CN-YunzeNeural` | 男声·成熟 | 替代选项 |

## 4 种文体的差异

| 文体 | 语速 | 切分策略 | 适用 |
|---|---|---|---|
| `prose`（散文） | -8% | 按句切分，单段 ≤200 字 | 朱自清/余秋雨/史铁生风格 |
| `poetry`（诗歌） | -12% | 按行切分，4 行为一"节" | 现代诗/古诗/歌词 |
| `news`（新闻） | 0% | 按句切分 | 行业资讯、新闻播报 |
| `novel`（小说） | -5% | 按段切分 | 长篇小说、人物对话 |

## 工作流（含完整参数）

### 1. 准备文本
- **MD 文件**：`#` `**` `>` 等格式自动清除，保留段落
- **TXT 文件**：直接用，但建议段落间用空行分隔
- **直接传**：`--text "..."` 仅适合短文本

### 2. 选择文体
脚本会根据 `--style` 自动设置语速和切分策略。**不指定 `--rate` 就用默认**。

### 3. 输出
- 单段文本 → 直接 1 个 MP3
- 多段文本 → 临时切分合成 + ffmpeg 合并为 1 个 MP3
- 输出目录不存在会自动创建

### 4. 网络
需要走代理访问 Microsoft Edge TTS：
```bash
export HTTPS_PROXY=127.0.0.1:7897 HTTP_PROXY=127.0.0.1:7897
```

## 关键坑 & 解决

### edge-tts 不支持 pitch="0Hz"
传 pitch 必须用非零值（如 `"+0Hz"`/`"-2Hz"`），否则 ValueError。本 skill **不传 pitch** 走默认值，规避此问题。

### pitch 不传时 edge-tts 可能也会报 "No audio was received"
**网络问题**。检查代理：
```bash
curl -x http://127.0.0.1:7897 -I https://api.edge.microsoft.com
```

### ffmpeg 不存在
合并多段需要 `ffmpeg`：
```bash
sudo apt install ffmpeg
```

### 长文超过 4096 字符
edge-tts 单次最多 ~4096 字符。本 skill 默认 `--max-chars=1500`，超过会自动切分合并。

### 生成速度
- 1 分钟音频 ≈ 2-5 秒合成
- 一篇 5000 字散文 ≈ 30-60 秒出成品

## 路线 B 备忘（音色克隆，如果你未来要走）

如确需"克隆某个真实的人声"（如瞿弦和、某个播音名家），**强烈建议先评估法律风险**：

- **民法典 1019 条**：自然人声音受人格权保护
- **2024 杭州 AIGC 第一案**：未授权克隆已故配音演员声音构成侵权
- **喜马拉雅/网易云**：2024 年起普遍禁止未授权的 AI 克隆音色上架
- **个人自用研究**：法律灰色地带，但训练数据和模型 ckpt 不能公开传播

技术上路线 B 的完整步骤：
1. 抓取 B 站视频 → `yt-dlp` 下载
2. UVR5 做**人声/背景音分离**（必须，否则训练会带 BGM 噪声）
3. Whisper-large-v3 做**强制对齐**生成精确时间戳
4. 切片 5-10 分钟高质量纯净人声
5. 选模型：
   - **So-VITS-SVC v4**：音质最好但训练复杂，要 12G+ 显存
   - **XTTS-v2**（推荐入门）：Coqui 出品，CPU 推理也能用，效果略逊
6. 租云 GPU：**AutoDL**（A10 1.8 元/小时）/ **恒源云** / **矩池云**
7. 训练 4-12 小时，下载 ckpt，本地或云推理
8. 配套需要 GPU 服务器，本机 CPU 跑 XTTS 推理 1 分钟音频需要 5-15 分钟

> 现实建议：商用 TTS 已经做到 95% 自然度 + 0 风险。除非有**不可替代的真实克隆需求**（如家族声音纪念、过世家人的声音），否则路线 A 的投资回报比远高于路线 B。

## 相关 skill

- `chinese-tts-doc`：基于 edge-tts 的通用长文档 TTS 流水线（本 skill 的前身/简化版）
- `chinese-tts-doc/SKILL.md` 中有更详细的 edge-tts 参数文档
- `dialogue-tts`：8 个 dialogue-* 数字分身的 TTS 朗读（单句短音频专用，与本 skill 长文档场景不重叠）
- `references/voice-cloning-reality-check.md`：用户要求"克隆真实人物声音"时必读的 A/B/C 决策清单

## 用户要求"克隆 XX 声音"时的标准动作

**先读** `references/voice-cloning-reality-check.md`，再决定 A/B/C 三选项。95% 情况下推荐 A（商用 TTS 男声 + 朗诵风格优化），不要默认走 B（云上训练）。
