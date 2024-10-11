# 有用链接

[English](./VOID_USEFUL_LINKS.md) | [中文](./VOID_USEFUL_LINKS_CN.md) | [日本語](./VOID_USEFUL_LINKS_JP.md)

Void团队整理了这份链接列表,以帮助您快速上手VSCode的源代码。我们希望它能对您有所帮助!

## 初学者 / 入门

- [VSCode UI指南](https://code.visualstudio.com/docs/getstarted/userinterface) - 涵盖辅助栏、面板等。

- [UX指南](https://code.visualstudio.com/api/ux-guidelines/overview) - 涵盖容器、视图、项目等。

## 贡献

- [VS Code源代码的组织方式](https://github.com/microsoft/vscode/wiki/Source-Code-Organization) - 这解释了入口点文件的位置,`browser/`和`common/`的含义等。这是整个列表中最重要的阅读材料!我们建议您通读全文。

- [VSCode内置的所有命令](https://code.visualstudio.com/api/references/commands) - 有时用于参考很有用。

## VSCode的扩展API

Void目前主要是一个扩展,这些链接对我们的设置非常有用。

- [扩展中需要的文件](https://code.visualstudio.com/api/get-started/extension-anatomy)。

- [扩展的`package.json`模式](https://code.visualstudio.com/api/references/extension-manifest)。

- ["Contributes"指南](https://code.visualstudio.com/api/references/contribution-points) - `package.json`中的`"contributes"`部分是扩展如何挂载的方式。

- [完整的VSCode扩展API](https://code.visualstudio.com/api/references/vscode-api) - 查看右侧以了解组织结构。页面[底部](https://code.visualstudio.com/api/references/vscode-api#api-patterns)容易被忽视但很有用 - 取消令牌、事件、可释放资源。

- 您可以在`package.json`中定义的[激活事件](https://code.visualstudio.com/api/references/activation-events)（不是最有用的）
