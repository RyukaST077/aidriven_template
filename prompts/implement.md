---
name: implement
description: タスクファイルに基づいてPRの実装を完了し、受け入れ基準を満たした状態でコミットする。skills(prereq-check), skills(acceptance-check), skills(commit) を連携して使用する。
---

# タスク実装

## 目的
`$TASK_FILE` の `$PR_NUM` を実装し、受け入れ基準を満たした状態でコミットする。

## 入力変数
- `$TASK_FILE`: タスクが記載されたファイル（例: `_tasks/task.md`）
- `$PR_NUM`: 対象PR識別子（例: `PR-001`）

## ワークフロー

### 1. タスク確認
`$TASK_FILE` を読み込み、`$PR_NUM` の実装内容を把握する。

### 2. 前提条件チェック
`skills(prereq-check)` を実行し、`$PR_NUM` の前提条件を確認する。
- 結果が `clear` → Step 3 へ進む
- 結果が `blocked` → 前提PRを先に完了する必要あり（エラー終了）

### 3. 実装
タスクファイルの「実行タスク」「変更予定ファイル」に従い実装を行う。
- コードの品質とベストプラクティスに従う
- 必要に応じてテストも実装する

### 4. 受け入れ基準チェック
`skills(acceptance-check)` を実行し、`$PR_NUM` の受け入れ基準を検証する。
- 合格 → Step 5 へ進む
- 不合格 → Step 3 に戻り修正

### 5. コミット
`skills(commit)` を実行してコミットする。
- コミットメッセージは**日本語**で記述すること

### 6. アーカイブ（最終PRの場合のみ）
`$PR_NUM` がタスクリストの最後のPRである場合:
- タスクファイルを `_tasks/archive/` に移動する

## 制約条件（厳守）
1. **継続実行**: skills実行後も作業を中断せず、完了まで続けること
2. **コミットメッセージ**: 必ず日本語で記述すること
3. **品質保証**: 受け入れ基準を満たさない限りコミットしないこと
4. **ループ制御**: Step 3〜4 は `$PR_NUM` が完了するまで繰り返すこと

## 使用例

```
ユーザー入力:
  /implement TASK_FILE=_tasks/feature-auth.md PR_NUM=PR-001

期待動作:
  1. _tasks/feature-auth.md の PR-001 を確認
  2. skills(prereq-check) → clear
  3. 認証機能を実装
  4. skills(acceptance-check) → 合格
  5. skills(commit) → 「feat: ユーザー認証機能を追加」でコミット
  6. 完了（最後のPRなら _tasks/archive/ へ移動）
```
