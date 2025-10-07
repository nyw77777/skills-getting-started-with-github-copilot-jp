
https://learn.microsoft.com/ja-jp/visualstudio/ide/visual-studio-github-copilot-extension?view=vs-2…
GitHub Copilot for Visual Studio を取得する
Visual Studio 2022 バージョン 17.10 以降では、 統合された GitHub Copilot 拡張機能 が Visual Studio インストーラーの推奨コンポーネントとして使用できます。 既定では、インストール中に除外することを選択しない限り、すべてのワークロードでインストールされます。

→ Visual Studio 2022でバージョン 17.10 以降なら特に拡張機能の追加インストールは不要のようです。

# Playwright - Web Testing and Automation F...、Masaru Takahashi が作成

Masaru Takahashi (外部)
16:57

# Playwright - Web Testing and Automation Framework

 

## プロジェクト概要

 

Playwrightは、Chromium、Firefox、WebKitの3つのブラウザエンジンに対応したWeb Testing & Automation フレームワークです。クロスブラウザーでの統一されたAPIを提供し、信頼性が高く高速なE2Eテストの作成を可能にします。

 

- **対応ブラウザ**: Chromium (141.0.7390.37), Firefox (142.0.1), WebKit (26.0)

- **対応プラットフォーム**: Linux, macOS, Windows

- **言語バインディング**: TypeScript/JavaScript, Python, .NET, Java

- **Node.js要件**: 18以上 (推奨20以上)

 

## フォルダー構造

 

```

playwright/

├── packages/                     # NPMワークスペース構成のパッケージ群

│   ├── playwright/               # メインのPlaywright Test

│   ├── playwright-core/          # Playwrightコアライブラリ（ブラウザAPI）

│   ├── playwright-ct-*/          # コンポーネントテスト関連パッケージ

│   ├── html-reporter/            # HTMLレポート機能

│   ├── trace-viewer/             # トレースビューア

│   └── ...                       # その他の専門パッケージ

├── tests/                        # テストスイート

│   ├── library/                  # ライブラリ（非test runner）のテスト

│   ├── playwright-test/          # test runnerのテスト

│   ├── android/                  # Androidテスト

│   ├── electron/                 # Electronテスト

│   └── ...

├── docs/src/                     # APIドキュメントソース（Markdownから自動生成）

├── utils/                        # ビルドとメンテナンス用ユーティリティ

├── browser_patches/              # ブラウザパッチ（Chromium/Firefox/WebKit）

└── examples/                     # 使用例とサンプルコード

```

 

## ビルドと開発環境セットアップ

 

### 初期セットアップ

```bash

# Node.js 20以上が必要

node --version

 

# リポジトリのクローン

git clone https://github.com/microsoft/playwright

cd playwright

 

# 依存関係のインストールとビルド（ウォッチモード）

npm ci

npm run watch

npx playwright install

```

 

### 開発用コマンド

 

**ビルドとリント**

```bash

npm run watch           # ウォッチモードでビルド（開発時に常時実行推奨）

npm run build          # ワンタイムビルド

npm run lint           # 全体のリンターチェック（eslint + tsc + doc + deps）

npm run flint          # 高速リンター（並列実行）

```

 

**テスト実行**

```bash

# ライブラリテスト（API関連）

npm run ctest          # Chromiumのみ（高速）

npm run test           # 全ブラウザ（フル）

npm run ftest          # Firefox

npm run wtest          # WebKit

 

# Test runnerテスト

npm run ttest          # Test runner機能のテスト

 

# 専門テスト

npm run atest          # Android

npm run etest          # Electron

npm run ct             # コンポーネントテスト

```

 

**注意事項**

- `npm run watch`を実行中は、TypeScript型定義などが自動生成されるため、生成されたファイルを直接編集しないこと

- `docs/src`でAPIドキュメントを編集すると、関連ファイルが自動生成される

 

## コーディング標準とベストプラクティス

 

### コーディングスタイル

- ESLint設定は`eslint.config.mjs`で完全に定義済み

- TypeScript を使用し、厳格な型チェックを適用

- コメントは明確な目的を持ち、コードの理解を助けるもののみ記述

- 自明でないコードにはコメントより可読性の高いコードに書き直すことを優先

 

### Commit メッセージフォーマット

[Conventional Commits](https://www.conventionalcommits.org/)に従う：

```

label(namespace): title

 

description

 

footer

```

 

**label**:

- `fix`: バグ修正

- `feat`: 新機能

- `docs`: ドキュメントのみの変更

- `test`: テストのみの変更

- `devops`: CI/ビルドの変更

- `chore`: その他

 

例：

```

feat(trace viewer): network panel filtering

 

This patch adds a filtering toolbar to the network panel.

 

Fixes #123, references #234.

```

 

### テスト要件

- 新機能や変更には必ずテストを追加

- テストは独立性（hermetic）を保つこと

- 外部サービスに依存しないこと

- 全プラットフォーム（macOS, Linux, Windows）で動作すること

 

## 依存関係とツール

 

### 主要フレームワーク・ライブラリ

- **TypeScript**: 厳格な型システム

- **ESLint**: コードスタイル・品質チェック

- **Vite**: ビルドツール（HMR対応）

- **React**: UI コンポーネント（trace-viewer等）

- **esbuild**: 高速バンドラー

 

### ブラウザエンジン

- Chromium（パッチ適用版）

- Firefox（Juggler protocol使用）

- WebKit（パッチ適用版）

 

### 特殊な開発環境

```bash

# HMR（Hot Module Replacement）開発モード

PW_HMR=1 npm run watch

PW_HMR=1 npx playwright show-trace

PW_HMR=1 npm run ctest -- --ui

```

 

## 重要な設定ファイル

 

- `package.json`: ワークスペース設定とスクリプト定義

- `eslint.config.mjs`: ESLint設定

- `tsconfig.json`: TypeScript設定

- `tests/*/playwright.config.ts`: 各テストスイートの設定

- `utils/`: ビルド・生成・チェック用ユーティリティ

 

## APIドキュメントとコード生成

 

- API仕様は`docs/src`で管理され、TypeScript型定義が自動生成される

- 公開APIには必ず`docs/src`でのドキュメント作成が必要

- `npm run watch`実行中は変更が自動的に関連ファイルに反映される

 

## カスタムブラウザビルドでのテスト

 

```bash

# カスタムブラウザパスを指定してテスト実行

CRPATH=<path-to-executable> npm run ctest

WKPATH=<path-to-executable> npm run wtest

FFPATH=<path-to-executable> npm run ftest

 

# デバッグ用

DEBUG=pw:browser npm run ctest

```

 

## 新しい依存関係について

 

新しい依存関係の追加には非常に高いハードルがあります。依存関係の追加や更新を行う前に、必ずissueで議論し、メンテナーからの承認を得てください。

 

## プルリクエストガイドライン

 

- 必ずissueが関連付けられていること（軽微なドキュメント更新を除く）

- 初回貢献者は`open-to-a-pull-request`ラベル