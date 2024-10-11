# 为Void做贡献

[English](./CONTRIBUTING.md) | [中文](./CONTRIBUTING_CN.md) | [日本語](./CONTRIBUTING_JP.md)

欢迎！👋 这是关于如何为Void做贡献的指南。我们希望尽可能简单地进行贡献，所以如果您有任何问题或意见，请通过电子邮件或Discord联系我们！

有两种主要的贡献方式：

- 提出新功能建议（[discord](https://discord.gg/RSNjgaugJs)）
- 构建新功能（[project](https://github.com/orgs/voideditor/projects/2/views/3)）

我们使用一个[VSCode扩展](https://code.visualstudio.com/api/get-started/your-first-extension)来实现大部分Void的功能。向下滚动查看以下内容：1. 如何构建/贡献于扩展，或者 2. 如何构建/贡献于完整的IDE（用于更多原生改变）。

查看我们整理的一些有用链接，请参阅[`VOID_USEFUL_LINKS.md`](https://github.com/voideditor/void/blob/main/VOID_USEFUL_LINKS.md)。

## 1. 构建扩展
以下是您可以开始为Void扩展做贡献的方法。如果您是新手，这就是您应该开始的地方。

1. 克隆存储库：

```
git clone https://github.com/voideditor/void
```

2. 在VS Code中打开`/extensions/void`文件夹（在新的工作区中打开，*不要*只进入该文件夹）：

```
open /extensions/void
```

3. 安装依赖项：

```
npm install
```

4. 构建项目。我们创建了这个构建命令，以便可以在vscode中运行React - 它将`sidebar/index.tsx`转换为`dist/`中的CSS/JS捆绑包。

```
npm run build
```

5. 按下 <kbd>F5</kbd> 运行项目。

这将启动一个启用了该扩展的新的VS Code实例。如果这不起作用，您可以按下 <kbd>Ctrl+Shift+P</kbd>，选择"Debug: Start Debugging"，然后选择"VS Code Extension Development"。

如果您想使用AI功能，您需要提供一个API密钥。您可以通过转到设置（Ctrl+,），键入"void"，并添加您想要使用的API密钥（例如，`"Anthropic Api Key"`环境变量）来执行此操作。"Which API"环境变量控制提供程序，默认为"anthropic"。

现在您已经设置好了，随时查看我们的[Issues](https://github.com/voideditor/void/issues)页面吧！

## 2. 构建完整的IDE

除了扩展，当我们需要访问更多功能时，我们偶尔会编辑IDE。如果您想要在完整的IDE上工作，请按照以下步骤进行，或查看VS Code的完整[如何贡献](https://github.com/microsoft/vscode/wiki/How-to-Contribute)页面。

在开始之前，请确保您已经构建了扩展（通过运行`cd .\extensions\void\`和`npm run build`）。同时确保您的系统上安装了Python。

确保您使用正确的NodeJS版本，如`.nvmrc`所示。

1. 安装所有依赖项。

```
npm install
```

2. 在VS Code中，按下<kbd>Ctrl+Shift+B</kbd>开始构建过程 - 这可能需要一些时间。如果您没有使用VS Code，请运行`npm run watch`。

3. 在终端中运行`./scripts/code.sh`。

这将在加载一段时间后打开构建好的IDE。要查看新的更改而无需重新启动构建，请使用<kbd>Ctrl+Shift+P</kbd>并运行"Reload Window"。

要打包IDE，请运行`npm run gulp vscode-darwin-arm64`。这是全部选项：`vscode-{win32-ia32 | win32-x64 | darwin-x64 | darwin-arm64 | linux-ia32 | linux-x64 | linux-arm}(-min)`。

如果您使用Windows，我们建议在开发容器中运行项目。VSCode应该会自动提示您这样做。

现在您已经设置好了，随时查看我们的[Issues](https://github.com/voideditor/void/issues)页面吧！

## 路线图

以下是我们路线图上最重要的主题。更多⭐代表更重要。

## ⭐⭐⭐ 改进差异。

我们定义"diff"为一个表示更改的单个绿色/红色对。以下是要进行的改进：

1. 显示删除（-）差异。目前我们只显示插入（+）差异。差异目前通过将所有新代码以绿色高亮显示和简单文本修饰来工作。相反，我们希望使用VS Code的本机代码。将diffEditor更改为显示差异（“内联”模式）。或者我们可以保留现有的内容，添加红色的删除代码区域以指示删除差异（-）。

2. 修复用户在差异上按下“接受”或“拒绝”时的错误行为。一个问题是，当一个差异被接受/拒绝时，下面的所有差异应该被更新（因为它们现在在不同的行号上）。还有其他杂项问题。

3. 使差异高亮动态化。目前，当用户编辑文本时，所有的差异和它们的高亮都会被清除。相反，我们应该更新差异的高亮显示。每个差异都存在于一系列行中，所有在该范围内或与之相交的变化都应该更新其高亮显示。

## ⭐⭐⭐ 构建光标样式的快速编辑（ctrl+k）。

当用户按下ctrl+k时，应该在他们选择的代码旁边内联显示一个输入框。这有点难以实现，因为单独的扩展不能做到这一点，需要在IDE中创建一个新组件。我们认为您可以修改vscode内置的“codelens”或“zone widget”组件，但我们也愿意接受其他方案。

## ⭐⭐⭐ 使历史记录正常工作。

当用户提交响应或按下应用/接受/拒绝按钮时，我们应该将这些事件添加到历史记录中，以允许用户撤消/重做它们。目前，如果用户尝试撤消或重做更改，则会出现意外行为。

## ⭐⭐⭐ 改进Ctrl+L后端。

目前，模型会输出整个文件。相反，我们应该更改提示，使模型输出部分更改，如`// ... 文件的其余部分`。当用户点击“应用”按钮时，模型应该重新编写文件，并将部分更改应用到正确的位置。

## ⭐⭐ 集成Ollama。

我们在扩展中编写了一个Ollama集成，但它出现了故障。这是因为Ollama具有Node.js依赖项，如'path'和'os'，这些依赖项无法在扩展中运行（扩展必须能够在浏览器中运行）。要解决此问题，我们需要将Void的扩展迁移到VS Code编辑器中以原生运行，以便我们可以访问Node.js。

## ⭐⭐⭐ 创新。

请随意构建超出标准光标功能的AI功能。例如，创建更好的代码搜索，或支持跨文件进行编辑和进行多个LLM调用的AI代理。

最终，我们希望建立一个方便的API来创建AI工具。该API将提供用于创建UI（显示自动完成建议或创建新差异）、检测事件更改（如`onKeystroke`或`onFileOpen`）以及修改用户文件系统（存储与每个文件相关联的索引）的方法，这将大大简化制作自己的AI插件。我们计划在未来的时间轴中进一步构建这些功能，但我们希望在这里列出它们以确保完整性。

## ⭐ 单星。

⭐ 当用户按下ctrl+L时，应清除侧边栏的状态。

⭐ 让用户通过侧边栏接受/拒绝整个文件中的所有差异。

⭐ 允许用户一次选择多个代码或文件。

⭐ 允许用户取消当前选择。

# 指南

请不要在未经与我们讨论的情况下进行大规模重构。我们希望保持代码库类似于vscode，这样我们就可以定期rebase，如果有重大更改，就会变得复杂。

# 提交拉取请求

一旦您进行了更改，请提交拉取请求。以下是一些建议：

- 一个PR应该涉及一个*单一*功能更改。更改的项目越少，PR被接受的可能性就越大。

- 您的PR应该包含一个描述，首先解释您做了什么，然后描述您所做的确切更改（以及更改的文件）。请不要使用模糊的语句，如“重构代码”或“改进类型”（而是描述您重构的代码，或者您更改的类型）。

- 您的标题应清楚地描述您所做的更改。

- 添加标签以帮助我们保持组织！

- 请不要为您的PR打开新问题。只需提交PR。

- 避免在同一个PR中进行重构和功能更改。

- 编写良好的代码。例如，当人们编辑Void的配置时常见的错误之一是在2个或更多的地方硬编码默认值，如`'claude-3.5'`。请遵循最佳实践，或者如果不得不妥协，请描述您的思路。

# 相关文件

我们跟踪我们与Void一起更改的所有文件，以便容易rebase：

- README.md
- CONTRIBUTING.md
- VOID_USEFUL_LINKS.md
- product.json

- src/vs/workbench/api/common/{extHost.api.impl.ts | extHostApiCommands.ts}
- src/vs/workbench/workbench.common.main.ts
- src/vs/workbench/contrib/void
- extensions/void

- .github/
- .vscode/settings
- .eslintrc.json
- build/hygiene.js
- build/lib/i18n.resources.json
- build/npm/dirs.js
