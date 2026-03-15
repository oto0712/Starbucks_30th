# ☕ スターバックス 群馬DC 限定ドリンクコレクションサイト

店舗限定ドリンクを巡るコレクションサイトです。  
**`index.html` 1ファイルで動作します。サーバー不要・APIキー不要。**

---

## 📁 ファイル構成

```
/
├── index.html   ← サイト本体（これだけでOK）
└── README.md    ← このファイル
```

---

## 🚀 GitHub Pages で公開する方法

1. このリポジトリを GitHub で開く
2. **Settings** → **Pages**
3. Branch: `main`、フォルダ: `/ (root)` を選択して **Save**
4. 数分後に `https://ユーザー名.github.io/リポジトリ名/` で公開されます

---

## ✏️ 編集ガイド

`index.html` を GitHub 上で直接編集する場合は、ファイルを開いて右上の **鉛筆アイコン (Edit)** をクリックしてください。  
編集後は **Commit changes** で保存します。

> **ポイント**: JS の `<script>` タグ内の先頭にある **CONFIG ブロック**と **DRINKS / STORES 配列** の2箇所を変更するだけで、サイトのほぼすべてをカスタマイズできます。

---

### [1] サイト基本情報 — `CONFIG` の上部

```js
var CONFIG = {
  siteTitle:    'Starbucks Coffee',       // ← ブラウザタブ・ヘッダーのタイトル
  campaignName: '群馬DC 限定ドリンク',    // ← キャンペーン名（イントロ画面・フッター）
  campaignSub:  'EAST GUNMA — COLLECTION 2026', // ← サブタイトル（イントロ画面）
  navBrand:     '☕ 群馬東地区 限定ドリンク',    // ← ナビバー左上のテキスト
```

---

### [2] ヒーロー（トップ画面）のテキスト

```js
  heroEyebrow: 'STARBUCKS COFFEE — 群馬 DC', // 上部バッジ
  heroTitle1:  '群馬DC',                       // 見出し1行目
  heroTitle2:  '限定ドリンク',                 // 見出し2行目（ゴールド色）
  heroTitle3:  'コレクション',                 // 見出し3行目
  heroLead:    '...全5種類の制覇を目指そう！', // リード文（<br>で改行可）
  heroNum1: { n: '5',  l: '限定ドリンク' },    // 数字カード1（n=数字, l=ラベル）
  heroNum2: { n: '13', l: '対象店舗' },         // 数字カード2
  heroNum3: { n: '3',  l: 'エリア' },           // 数字カード3
  totalDrinks: 5,  // ← ドリンク総数。DRINKSの件数と一致させること
```

---

### [3] 開催期間・エリア情報

HTML の `<!-- ✏️ 編集: 開催期間… -->` コメントの下にある **INFO セクション** を直接編集します。

```html
<!-- 開催期間 -->
<div class="period-dates">
  2025年4月3日<span>（木）</span><br>
  〜 2025年5月6日<span>（火）</span>     ← ここを変更
</div>

<!-- 開催中バッジ（終了後は「終了」などに変更） -->
<div class="info-period"><span class="dot"></span>開催中</div>
```

---

### [4] ドリンク情報 — `DRINKS` 配列

```js
const DRINKS = [
  {
    id:    0,                    // 変更しないこと（0〜totalDrinks-1）
    name:  'ドリンク名',         // ← カードに表示されるドリンク名
    desc:  '説明文',             // ← カードに表示される説明
    emoji: '🌿',                // ← 写真なし時のアイコン
    area:  '前橋エリア',         // ← エリア名（カード上部に表示）
    photo: 'https://...jpg',    // ← 画像URL（'' にすると絵文字表示）
    link:  'https://...',       // ← 詳細ページURL（'' でボタン非表示）
  },
  // ... id: 1, 2, 3, 4 と続く
];
```

**ドリンク数を変えたい場合：**
1. DRINKS の配列を追加/削除
2. `CONFIG.totalDrinks` を合わせて変更
3. ヒーローの `heroNum1.n`（ドリンク数）も更新
4. 進捗バーのHTMLテキスト `/ 5 種類制覇` も変更（HTML内検索）

---

### [5] 店舗情報 — `STORES` 配列

```js
const STORES = [
  {
    id:     1,                          // 1から始まる連番
    city:   '前橋市',                   // 市区町村名（フィルタータブに反映）
    name:   'けやきウォーク前橋店',     // 店舗名
    addr:   '前橋市 文京町2-1-1',       // 住所
    hours:  '10:00〜21:00',             // 営業時間
    lat:    36.379396,                  // 緯度（Google マップから取得）
    lng:    139.0783944,                // 経度
    drink:  0,                          // 販売ドリンクのid（0〜totalDrinks-1）
    mapUrl: '',                         // Google マップ共有URL（'' で自動生成）
  },
  // ... 続く
];
```

**緯度・経度の調べ方：**  
Google マップで店舗を右クリック → 座標が表示されます。

**店舗を追加する場合：**
```js
{ id: 14, city: '高崎市', name: '高崎○○店', addr: '高崎市...', hours: '8:00〜22:00', lat: 36.33, lng: 139.01, drink: 0, mapUrl: '' },
```

**フィルタータブも更新：** HTML内の `city-tabs` ブロックを検索して店舗数を変更
```html
<button class="ctab on" onclick="filterCity('all', this)">すべて（13）</button>  ← 13 を変更
```

---

### [6] 全制覇エフェクト（紙吹雪）の調整

```js
  confettiCount:    150,   // 数を減らすと軽くなる（目安: スマホ重い→80〜100）
  confettiSizeMin:  8,     // 最小サイズ(px)
  confettiSizeMax:  30,    // 最大サイズ(px)
  confettiDurMin:   1.8,   // 落下アニメ最短時間(秒)
  confettiDurMax:   4.6,   // 落下アニメ最長時間(秒)
  confettiDelayMax: 1.8,   // 出現ディレイ最大(秒)
  confettiColors: ['#CBA258', '#FFE566', '#ffffff', ...], // 色を追加/変更
  confettiShapes: ['★','✦','✧','◆','●','✿'],            // 形を変更
```

---

### [7] ヒーロー背景パーティクルの調整

```js
  particleCount:    80,     // 粒の数（増やすと密になる）
  particleSizeMin:  0.4,    // 最小半径(px)
  particleSizeMax:  2.2,    // 最大半径(px)
  particleSpeedMax: 0.0004, // 移動速度（大きいほど速い）
  particleAlphaMin: 0.15,   // 最小透明度
  particleAlphaMax: 0.75,   // 最大透明度
  particleColors: [
    'rgba(0,200,100,',   // 緑系
    'rgba(203,162,88,',  // ゴールド
    ...
  ],
```

> 注意: `rgba(R,G,B,` という形式で末尾のカンマまで含めること

---

### [8] 背景オーブ（光の玉）の調整 — CSS

`index.html` の `<style>` 内の `.orb1` 〜 `.orb5` を編集します。

```css
/* 例: orb1 の色を変える */
.orb1 {
  width: 600px; height: 600px;
  background: radial-gradient(circle at 40% 40%, rgba(0,180,100,.55), ...);
  /* ↑ rgba の最後の数値（.55）が濃さ。0〜1 で調整 */
}

/* アニメーション速度を変える */
.orb { animation: ... 5s ease-in-out infinite; }
/*                    ↑ 秒数を増やすと遅くなる */
```

---

### [9] マップの初期表示設定

```js
  mapCenter: { lat: 36.32, lng: 139.20 }, // 初期中心座標（群馬東部）
  mapZoom:   11,   // ズームレベル（大きいほど拡大。10〜13 が目安）
```

---

### [10] イントロアニメーションの時間

```js
  introDuration: 3200, // イントロ表示時間(ms)。速くしたいなら 2000
  introFadeOut:  800,  // フェードアウト時間(ms)
```

---

### [11] フッターの注意書き

```js
  footerNote1: '※掲載情報は予告なく変更になる場合があります。',
  footerNote2: '※限定ドリンクは各店舗の在庫状況により...', // ← 変更
```

---

## 🎨 色テーマの変更（CSS変数）

`index.html` の `:root` ブロックを編集します。

```css
:root {
  --gd:   #1E3932;  /* メイン背景（ダークグリーン）*/
  --gm:   #00704A;  /* アクセントグリーン */
  --gl:   #D4E9E2;  /* ライトグリーン */
  --gold: #CBA258;  /* ゴールド */
  --gold2:#E8C97A;  /* ライトゴールド */
  --cream:#F2F0EB;  /* クリーム（明るいセクション背景）*/
  --ww:   #FDFAF5;  /* オフホワイト */
}
```

---

## ❓ よくある問題

| 症状 | 原因 | 対処 |
|------|------|------|
| マップにピンが出ない | Leafletのサイズ未計算 | ページをスクロールしてマップを表示エリアに入れる |
| ルート生成ができない | 店舗が未選択 | ドロップダウンから店舗を選んでから「ルートを生成」 |
| 画像が表示されない | URLが無効 or CORS制限 | 別の画像URLを試すか `''` に戻す |
| スマホでナビが出ない | 幅700px以下でハンバーガー表示 | ≡ ボタンをタップ |
| 編集後に壊れた | 構文ミス | GitHub History から前バージョンに戻す |

---

## 📝 新しいキャンペーンへの使い回し手順

1. `DRINKS` を新しいドリンク情報に書き換え
2. `STORES` を新しい店舗情報に書き換え
3. `CONFIG.totalDrinks` を合わせて変更
4. `CONFIG.campaignName` / `campaignSub` を変更
5. INFO セクションの開催期間テキストを更新
6. ヒーローの数字 (`heroNum1`〜`3`) を更新
7. `localStorage` キー `KEY` の末尾バージョン番号を上げる（例: `v4` → `v5`）  
   → これで前回のコレクションデータがリセットされます

---

*Built with ❤️ — index.html single file, no server required*
