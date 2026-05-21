# Kami
## ReadMe中文翻译

<img src="public/icon.png" width="200">

Kami 是一款折纸模拟游戏，旨在通过物理铰链（折叠屏）进行驱动，并在支持时使用折叠设备 API。

在线体验：[https://maxwase.github.io/kami](https://maxwase.github.io/kami)

!**重要提示** [Posture API (姿态 API)](https://developer.mozilla.org/en-US/docs/Web/API/Device_Posture_API) 仅在部分浏览器中有效！请在[此处](https://developer.mozilla.org/en-US/docs/Web/API/Device_Posture_API#browser_compatibility)查看浏览器兼容性。

## 效果演示

[https://github.com/user-attachments/assets/56427f60-d67c-44de-a087-7d626d0598f2](https://github.com/user-attachments/assets/56427f60-d67c-44de-a087-7d626d0598f2)

# 游戏选项

游戏会尽最大努力自动检测您设备的折叠姿态和功能，但您也可以通过左上角的“Show Options（显示选项）”按钮进行手动设置。

1. **反转折叠方向 (Invert fold direction)** —— 默认情况下，Kami 假设加速度计位于屏幕的右半部分。它会尝试检测您折叠设备的方向（从左到右、从上到下等）。如果检测错误，请在此处手动设置。
2. **稳定性阈值 (Stability threshold)** —— 此设置控制姿态检测对微小动作的敏感度。较低的值意味着即使是轻微的倾斜也会被计为折叠，而较高的值则需要更快的折叠动作。
3. **X 轴和 Y 轴 (X and Y axis)** —— 世纪难题依然存在：设备的中心究竟在哪里？

## 安装方法

1. 从 [Releases (发布)](https://github.com/maxwase/kami/releases) 页面下载适用于 Mac 的最新版本。
2. 解压文件。
3. 像安装其他 dmg 一样进行安装，将应用拖入“应用程序 (Applications)”文件夹。
4. 运行命令：`xattr -dr com.apple.quarantine /Applications/kami-tauri.app`。这一步是必需的，因为我没有用于对二进制文件进行签名的 Apple 开发者账号。
   如果您不信任 GitHub Actions 的构建输出，可以考虑[自行编译](#原生应用-native)该应用。

## 环境要求

- Node.js 18+ (Vite 7)
- pnpm 9+
- 运行测试折叠功能需要一款现代[浏览器](https://developer.mozilla.org/en-US/docs/Web/API/Device_Posture_API)。请注意，该 API 仅在 localhost 或 HTTPS 连接下可用。
- 如果使用 `tauri` 为 MacOS 编译，则需要 [稳定版 Rust](https://rustup.sh)。

## 构建与运行

### 网页端 (Web)

```sh
pnpm install
pnpm run dev    # 启动 Vite 开发服务器
pnpm run build  # 类型检查 + 生产环境打包至 dist/
```

### 原生应用 (Native)

在 MacOS 上运行，请执行以下命令：

```sh
pnpm install
pnpm run tauri dev    # 启动 Vite 开发服务器
pnpm tauri build --bundles app    # 构建应用安装包
```

# 致谢

- [Foldy bird](https://lyra.horse/fun/foldy-bird) —— 用屏幕折叠（铰链翻动）来控制的像素鸟 (Flappy Bird)！令人惊讶的是，两个人竟然能独立想到同一个点子！不过 Lyra 先发布了它，恭喜！
- [LidAngleSensor](https://github.com/samhenrigold/LidAngleSensor) —— 对 MacBook 开合角度传感器非常厉害的反向工程，正是它启发了我去尝试折叠屏设备！

# 项目未来

我主要是一名后端开发人员，所以这里的代码质量可能不是最好的，其中很多代码都是在某天周末由 AI 生成的。
我想用 Rust 和 WebAssembly 重写这个项目，使其具有跨平台能力，并加入更复杂的折叠谜题。
如果您有任何想法或建议，欢迎通过 [Telegram](https://t.me/maxwase) 或 [电子邮箱](mailto:max.vvase@gmail.com) 与我联系 :)
