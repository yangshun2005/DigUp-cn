

> **[中文化] DigUp**
>
> 此项目是 [ARahim3/DigUp](https://github.com/ARahim3/DigUp) 的中文翻译版本。
> - 原项目 Stars: 2125
> - 主语言: Swift
> - 许可证: MIT
> - 翻译日期: 2026-10-13
> - 原始 README: [README_en.md](README_en.md)
>
> 说明：下方 README 正文为**原项目文档的中文翻译**，力求忠于原文；本页顶部的「中文快速上手」为**面向中文用户的补充导读**（非原文内容），目的是让你不用读完整篇 README 就能先把项目跑起来。
>
> 如有翻译不准确之处，欢迎提 Issue 或 PR。

---


## 🚀 中文快速上手（补充导读，非原文）

### 这是什么 / 解决什么问题

DigUp 是一个 macOS 桌面搜索工具，用 Google DeepMind 的 EmbeddingGemma 2 多模态嵌入模型，按「文件内容」而不是文件名来搜索你 Mac 上的文件。它能把图片、PDF、文档、录音、视频放进同一个语义空间，你用自然语言描述想找的东西，它就能定位到对应的文件、页面或时间点。所有索引都在本机完成，不上传文件。

### 快速上手（最短路径）

1. 从 [Releases](https://github.com/ARahim3/DigUp/releases) 下载 DMG 并拖入 Applications，或用 Homebrew 安装：`brew install --cask arahim3/tap/digup`
2. 打开 DigUp。模型会下载（865 MB，仅一次），期间选择要搜索的文件夹（可整目录，也可只选部分子目录）。
3. 等待首次索引完成（几百个文件约几分钟，大的 Downloads 文件夹可能约一小时）。
4. 在任意应用中按 **⇧⌘Space**，用自然语言描述你要找的内容。
5. 用 ↓ ↑ 选择结果，按 ↩ 打开（视频/录音跳到对应时刻，PDF 在 Preview 中定位到关键词，代码在编辑器中跳到对应行）。

### 环境要求

- 操作系统：macOS 14 或更高（原文称在 macOS 26 上测试过）
- 硬件：Apple Silicon Mac（M 系列芯片）
- 依赖：无需额外安装运行时；模型由应用自动下载（865 MB）
- 版本要求：原文未说明其他版本约束
- 国内网络提示：模型需从网络下载（865 MB），国内网络环境可能需要自备加速手段，原文未提供镜像源说明。

### 常见坑与注意事项

- 仅支持 Apple Silicon + macOS 14 及以上；Windows 和 Linux 版本原文称「在路上」，尚未提供。
- 首次使用需下载 865 MB 模型，且首次索引可能耗时较长（大文件夹约一小时），期间会占用资源，低电量模式下会暂停。
- 代码搜索默认关闭，需在 Settings → Code 或安装过程中手动开启，且只对你选定的文件夹生效。
- 首次用视频跳转到对应时刻时，macOS 会询问是否允许 DigUp 控制 QuickTime Player，需授权才能跳转。

---



---

<p align="center"><img src="docs/logo.png" width="96" alt=""></p>

<h1 align="center">DigUp</h1>

<p align="center"><b>描述它。挖出它。</b><br>
借助 Google DeepMind 的
<a href="https://huggingface.co/google/embeddinggemma-2">EmbeddingGemma 2</a>，按文件内容搜索你 Mac 上的文件。</p>

<p align="center"><a href="https://github.com/ARahim3/DigUp/releases/latest"><b>下载 Mac 版</b></a> · Apple Silicon，
macOS 14 或更高版本 · 免费且开源<br>
<sub>Windows 和 Linux 版本即将推出。</sub></p>

<p align="center"><img src="docs/demo.gif" width="800" alt="DigUp 的搜索面板在视频中找到斑马、播客中的某个片段、租约中的某条款、海滩上的狗（支持英语、孟加拉语和阿拉伯语），以及可在 Zed 中打开的代码"></p>

EmbeddingGemma 2 是 Google DeepMind 于 2026 年 10 月发布的多模态嵌入模型。它将文本、图像、音频和视频放入同一个共享空间：一张海滩上狗的照片会落在"海滩上的狗"这些词旁边，一段谈论睡眠的录音会落在"他们谈论睡眠的地方"旁边。它理解 100 多种语言，是开放的（Apache 2.0），并且只有 7.4 亿参数，小到足以在笔记本电脑上流畅运行。

DigUp 将这一能力带到了你 Mac 上的文件中。选择要搜索的文件夹，它会读取其中的图片、PDF、文档、录音和视频。然后，用你自己的话描述你要找的内容，它就能找到匹配项，无论是什么类型的文件。所有这一切都在你的 Mac 上完成。

## 你能找到什么

- "视频中的斑马"会打开斑马出现那一刻的片段
- "他们谈论睡眠的地方"会跳转到播客的那一分钟
- "租约中关于宠物的条款"会显示 PDF 页面，并标记出相关文字
- "海滩上的狗"能找到那张照片，"支付被拒错误"能找到那张截图
- 用英语搜索可以找到用孟加拉语、阿拉伯语或该模型支持的 100 多种语言写成的笔记，反之亦然
- "code: 用退避重试失败的调用"能在你的项目中找到那个函数，前提是你开启了代码搜索

精确词语同样重要。发票号码、错误代码和名称会按原样匹配，无论是在文件名、文档文本还是截图内的文字中，因此一次搜索既能获得语义，也能获得精确字符串。

## 隐私

你索引的任何内容都不会离开你的 Mac。DigUp 仅在首次下载模型和每天检查一次更新时联网。更新检查不会发送任何关于你文件的信息，你也可以将其关闭。无需账户，无遥测。

## 安装

1. 从 [Releases](https://github.com/ARahim3/DigUp/releases) 下载 DMG 并将 DigUp 拖入 Applications，或使用
   Homebrew：`brew install --cask arahim3/tap/digup`。
2. 打开它。在模型下载期间（865 MB，仅一次），选择要搜索的文件夹：整个文件夹，或仅其中的部分子文件夹。DigUp 会显示每个文件夹首次扫描所需的时间。
3. 在任意应用中按 **⇧⌘Space**，描述你要找的内容。

DigUp 需要一台搭载 Apple Silicon 且运行 macOS 14 或更高版本的 Mac（已在 macOS 26 上测试），并会自动保持更新。

## 使用方法

| 按键 | 功能 |
|---|---|
| ⇧⌘Space | 从任意应用打开搜索面板（可在设置中更改） |
| ↓ ↑ | 在结果中移动 |
| ↩ | 打开结果：视频和录音跳转到对应时刻，PDF 在 Preview 的搜索中显示你的词语，代码在编辑器中跳转到对应行 |
| Space | 快速查看，跳转到对应页面或时刻（在你移动到某个结果后） |
| ⌘↩ | 在 Finder 中显示 |
| ⌘C | 复制文件，以便粘贴到任何地方 |
| ⌘O | 在更大的窗口中执行相同搜索，带有图片网格和筛选器 |

DigUp 驻留在菜单栏中，你可以在那里查看索引进度、暂停索引或打开设置。首次在对应时刻打开视频时，macOS 会询问 DigUp 是否可以控制 QuickTime Player；这正是它跳转到那里所需的方式。

## 它能读取什么

仅限你选择的文件夹：

- 图片和截图（HEIC、JPEG、PNG、RAW、WebP 等），按其显示的内容读取，截图还会按其文字读取
- PDF，逐页读取，包括扫描件。较长的 PDF 会立即处理前 30 页，其余部分在其他所有内容处理完后处理（每个文件最多 5,000 页）
- 文档：txt、md、rtf、doc、docx、odt、html，长文档同样处理。主要由数字组成的文本（如数据导出）仅按其精确文本匹配
- 任意长度的音频：模型每次聆听 30 秒，因此 DigUp 采用重叠的 30 秒窗口，匹配项会指向其对应时刻
- 任意长度的视频：每隔几秒一帧，每个镜头一帧，外加与音频相同方式处理的音轨

在你为代码搜索选择的文件夹之外，它从不读取代码；而在代码项目（包含 `.git`、`package.json` 等的文件夹）内，它只读取截图。它从不读取密钥、证书、密码文件、像 `~/.ssh` 这样的隐藏文件夹、应用包或缓存。它会跳过看起来像数据集的文件夹，也从不下载仅存在于云端的 iCloud 文件。你可以在设置中跳过更多文件夹或文件类型。DigUp 只读取你的文件；它从不更改、移动或上传它们。

首次扫描对于几百个文件需要几分钟，对于庞大的 Downloads 文件夹可能需要一小时。这只会发生一次，使用电池时也会进行，除非你让它等待充电器，并且在低电量模式下会暂停。此后，新文件在落盘一两秒后即可被搜索到。

## 代码

EmbeddingGemma 2 也能读取代码，因此 DigUp 可以搜索你的项目。代码搜索在你于设置 → 代码中或设置过程中为你选择的文件夹开启之前是关闭的。每个仓库会显示读取所需的时间以及其索引占用的空间。然后以 `code:` 开始搜索，说明代码做什么，或输入其中包含的名称：

- "code: 用退避重试失败的调用"能找到那个函数，无论它叫什么名字
- "code: refreshAccessToken"会跳转到定义它的那一行，而不是调用它的地方
- "code: 绘制每个类别有多少个示例"能找到那个 notebook 单元格

结果会在你的编辑器中跳转到对应行：Zed、VS Code、Cursor、Xcode、Sublime Text、JetBrains IDE 等（在设置中选择一个）。代码有自己独立的索引，从不出现在其他搜索中。DigUp 读取源文件、notebook（不含其输出）以及仓库自身的文档。它会跳过 git 忽略的内容、第三方和生成的代码、数据文件，以及任何看起来像密钥或密码的内容。当你在处理代码时，索引会在一切安静下来一分钟后跟上进度。

读取代码对于一个小型应用约需 20 秒，而对于整个 llama.cpp 约需 20 分钟和 130 MB 的索引。

## 工作原理

```
你的文件夹 ─► 读取器（ImageIO、PDFKit、AVFoundation，以及用于截图文字的 Vision）
             ─► 在 llama.cpp（Metal）上运行的 EmbeddingGemma 2，位于一个完成后即退出的辅助进程中
             ─► 一个 SQLite 文件：为每张图片、每一页、每一段文字、每一视频帧和每 30 秒声音存储一个向量，
                外加一个关键词索引（代码搜索保留第二个索引，用于代码）
你的词语   ─► 同一模型的文本部分（约 250 MB，仅在你搜索时加载）─► 最近的向量 + 精确词语
```

DigUp 通过 [llama.cpp](https://github.com/ggml-org/llama.cpp) 在 Mac 的 GPU 上运行 ggml-org 的 EmbeddingGemma 2 8 位构建版本。每个向量都位于同一个 768 维空间中，这就是为什么一次查询可以将一个视频帧与一个 PDF 页面进行排名比较。一次搜索会在几毫秒内嵌入你的词语，并将其与索引中的所有内容进行比较。精确词语匹配会获得加权，因为没有任何嵌入能精确地保存一个发票号码。

索引会记住是哪个模型版本生成了它的向量。如果更新不改变向量，则保留你的索引；并且每次 llama.cpp 更新在发布前都会用存储的参考向量进行测试。

## 从源码构建

你需要 Xcode 26、git，以及用于 llama.cpp 的 CMake（或 `uv`）。如果 `xcode-select -p` 显示的是 Command Line Tools，请先切换到 Xcode（`sudo xcode-select -s /Applications/Xcode.app`）：它们缺少构建所需的 SwiftUI 和 Swift Testing 宏。

```sh
git clone https://github.com/ARahim3/DigUp && cd DigUp
scripts/build-llama.sh            # 固定标签版本的 llama.cpp，带一行补丁（几分钟）
swift build -c release && swift test
./build.sh                        # → build.noindex/DigUp.app
```

还有一个命令行工具 `.build/release/digup`，可以从终端进行索引、搜索和运行评估（`digup --help`）。`scripts/make-testbed.sh` 会构建一个测试文件文件夹供你试用（它需要 ffmpeg），而 `evals/` 存放用于衡量排名变化的查询。

## 常见问题

**这与 Spotlight 有何不同？** Spotlight 按文件名、文本和元数据查找文件。DigUp 还能按文件显示或讲述的内容查找它们，并带你到对应页面或时刻。两者可以很好地并存。

**Windows 或 Linux？** 两者都在开发中。

**为什么下载有 865 MB？** 那是模型：文本部分（310 MB）以及图像和音频编码器（555 MB）。应用本身约 20 MB。

**它会拖慢我的 Mac 吗？** 只有首次扫描负担较重。此后它只读取新文件。模型在单独的进程中运行，完成后即退出，而搜索部分仅在你搜索时加载。

**支持哪些语言？** 该模型支持 100 多种语言，DigUp 可在所有这些语言中搜索，也可跨语言搜索。评估仅涵盖英语、孟加拉语和阿拉伯语，因为这些是 DigUp 测试所用文件的语言，并且 Google 指出该模型并非在每种语言中都同样强大。有两个限制适用于精确词语，而非语义：截图内的文字由 Apple 的文本识别读取，它支持约 25 种语言；而像中文、日文和泰文这样不用空格书写的语言不会被分词。

**如何卸载？** 退出它，然后删除 DigUp.app 和 `~/Library/Application Support/DigUp`，后者存放模型和索引。其设置位于 `~/Library/Preferences/com.abdurrahim.DigUp.plist`。使用 Homebrew 时，`brew uninstall --cask --zap digup` 会删除全部内容。

## 支持

DigUp 是免费且开源的，并将一直如此。如果它对你有帮助，而你想支持它，可以
[请我喝杯咖啡](https://arahim3.gumroad.com/l/support)。

## 致谢

DigUp 构建于 Google DeepMind 的 [EmbeddingGemma 2](https://huggingface.co/google/embeddinggemma-2)（Apache 2.0）、
[llama.cpp](https://github.com/ggml-org/llama.cpp)（MIT）和 [Sparkle](https://sparkle-project.org)（MIT）之上。它们的
许可声明随应用一同发布，位于 `DigUp.app/Contents/Resources/Acknowledgements.txt`。

DigUp 与 Google 或 Apple 无关联。Gemma 是 Google LLC 的商标；Mac 和 Spotlight 是 Apple Inc. 的商标。

## 许可证

MIT