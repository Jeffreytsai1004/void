# 有用なリンク

[English](./VOID_USEFUL_LINKS.md) | [中文](./VOID_USEFUL_LINKS_CN.md) | [日本語](./VOID_USEFUL_LINKS_JP.md)

VoidチームはVSCodeのソースコードを使い始めるためのリンクリストをまとめました。お役に立てば幸いです！

## 初心者 / はじめに

- [VSCode UIガイド](https://code.visualstudio.com/docs/getstarted/userinterface) - 補助バー、パネルなどについて説明しています。

- [UXガイド](https://code.visualstudio.com/api/ux-guidelines/overview) - コンテナ、ビュー、アイテムなどについて説明しています。

## 貢献

- [VS Codeのソースコードの構成方法](https://github.com/microsoft/vscode/wiki/Source-Code-Organization) - エントリーポイントファイルの場所、`browser/`と`common/`の意味などを説明しています。これはこのリスト全体で最も重要な読み物です！全体を読むことをお勧めします。

- [VSCodeに組み込まれているすべてのコマンド](https://code.visualstudio.com/api/references/commands) - 参照用に時々役立ちます。

## VSCodeの拡張機能API

Voidは現在主に拡張機能であり、これらのリンクはセットアップに非常に役立ちました。

- [拡張機能に必要なファイル](https://code.visualstudio.com/api/get-started/extension-anatomy)。

- [拡張機能の`package.json`スキーマ](https://code.visualstudio.com/api/references/extension-manifest)。

- ["Contributes"ガイド](https://code.visualstudio.com/api/references/contribution-points) - `package.json`の`"contributes"`部分は拡張機能がどのようにマウントされるかを示しています。

- [完全なVSCode拡張機能API](https://code.visualstudio.com/api/references/vscode-api) - 右側で構成を確認してください。ページの[下部](https://code.visualstudio.com/api/references/vscode-api#api-patterns)は見逃しやすいですが、キャンセルトークン、イベント、破棄可能なリソースなど、有用な情報があります。

- `package.json`で定義できる[アクティベーションイベント](https://code.visualstudio.com/api/references/activation-events)（あまり有用ではありません）
