# ToDo アプリ

Next.js を用いて構築するシンプルなタスク管理アプリです。タスクの追加・編集・削除・完了管理が可能で、発展的にクラウド保存や認証機能にも対応できる設計を想定しています。

---

## 概要

- フロントエンド: [Next.js](https://nextjs.org/) (App Router)
- 言語: TypeScript
- スタイリング: Tailwind CSS
- データ保存
  - MVP: ブラウザの `localStorage`
  - 拡張: Next.js API Routes + SQLite / PostgreSQL / Supabase

---

## 機能

### 必須機能（MVP）

- タスクの追加（タイトル・期限・メモ）
- タスク一覧表示（未完了/完了切替）
- タスク編集（タイトル・期限・メモ更新）
- タスク削除
- 完了フラグ（チェックボックス）

### 発展機能（任意）

- タスクのフィルタリング（すべて / 未完了 / 完了）
- ソート（期限日順 / 作成日順）
- タスク検索（タイトル・メモ部分一致）
- ユーザー認証（NextAuth.js: Google, GitHub OAuth）
- クラウド保存（Supabase / Firebase）

---

## データモデル

```ts
type Task = {
  id: string; // UUID
  title: string; // タスク名
  description?: string; // メモ
  dueDate?: Date; // 期限日
  completed: boolean; // 完了状態
};
```

## 画面構成

- ホーム画面
  - タスク追加フォーム
  - タスク一覧
- 編集モーダル
- ログイン画面（拡張）

## 今後の拡張

- タグ機能
- プッシュ通知

---

## 開発フロー（GitHub Flow）

- メインブランチは `main`（直接コミットは避ける）
- 作業は `main` からブランチ作成：`feature/<短い説明>` / `fix/<短い説明>` / `chore/<短い説明>`
- 早めに Pull Request を作成し、目的・変更点・確認手順・スクリーンショット（UI 変更時）を記載
- Lint/ビルドが通り、レビュー承認後に「Squash and merge」で `main` へマージ
- マージ後は作業ブランチを削除
