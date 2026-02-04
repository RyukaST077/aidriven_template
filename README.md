# 概要

このリポジトリはAIを十分に活用し、開発の効率を高めるためのテンプレートです。

## ディレクトリ構成

```
├── prompts/                    # AIへのプロンプトファイル
│   ├── 01_specify.md           # 要件定義・業務プロセス作成
│   ├── 02_plan.md              # アーキテクチャ・基本設計・機能一覧作成
│   ├── 03_detail_design.md     # 詳細設計作成
│   ├── 04_security_design.md   # セキュリティ設計作成
│   ├── 05_test_design.md       # テスト計画・テスト仕様作成
│   └── 06_release_operation.md # リリース・運用設計作成
├── templates/                  # 設計書テンプレート
│   ├── 01_Project_Design/      # プロジェクト設計テンプレート
│   └── 02_Detailed_Design/     # 詳細設計テンプレート
└── docs/                       # 作成した設計書の出力先
    ├── 01_Project_Design/
    └── 02_Detailed_Design/
```

## 開発手順

1. このリポジトリをクローン
2. 以下の順序でプロンプトファイルを使用し、AIと対話しながら設計書を作成

## プロンプトファイルの使い方

各プロンプトファイルは番号順に実行してください。前のフェーズの成果物が次のフェーズの入力となります。

### Step 1: 要件定義・業務プロセス（01_specify.md）

```
@01_specify.md を読んで、このプロジェクトの要件定義を始めてください。
```

**入力**: ユーザーからの要望、既存資料、ヒアリング内容  
**出力**: 
- `docs/01_Project_Design/01_Requirements.md`（要件定義書）
- `docs/01_Project_Design/02_Business_Process.md`（業務プロセス定義書）

---

### Step 2: アーキテクチャ・基本設計（02_plan.md）

```
@02_plan.md を読んで、アーキテクチャ設計を始めてください。
```

**入力**: Step 1で作成した要件定義書、業務プロセス定義書  
**出力**: 
- `docs/01_Project_Design/03_Architecture.md`（アーキテクチャ設計書）
- `docs/01_Project_Design/04_Basic_Design.md`（基本設計書）
- `docs/01_Project_Design/05_Feature_List.md`（機能一覧）

---

### Step 3: 詳細設計（03_detail_design.md）

```
@03_detail_design.md を読んで、詳細設計を始めてください。
```

**入力**: Step 2で作成した機能一覧、アーキテクチャ設計書、基本設計書  
**出力**: 
- `docs/02_Detailed_Design/06_Data_Design/`（データ設計）
- `docs/02_Detailed_Design/07_Screen_Design/`（画面設計）
- `docs/02_Detailed_Design/08_Interface_Design/`（外部IF設計）
- `docs/02_Detailed_Design/11_Module_Design/`（モジュール設計）

---

### Step 4: セキュリティ設計（04_security_design.md）

```
@04_security_design.md を読んで、セキュリティ設計を始めてください。
```

**入力**: アーキテクチャ設計書、基本設計書、業務プロセス定義書  
**出力**: 
- `docs/01_Project_Design/10_Security_Design.md`（セキュリティ設計書）

---

### Step 5: テスト設計（05_test_design.md）

```
@05_test_design.md を読んで、テスト計画を始めてください。
```

**入力**: 要件定義書、機能一覧、詳細設計  
**出力**: 
- `docs/01_Project_Design/12_Test_Plan.md`（テスト計画書）
- `docs/01_Project_Design/13_Test_Specs/`（テスト仕様書）

---

### Step 6: リリース・運用設計（06_release_operation.md）

```
@06_release_operation.md を読んで、リリース・運用設計を始めてください。
```

**入力**: アーキテクチャ設計書、基本設計書、セキュリティ設計書  
**出力**: 
- `docs/01_Project_Design/16_Release_Procedure.md`（リリース手順書）
- `docs/01_Project_Design/17_Operation_Design.md`（運用設計書）

---

## 設計フロー図

```
┌─────────────────┐
│  01_specify.md  │ ← ユーザー要望・既存資料
│  要件定義       │
└────────┬────────┘
         ▼
┌─────────────────┐
│   02_plan.md    │
│ アーキテクチャ  │
│   基本設計      │
└────────┬────────┘
         ▼
┌─────────────────┐
│03_detail_design │
│    詳細設計     │
└────────┬────────┘
         ▼
┌─────────────────┐
│04_security_design│
│ セキュリティ設計 │
└────────┬────────┘
         ▼
┌─────────────────┐
│ 05_test_design  │
│   テスト設計    │
└────────┬────────┘
         ▼
┌─────────────────┐
│06_release_operation│
│ リリース・運用   │
└─────────────────┘
```

## 注意事項

- 各プロンプトは **フェーズ制・ゲート方式** で進行します。AIが確認ゲートで質問してくるので、回答してから次に進んでください。
- 不明点がある場合、AIは推測せず質問します。曖昧なまま進めないでください。
- 作成した設計書は `docs/` 配下に出力されます。
- テンプレートを直接編集せず、`docs/` に出力されたファイルを編集してください。 