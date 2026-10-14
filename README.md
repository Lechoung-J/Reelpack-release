<div align="center">
  <h1>Reelpack</h1>
  <p><strong>给 AI 的视频理解引擎</strong> · 拉片 · 分镜 · 口播</p>
  <p>
    <img src="https://img.shields.io/badge/platform-macOS-000000?style=flat&logo=apple&logoColor=white" alt="Platform: macOS">
    <img src="https://img.shields.io/badge/macOS-14%2B-007AFF?style=flat" alt="macOS 14+">
    <img src="https://img.shields.io/badge/status-preview-F59E0B?style=flat" alt="Status: preview">
    <img src="https://img.shields.io/badge/license-FSL--1.1--MIT-6F42C1?style=flat" alt="License">
  </p>
</div>

# Reelpack — preview downloads

把一条视频，拆成 AI Agent 能读的资产包。

---

**先问你一句：你刷过的那些好片，最后都去哪了？**

别人刷视频是刷视频。你刷到一条好广告，会下意识倒回去——这个转场怎么接的？几秒切一刀？那句台词凭什么这么勾人？然后拖着进度条想把它拆开看。四十分钟，记了三行，剩下一半还在脑子里，第二天全忘。因为视频，是这世界上**唯一一种没法 Ctrl+F 的格式**：搜不到、拷不走、回不去。

一个在影视行业待了十几年的人，这几年最大的感受是：**AI 只能读文字，它读不懂一条片子。** 于是总有那种错位——**人眼看哭的，AI 看着没感觉。**

Reelpack 想让 AI **真的坐下来，把片子看一遍**：谁在第几秒说了什么、切了几刀、画面写着什么、节拍压在哪——全拆成**能回查、能复制、能喂给你自己 Agent 的证据**。**它就是给视频装上的那个 Ctrl+F。** 它不改视频，它改的，是你看视频的方式；而你看过的每一条，都会留下——慢慢长成你自己的知识库。

---

## ⬇️ 下载

- **平台**：Apple Silicon（arm64），macOS 14 或更新
- **版本**：0.1.0 preview
- **文件**：
  - `Reelpack-0.1.0-arm64.zip`（3,304,456 字节）
  - `Reelpack-0.1.0-arm64.zip.sha256`
  - `release-manifest.json`
- **SHA-256**：
  `44f330945961b2e5320f7a9748f00707e3bc18c2d5cf7ec0a069f3b8156e8574`

下载后先校验：

```sh
shasum -a 256 -c Reelpack-0.1.0-arm64.zip.sha256
```

## 安装

```sh
bash install.sh --archive 'Reelpack-0.1.0-arm64.zip' \
  --sha256 'Reelpack-0.1.0-arm64.zip.sha256' --no-launch
```

默认安装到 `~/Applications/Reelpack.app` 与 `~/Library/Application Support/Reelpack/runtime/arm64`。
需要原生 **Python 3.12** 与 **FFmpeg / ffprobe**；模型权重按需另装，不随包。

装完丢一个**本地视频文件**进去即可；Agent 用法见包内 `SKILL.md`。

## 已知限制

- **未公证**：本机 ad-hoc 签名，下载副本可能被 macOS Gatekeeper 拦截。
- **仅 arm64**；Intel / x86_64 未构建、未验证。
- **macOS 14 尚未实机验证**（最低目标为 14.0）。
- **只吃本地文件**（MP4 / MOV / MKV）；不解析网页 / 平台链接。
- 可选后端（音乐、OCR）按需自装，缺席时优雅降级，不影响主流程。

## 关于源码

源码在 [`Lechoung-J/Reelpack`](https://github.com/Lechoung-J/Reelpack)（**Fair Source，即将开放**）。
本仓库是**下载 / 校验 / 安装**端点。有问题请开 Issue。

## 许可

[FSL-1.1-MIT](LICENSE)（源码可用 / Fair Source，2 年后转 MIT）。依赖、系统工具与模型权重各自保留其许可。
