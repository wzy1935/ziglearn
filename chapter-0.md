---
title: "Chapter 0 - Getting Started"
weight: 1
date: 2021-01-23 20:52:00
description: "Ziglearn - A Guide / Tutorial for the Zig programming language. Install and get started with ziglang here."
---



# 欢迎！

[Zig](https://ziglang.org) 是一种通用编程语言和工具链，用于维护 __高稳定__、__高性能__ 和 __高可用__ 的软件。

警告：Zig的最新的主版本是 is 0.9，仍在测试阶段。因此仍然不建议在生产中使用，您可能会遇到编译器自身的bug。

要遵循本指南，我们假设您已经：
   * 有一定编程经验
   * 对底层编程概念有一定理解

了解 C、C++、Rust、Go、Pascal 或其他类似的语言将有助于您使用本指南。阅读时，请确保你的电脑有可用的编辑器、终端和互联网连接。本指南是非官方的，与 Zig 软件基金会无关。阅读时建议按章节顺序从头阅读。



# 安装

这篇指南假设你安装的是Zig的最新版本。主版本可以从官网下载或者直接通过源代码编译生成。通过包管理器下载的Zig可能版本比较落后。这篇指南不支持Zig 0.9.1。

1.  可以在下面网站上获取编译好的Zig：
```
https://ziglang.org/download/
```

2. 添加Zig到环境变量
   - linux， macos， bsd

      将Zig所在路径添加到 `PATH` 环境变量下。安装时，可以将类似 `export PATH=$PATH:~/zig` 的内容添加到 `/etc/profile` （安装到整个系统）或 `$HOME/.profile` 目录下。如果没有立即生效，请手动在shell窗口中运行。
   - windows

      a) 安装到整个系统（管理员权限下使用powershell）

      ```powershell
      [Environment]::SetEnvironmentVariable(
         "Path",
         [Environment]::GetEnvironmentVariable("Path", "Machine") + ";C:\your-path\zig-windows-x86_64-your-version",
         "Machine"
      )
      ```

      b) 个人安装（使用powershell）

      ```powershell
      [Environment]::SetEnvironmentVariable(
         "Path",
         [Environment]::GetEnvironmentVariable("Path", "User") + ";C:\your-path\zig-windows-x86_64-your-version",
         "User"
      )
      ```

      接着关闭这个控制台，再重新打开一个。

3. 使用命令 `zig version` 来验证安装是否成功。输出看起来应该是这样的：
```
$ zig version
0.9.0-dev.1083+9fa723ee5
```

4. （可选的，第三方工具）如果需要为编辑器提供代码补全和变量声明查找功能，可以在这里安装Zig的语言服务器：
```
https://github.com/zigtools/zls/
```
5. （可选的）加入[Zig社区](https://github.com/ziglang/zig/wiki/Community)。



# Hello World

创建一个 `main.zig` 文件，添加以下内容：

```zig
const std = @import("std");

pub fn main() void {
    std.debug.print("Hello, {s}!\n", .{"World"});
}
```
###### （注意：确保你的文件使用空格缩进，LF换行和UTF-8编码！）

使用 `zig run main.zig` 来编译和运行。在这个例子中，`Hello, World!` 会输出到stderr流中，并不应该报错。
