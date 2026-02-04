# セキュリティガイドライン

## 必須のセキュリティチェック

任意のコミット前：
- [ ] ハードコードされたシークレット無し（API キー、パスワード、トークン）
- [ ] すべてのユーザー入力を検証
- [ ] SQL インジェクション対策（パラメータ化クエリ）
- [ ] XSS 対策（HTML サニタイズ）
- [ ] CSRF 対策有効
- [ ] 認証/認可を確認
- [ ] すべてのエンドポイントにレート制限
- [ ] エラーメッセージが機密データを漏らさない

## シークレット管理

```typescript
// NEVER: Hardcoded secrets
const apiKey = "sk-proj-xxxxx"

// ALWAYS: Environment variables
const apiKey = process.env.OPENAI_API_KEY

if (!apiKey) {
  throw new Error('OPENAI_API_KEY not configured')
}
```

## セキュリティ対応プロトコル

セキュリティ問題が見つかった場合：
1. 即座に STOP
2. **security-reviewer** エージェントを使用
3. 続行前に CRITICAL 問題を修正
4. 露出したシークレットをローテーション
5. 類似の問題がないかコードベース全体を確認
