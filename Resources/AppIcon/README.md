# DigUp 的图标："One space"

四块瓷砖，对应 DigUp 搜索的内容（文本、图片、声音、视频），围绕着一个琥珀色的 D，D 中的搜索光点在发光。
苔藓配色。

- `appicon.svg`：应用图标（1024 × 1024，macOS 图标网格）。`../AppIcon.icns` 在 64 px 及以上尺寸使用它。
- `appicon-small.svg`：相同设计，但去掉了瓷砖内部的字形，因为缩小后会变成噪点。`../AppIcon.icns`
  在 16 和 32 px 尺寸使用它。
- `AppIcon.icon`：与 macOS 26 及更高版本相同的分层设计（一个 Icon Composer 文档：一个 #13201A 填充、瓷砖、D）。`build.sh` 用 `actool` 将其编译为 `Assets.car`；`Info.plist` 的 `CFBundleIconName` 指向它。没有它，macOS 26 会把 `.icns` 缩小绘制在一个灰色方块内。较旧的 macOS 使用 `.icns`（`CFBundleIconFile`；未在那里测试过）。
- `menubar.svg`：菜单栏标记，一个带框的 D。应用在代码中用相同的几何形状绘制它（`Sources/DigUpApp/StatusMenu.swift` 中的 `StatusIcon`），用索引环代替方框。

要在编辑源文件后重新构建 `AppIcon.icns`：用能绘制 SVG 模糊滤镜的渲染器（浏览器或 WebKit；macOS 自带的 SVG 渲染器会丢弃柔和阴影）将两个 SVG 渲染为 iconset（`icon_16x16.png` 和 `icon_16x16@2x.png`/`icon_32x32.png` 来自 `appicon-small.svg`，尺寸为 16 和 32 px；其余八个尺寸，64 到 1024 px，来自 `appicon.svg`），然后执行 `iconutil -c icns AppIcon.iconset -o ../AppIcon.icns`。

颜色：瓷砖 #13201A；瓷砖 #D5E6BB、#A2C78E、#64976B、#356652；D 从 #FFD166 → #F2A22A，带 #13201A 描边；搜索光点 #FFF6DA。