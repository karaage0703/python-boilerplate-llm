# Python-Boilerplate-LLM

このリポジトリはAIコーディングツール（Cline/Cursor等）を活用したPythonプロジェクト開発のためのボイラープレートです。LLMが設計書を自動生成し、それに基づいて実装を行うワークフローを前提としています。

## 機能

- LLMによる設計書自動生成と実装の一貫したワークフロー
- 設計書テンプレート（docs/design.md.sample）をベースにLLMが要件に合わせた設計書を作成
- uvを使用した仮想環境管理
- src/とtests/ディレクトリによる構造化
- メインプログラムのエントリーポイント
- pytestを使用したテスト例

## 使い方

### 開発環境のセットアップ

#### 方法1: ローカル環境

1. uvによる仮想環境の作成とパッケージのインストール:

```bash
uv venv
```

2. 開発用パッケージのインストール:

```bash
uv pip install -r requirements.txt
```

#### 方法2: DevContainer

VS Codeユーザーの場合、DevContainerを使用した開発環境が利用可能です：

1. VS CodeでDevContainerを開く:
   - `F1` → `Dev Containers: Reopen in Container`
   - または通知からコンテナで再開を選択

2. 自動的にDocker環境がセットアップされ、Pythonの開発環境が構築されます

### メインプログラムの実行

```bash
python -m src.main
```

### LLMを活用した開発ワークフロー

このボイラープレートは、AIコーディングツール（Cline/Cursor/Claude Code等）を活用した以下の開発ワークフローを前提としています：

1. プロジェクトの要件をLLMに伝える
2. LLMが`docs/design.md.sample`テンプレートをベースに、要件に合わせた`docs/design.md`を自動生成
3. 生成された設計書に基づいて、LLMがコードを実装
4. テストコードの作成と実行

このワークフローにより、要件定義から実装までの一貫性が保たれ、効率的な開発が可能になります。

#### LLMへの指示例

```
このリポジトリを使って、以下の要件のプロジェクトを実装してください。

<プロジェクトの要件>

docs/design.md.sample をベースに設計書を作成し、その設計に基づいて実装を行ってください。
```

## テスト

テストの実行:

```bash
pytest
```

## 設計書テンプレート

`docs/design.md.sample`には、プロジェクトの要件定義から設計、開発工程までを体系的に記述するためのテンプレートが含まれています。このテンプレートは以下の特徴を持っています：

- 要件定義セクション（基本情報、プロジェクト概要、機能要件、非機能要件など）
- システム設計セクション（アーキテクチャ、クラス設計、データフロー、エラーハンドリングなど）
- 開発工程セクション（フェーズ、マイルストーン、リスク管理など）

LLMはこのテンプレートを参照し、ユーザーから提供された要件に基づいて具体的な設計書を自動生成します。ユーザーは生成された設計書を確認し、必要に応じて調整を依頼できます。

## プロジェクト構造

```
.
├── docs/               # ドキュメント
│   └── design.md.sample  # 設計書テンプレート（LLMが参照）
├── src/                # ソースコード
│   ├── __init__.py
│   └── main.py         # メインエントリーポイント
├── tests/              # テストコード
│   ├── conftest.py
│   └── test_main.py    # メインモジュールのテスト
├── .devcontainer/      # DevContainer設定ファイル
│   ├── devcontainer.json
│   ├── docker-compose.yml
│   └── Dockerfile
├── .claude/            # Claude Code設定
│   └── settings.local.json
├── rules.md            # コーディングルール
├── .gitignore          # Git無視ファイル設定
├── LICENSE             # ライセンスファイル
├── README.md           # このファイル
└── requirements.txt    # 依存関係
```

## ライセンス

このプロジェクトは[MITライセンス](LICENSE)の下で公開されています。詳細については[LICENSE](LICENSE)ファイルを参照してください。
