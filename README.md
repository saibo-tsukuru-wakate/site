# 「細胞を創る」研究会 若手の会 — Webサイト

## フォルダ構成

```
site/
├── index.html      ← トップページ（About・イベント・お問い合わせ）
├── members.html    ← メンバー紹介（表形式）
├── joinus.html     ← 参加するには（対象者・ステップ・FAQ）
├── privacy.html    ← プライバシーポリシー
├── style.css       ← 共通スタイル（全ページで共有）
├── images/         ← 画像置き場（自分で作成してください）
└── README.md       ← このファイル
```

## ローカルで確認する方法

1. `index.html` をブラウザにドラッグ＆ドロップ、またはダブルクリック
2. それだけで動きます！

※ スクロールアニメーション（AOS）とフォントはインターネット接続が必要です
  （CDNから読み込んでいるため）


## GitHub Pages へのデプロイ手順

### 初回セットアップ

1. GitHub でリポジトリを作成（例: `cellcreate-wakate`）
2. ローカルのサイトフォルダで以下を実行：

```bash
cd site
git init
git add .
git commit -m "初回リリース"
git branch -M main
git remote add origin https://github.com/ユーザー名/リポジトリ名.git
git push -u origin main
```

3. GitHub のリポジトリ → Settings → Pages
4. Source を「Deploy from a branch」→「main」→「/ (root)」に設定
5. 数分後に `https://ユーザー名.github.io/リポジトリ名/` で公開

### 更新するとき

```bash
git add .
git commit -m "○○を更新"
git push
```
push 後、1〜2分で自動的にサイトに反映されます。


## ⚠ GitHub Pages の注意点

### ファイルパスについて
- GitHub Pages ではファイル名の**大文字・小文字が区別されます**
  - `Members.html` と `members.html` は別ファイル扱いです
  - すべて**小文字**で統一するのが安全です
- リンクは**相対パス**（`members.html`）で書いてください
  - `C:\Users\...` のようなローカルパスは使えません
- 画像ファイル名にも日本語や空白を含めないでください
  - ○ `tanaka.jpg`　× `田中 太郎.jpg`

### 公開範囲について
- GitHub Pages で公開すると**インターネット上の誰でもアクセス可能**です
- リポジトリを **Private** にしても GitHub Pages 自体は公開されます
  - ※ Private リポジトリで GitHub Pages を使うには有料プラン（Pro 以上）が必要です
- メンバーの個人情報（メールアドレスなど）を載せる場合はご注意ください

### カスタムドメイン（独自ドメイン）
- `xxx.github.io` の代わりに独自ドメインを使いたい場合：
  1. ドメインを取得（お名前.com、Google Domains 等）
  2. DNS に CNAME レコードを設定
  3. Settings → Pages → Custom domain にドメインを入力
  4. 「Enforce HTTPS」にチェック

### Google Analytics を使う場合
- `privacy.html` にアクセス解析に関する記載を入れてあります
- Google Analytics のトラッキングコードは各 HTML の `</head>` 直前に挿入してください
- Cookie の利用について告知が必要です（プライバシーポリシーに記載済み）

### Jekyll について
- GitHub Pages はデフォルトで Jekyll（静的サイトジェネレータ）が動きます
- このサイトは純粋な HTML/CSS なので Jekyll は不要です
- リポジトリのルートに `.nojekyll` という空ファイルを置くと
  Jekyll の処理をスキップしてデプロイが速くなります：

```bash
touch .nojekyll
git add .nojekyll
git commit -m "Jekyll 無効化"
git push
```


## ページの追加方法

1. 既存の HTML ファイル（`joinus.html` がテンプレートとして使いやすい）をコピー
2. ファイル名を変更（例: `events.html`）
3. `<title>` を変更
4. ナビゲーションの `class="current"` を移動
5. ヒーローセクションのタイトルを変更
6. 中身を編集
7. **全ページのナビゲーション**に新しいリンクを追加（これを忘れると遷移できません）


## メンバーの追加方法（members.html）

テーブルの `<tbody>` 内に `<tr>` ブロックを追加：

```html
<tr>
  <td class="name-cell">名前</td>
  <td>所属</td>
  <td><span class="role">役割</span></td>
  <td>専門キーワード</td>
  <td><a href="https://researchmap.jp/ユーザーID" target="_blank" rel="noopener" class="rm-link">researchmap ↗</a></td>
</tr>
```

researchmap がない場合は `<td>—</td>` としてください。


## 色・フォントの変更

`style.css` 先頭の `:root { }` 内を変更：

```css
:root {
  --c-primary: #0f9b8e;        /* メインカラー */
  --c-primary-light: #5ce0d2;  /* メインカラー（明） */
  --c-dark: #16213e;           /* ダークカラー */
  ...
}
```


## スクロールアニメーション（AOS）の使い方

```html
<div data-aos="fade-up">ふわっと上に</div>
<div data-aos="fade-right">右からスライド</div>
<div data-aos="zoom-in">拡大しながら表示</div>
<div data-aos="fade-up" data-aos-delay="200">200ms 遅延</div>
```


## 更新履歴

| 日付 | 内容 |
|------|------|
| 2026-03-28 | 初版リリース：トップページ、メンバー（表形式）、参加するには、プライバシーポリシー |
<!-- ★ 更新したらここに行を追加してください
| 2026-04-xx | ○○ページを追加 |
| 2026-04-xx | メンバー情報を更新 |
-->
