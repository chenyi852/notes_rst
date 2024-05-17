javscript
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

QuickJS
===================
QuickJS 是一个开源的 JavaScript 引擎，它被设计为轻量级且高性能。QuickJS 支持 ECMAScript 2020（ES2020）的主要特性，
包括但不限于模块、异步生成器、异步await和BigInt。它由法国的 Fabrice Bellard 开发，他也是许多其他著名开源项目
（如 QEMU、FFmpeg 和 TinyCC）的作者。

以下是 QuickJS 的一些主要特点：

轻量级：QuickJS 的设计目标之一是保持轻量级，适用于资源受限的环境。

快速：QuickJS 旨在提供快速的执行性能，即使在没有 JIT（即时编译）支持的情况下。

ES2020 支持：QuickJS 支持 ECMAScript 2020 规范的大部分特性。

模块支持：QuickJS 支持 ES6 模块，允许开发者编写模块化的 JavaScript 代码。

异步编程：QuickJS 支持异步函数和生成器，使得异步编程更加直观和易用。

BigInt：QuickJS 实现了 BigInt 类型，允许表示大于 2^53 - 1 的整数。

交叉编译：QuickJS 可以交叉编译到多种平台，包括 Windows、Linux、macOS 和嵌入式系统。

C API：QuickJS 提供了丰富的 C API，允许开发者从 C 语言中调用和控制 JavaScript 引擎。

JSON 支持：QuickJS 支持 JSON 的解析和生成。

命令行工具：QuickJS 提供了一个命令行工具，可以直接运行 JavaScript 文件或使用交互式 REPL（Read-Eval-Print Loop）模式。

QuickJS 适用于需要一个快速、可嵌入的 JavaScript 引擎的场景，如嵌入式设备、Web 服务器插件或其他需要执行 JavaScript 代码的应用程序。
由于其轻量级和高性能，QuickJS 也适合用于教育和研究目的，帮助开发者和学生更好地理解 JavaScript 引擎的工作原理。