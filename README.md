关于
drawio-desktop是一个基于Electron 的图表和白板桌面应用程序，它包装了核心 draw.io 编辑器。

从发布部分下载构建的二进制文件。

我可以免费使用此应用程序吗？可以，根据 Apache 2.0 许可证。如果您不更改代码并接受其“按原样”提供，则可以将其用于任何目的。

安全
draw.io Desktop 的设计完全与互联网隔离，除了更新过程之外。它会在启动时检查 github.com 是否有更新版本，并从 Github 拥有的 AWS S3 存储桶中下载。所有 JavaScript 文件都是独立的，内容安全策略禁止运行远程加载的 JavaScript。

我们从未向外部发送过任何图表数据，也不会向外部发送任何有关应用程序使用情况的分析数据。这意味着某些我们没有 JavaScript 实现的功能在桌面版本中无法使用，即 .vsd 和 Gliffy 导入。

安全性和隔离应用程序是 draw.io 桌面版的主要目标。如果您要求在应用程序中默认启用涉及外部连接的任何功能，答案将是“否”。

支持
支持是在合理的业务约束基础上提供的，但没有任何合同约束。所有支持均通过此存储库提供。没有私人票务支持。

购买适用于 Confluence 或 Jira 的 draw.io 并不意味着您有权获得 draw.io 桌面版的商业支持。Atlassian 的 draw.io 集成由 Seibert Media 销售，他们与该项目无关。

发展
draw.io是drawio-desktop的一个 git 子模块。要同时获得这两个模块，你需要递归克隆：

git clone --recursive https://github.com/jgraph/drawio-desktop.git

运行此命令：

npm install（在此 repo 的根目录中）
如果您想在开发模式下开发/调试，请导出 DRAWIO_ENV=dev。
npm start 此 repo 根目录中的运行应用程序。如需调试，请使用npm start --enable-logging。
注意：如果使用符号链接来引用 drawio repo（而不是子模块），那么符号链接node_modules里面的目录drawio/src/main/webapp也会被引用。

释放：

更新 draw.io 子模块并推送更改。推送到原点之前添加版本标签。
等待构建完成（https://travis-ci.org/jgraph/drawio-desktop和https://ci.appveyor.com/project/davidjgraph/drawio-desktop）
前往https://github.com/jgraph/drawio-desktop/releases，编辑预览版本。
下载 Windows exe 和 Windows portable，使用以下方式签名signtool sign /a /tr http://rfc3161timestamp.globalsign.com/advanced /td SHA256 c:/path/to/your/file.exe
重新上传已签名的文件，draw.io-windows-installer-x.y.z.exe并draw.io-windows-no-installer-x.y.z.exe
添加发行说明
发布版本
注意：在 Windows 版本中，当同时使用 x64 和 is32 作为架构时，结果将是一个包含两个架构的大文件。这就是我们将它们拆分的原因。

本地存储和会话存储存储在 AppData 文件夹中：

macOS：~/Library/Application Support/draw.io
视窗：C:\Users\<USER-NAME>\AppData\Roaming\draw.io\
不开放贡献
draw.io 不接受任何贡献。

该项目的复杂程度意味着，即使是简单的更改也可能破坏许多其他活动部件。所需的测试量远远超过乍一看的量。如果我们要收到 PR，我们基本上必须将其丢弃并按照我们希望实现的方式编写。

我们非常感谢社区的参与、错误报告和功能请求。我们不想表现得不热情，但是，为了项目的长期可行性，我们决定不接受任何贡献。
