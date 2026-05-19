# WordPress ギャラリーアップロード手順

## フォルダ構成

```
mosaic-gallery/
├── index.html          ← ギャラリーサイト本体
└── images/
    ├── artcafe/        (11枚)
    ├── bella/          (9枚)
    ├── cooper/         (9枚)
    ├── luna/           (8枚)
    ├── mashroom/       (10枚)
    ├── shine_hills/    (10枚)
    ├── sparkle/        (8枚)
    ├── tulip-mania/    (10枚)
    └── twinkle/        (8枚)
    合計 83枚
```

---

## 方法A：スタンドアロンページとして使う（最も簡単）

### 手順
1. `mosaic-gallery` フォルダごとWordPressサーバーにFTPでアップロード
   - アップロード先例: `/public_html/gallery/`
2. ブラウザで `https://あなたのドメイン/gallery/` にアクセスして確認

---

## 方法B：WordPressのメディアライブラリ＋カスタムHTMLページ

### ステップ1：画像をメディアライブラリにアップロード
1. WordPress管理画面 → **メディア → 新規追加**
2. 9フォルダの画像を一括ドラッグ＆ドロップ（83枚）
3. 各画像の **URL（フルサイズ）** をメモするか、後でHTMLを書き換え

### ステップ2：固定ページを作成
1. WordPress管理画面 → **固定ページ → 新規追加**
2. ページ名：「デザインギャラリー」など
3. エディター右上の「…」→ **コードエディター** に切り替え
4. `index.html` の `<main>〜</main>` の中身を貼り付け
5. `<style>` タグ内のCSSは、テーマの `style.css` に追記するか、
   プラグイン「Simple Custom CSS」で追加する

### ステップ3：画像パスの書き換え（方法Bのみ必要）
- `index.html` 内の `images/artcafe/brown_artcafe-cropped.png` のような相対パスを
  WordPressのメディアURLに置き換える
- 例: `https://あなたのドメイン/wp-content/uploads/2026/05/brown_artcafe-cropped.png`

---

## 方法C：iframeで埋め込む（最も手軽）

方法Aでサーバーに置いた後、WordPressの任意のページに下記を貼るだけ：

```html
<iframe 
  src="https://あなたのドメイン/gallery/" 
  width="100%" 
  height="900px" 
  style="border:none;"
></iframe>
```

---

## index.html の機能

- 9コレクション×カラーバリエーション表示
- クリックで拡大ライトボックス（← → キーで切り替え）
- スクロール連動ナビゲーション
- スマホ対応（レスポンシブ）
- 遅延読み込み（loading="lazy"）で高速表示
