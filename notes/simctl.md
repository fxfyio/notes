如果您想要编程控制 iOS 模拟器，可以使用 Apple 的自动化工具 `xcrun simctl`。`xcrun simctl` 是 Xcode 命令行工具的一部分，可以控制模拟器。

在 macOS 终端中，您可以使用 `xcrun simctl` 命令来进行各种操作，例如列出所有可用的设备、启动和关闭模拟器、安装应用程序、发送通知、更改设备设置等等。

以下是一些基本的 `xcrun simctl` 命令示例：

- 列出所有设备：
  ```shell
  xcrun simctl list devices
  ```
- 启动模拟器：
  ```shell
  xcrun simctl boot '设备的 UUID'
  ```
- 安装应用：
  ```shell
  xcrun simctl install '设备的 UUID' '应用程序的路径'
  ```
- 卸载应用：
  ```shell
  xcrun simctl uninstall '设备的 UUID' '应用程序的 Bundle ID'
  ```
- 向模拟器发送通知：
  ```shell
  xcrun simctl push '设备的 UUID' '应用程序的 Bundle ID' '通知的 json 文件路径'
  ```

要查看 `xcrun simctl` 的全部命令和选项，您可以在终端中运行 `xcrun simctl`。

需要注意的是，使用 `xcrun simctl` 需要在 macOS 上安装 Xcode，并确保 Xcode 命令行工具已经正确安装。在 macOS 终端中运行 `xcode-select --install` 可以安装 Xcode 命令行工具。

如果您想要在 Python 或其他语言中调用 `xcrun simctl`，可以使用对应语言的子进程或者系统命令调用功能。在 Python 中，可以使用 `subprocess` 模块来运行 `xcrun simctl` 命令。