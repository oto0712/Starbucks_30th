# ☕ スターバックス 群馬DC 限定ドリンクコレクションサイト

`index.html` 1ファイルで動作。サーバー不要・APIキー不要。  
**このREADMEを読めば、サイトのすべてを自分で編集できます。**

---

## 🚀 GitHub Pages で公開する手順

1. このリポジトリの **Settings → Pages**
2. Branch: `main`、フォルダ: `/ (root)` → **Save**
3. 数分後に `https://ユーザー名.github.io/リポジトリ名/` で公開

---

## ✏️ GitHub 上での編集方法

1. `index.html` を開く
2. 右上の **✏️ 鉛筆アイコン（Edit this file）** をクリック
3. 編集する
4. 右上の **Commit changes** で保存

> 壊してしまった場合: **History（📜アイコン）** から以前のバージョンに戻せます。

---

## 📋 編集箇所の全一覧

`index.html` の `<script>` タグ内の先頭に **CONFIG ブロック**と **DRINKS / STORES 配列**があります。  
HTMLの直接編集が必要な箇所には `<!-- ✏️ 編集: -->` コメントが入っています。

---

## [1] ブラウザタブのタイトル

**場所:** `<head>` 内

```html
<title>群馬DC 限定ドリンク | Starbucks Coffee</title>
```

---

## [2] サイト基本情報 — `CONFIG` ブロック

```js
var CONFIG = {
  siteTitle:    'Starbucks Coffee',             // イントロ画面の大タイトル
  campaignName: '群馬DC 限定ドリンク',          // イントロ画面・フッターのキャンペーン名
  campaignSub:  'EAST GUNMA — COLLECTION 2026', // イントロ画面のサブタイトル
  navBrand:     '☕ 群馬東地区 限定ドリンク',   // ナビバー左上のテキスト
```

---

## [3] ヒーロー（トップ画面）

**場所:** `CONFIG` ブロック内

```js
  heroEyebrow: 'STARBUCKS COFFEE — 群馬 DC', // 見出し上のバッジ文字
  heroTitle1:  '群馬DC',                       // H1 見出し 1行目
  heroTitle2:  '限定ドリンク',                 // H1 見出し 2行目（ゴールド色）
  heroTitle3:  'コレクション',                 // H1 見出し 3行目
  heroLead:    '各店舗でしか飲めない、<br>店舗限定ドリンクが登場。全5種類の制覇を目指そう！',
  //           ↑ <br> で改行できる
  heroNum1: { n: '5',  l: '限定ドリンク' },   // ヒーロー下の数字カード1（n=数字, l=ラベル）
  heroNum2: { n: '13', l: '対象店舗' },        // 数字カード2
  heroNum3: { n: '3',  l: 'エリア' },          // 数字カード3
  totalDrinks: 5,  // ドリンクの総数（DRINKS配列の件数と必ず一致させる）
```

> **注意:** `totalDrinks` を変えたら、HTML内の `/ 5 種類制覇` も検索して変更してください。

---

## [4] フッターの注意書き

**場所:** `CONFIG` ブロック内

```js
  footerNote1: '※掲載情報は予告なく変更になる場合があります。',
  footerNote2: '※限定ドリンクは各店舗の在庫状況により販売終了となる場合があります。',
```

---

## [5] 開催情報セクション

**場所:** HTML の `<section id="info">` 内。直接テキストを編集します。

### 開催期間の日付

```html
<div class="period-dates">
  2025年4月3日<span>（木）</span><br>
  〜 2025年5月6日<span>（火）</span>   ← 実際の日付に変更
</div>
```

### 開催中バッジ

```html
<div class="info-period"><span class="dot"></span>開催中</div>
<!-- 終了後は「開催中」→「終了」に変更 -->
<!-- 点滅ドットを消す場合は <span class="dot"></span> を削除 -->
```

### 開催エリアのリスト

```html
<ul>
  <li>前橋エリア（前橋市内 3店舗）</li>      ← エリア名・店舗数を変更
  <li>伊勢崎西エリア（伊勢崎市西部 3店舗）</li>
  ...
</ul>
```

### ドリンクについて・注意事項

同じ `<section id="info">` 内の各 `<ul>` リストを直接編集します。

---

## [6] 参加方法（How to）セクション

**場所:** HTML の `<section id="howto">` 内。

```html
<div class="step rv s1">
  <div class="step-n">01</div>
  <span class="step-ico">🗺️</span>    ← 絵文字を変更
  <h3>マップを確認</h3>               ← 見出しを変更
  <p>販売店舗セクションから...</p>    ← 説明文を変更
</div>
```

4ステップ（s1〜s4）の絵文字・見出し・説明文を変更できます。

---

## [7] ドリンクセクション

### セクション見出し

```html
<div class="sec-eye">Drink Collection</div>
<h2 class="sec-ttl">限定<em>ドリンク</em></h2>    <!-- <em>タグ内がグリーン色 -->
<p class="sec-note">☝️ 飲んだドリンクカードをタップしてコレクションしよう！</p>
```

### 全制覇バナー

```html
<h3>全5種類制覇おめでとうございます！</h3>
<p>限定ドリンクを全種類制覇しました！<br>ぜひ友達にもシェアしてください ☕</p>
<button ...>🎉 シェアカードを開く</button>
```

---

## [8] ドリンク情報 — `DRINKS` 配列

```js
const DRINKS = [
  {
    id:    0,                           // 変更しない（0〜totalDrinks-1 の連番）
    name:  'シュークリーム フラペチーノ®',  // ドリンク名
    desc:  'カスタードフレーバー...',       // 説明文（ドリンクカードに表示）
    emoji: '🌿',                        // 写真なし時のアイコン絵文字
    area:  '前橋エリア',                // エリア名（カード上部・ルート提案に使用）
    photo: 'https://...jpg',            // 商品画像URL（'' にすると絵文字表示）
    link:  '',                          // 詳細ページURL（'' でボタン非表示）
  },
  // id: 1, 2, 3, 4 と続く
];
```

**ドリンク数を増減する手順:**
1. `DRINKS` 配列を追加/削除
2. `CONFIG.totalDrinks` を合わせて変更
3. HTML内の `/ 5 種類制覇` を検索して数字を変更
4. `heroNum1.n`（ヒーローの数字）も更新

---

## [9] 店舗情報 — `STORES` 配列

```js
const STORES = [
  {
    id:     1,                        // 1から始まる連番
    city:   '前橋市',                 // 市区町村名（フィルタータブ・マップ色分けに使用）
    name:   'けやきウォーク前橋店',   // 店舗名
    addr:   '前橋市 文京町2-1-1',     // 住所
    hours:  '10:00〜21:00',           // 営業時間
    lat:    36.379396,                // 緯度
    lng:    139.0783944,              // 経度
    drink:  0,                        // 販売ドリンクのid（DRINKSのidと一致させる）
    mapUrl: '',                       // Google マップ共有URL（'' で住所から自動生成）
  },
];
```

**緯度・経度の調べ方:**
Google マップで店舗を開き、ピン長押し（スマホ）または右クリック（PC）→ 座標をコピー

**店舗を追加する場合:**
```js
{ id: 14, city: '高崎市', name: '高崎○○店', addr: '高崎市...', hours: '8:00〜22:00', lat: 36.33, lng: 139.01, drink: 0, mapUrl: '' },
```

**フィルタータブの数も更新（HTML内を検索）:**
```html
<button ... onclick="filterCity('all', this)">すべて（13）</button>  ← 13 を変更
<button ... onclick="filterCity('前橋市', this)">前橋市（3）</button>  ← 3 を変更
```

---

## [10] 販売店舗セクションの見出し

```html
<div class="sec-eye">Store & Drink Info</div>
<h2 class="sec-ttl">店舗別<em>販売情報</em></h2>
<p class="sec-note">カードをタップするとGoogleマップが開きます。</p>
```

---

## [11] マップの表示設定

```js
// CONFIG 内
mapCenter: { lat: 36.32, lng: 139.20 }, // 初期中心座標
mapZoom:   11,   // ズームレベル（10〜13 が目安。大きいほど拡大）
```

**マップの高さ（CSS内を検索）:**
```css
#storeMap { height: 440px; ... }  /* デスクトップ */
/* @media (max-width:700px) 内 */
#storeMap { height: 280px; }      /* スマホ */
```

---

## [12] ルート提案セクション

```html
<div class="sec-eye">Drink Tour Route</div>
<h2 ...>ドリンク<em style="color:var(--gold)">巡回ルート</em></h2>
<p class="sec-note">出発する店舗を選ぶと、ドリンクA〜Eを効率よく巡る5ストップルートを提案します。</p>
<span class="route-start-label">🚀 出発店舗：</span>
<button ...>ルートを生成</button>
<button class="btn-route-map" ...>🗺️ Google マップで全ルートを開く</button>
```

---

## [13] イントロアニメーション時間

```js
introDuration: 3200, // イントロ表示時間（ms）。速くしたい場合は 2000 など
introFadeOut:  800,  // フェードアウト時間（ms）
```

---

## [14] 全制覇エフェクト（紙吹雪）

```js
confettiCount:     150,   // 紙吹雪の数（スマホで重い場合は 80〜100 に）
confettiSizeMin:   8,     // 最小サイズ（px）
confettiSizeMax:   30,    // 最大サイズ（px）
confettiDurMin:    1.8,   // 落下アニメ最短時間（秒）
confettiDurMax:    4.6,   // 落下アニメ最長時間（秒）
confettiDelayMax:  1.8,   // 出現ディレイの最大（秒）
confettiColors: ['#CBA258','#E8C97A','#FFE566','#ffffff','#D4E9E2','#00704A','#4ade80','#fbbf24'],
confettiShapes: ['★','✦','✧','◆','●','✿'],  // 絵文字も使える
```

---

## [15] ヒーロー背景パーティクル

```js
particleCount:    80,     // 粒の数（増やすと密になるが重くなる）
particleSizeMin:  0.4,    // 最小半径（px）
particleSizeMax:  2.2,    // 最大半径（px）
particleSpeedMax: 0.0004, // 移動速度（大きいほど速い）
particleAlphaMin: 0.15,   // 最小透明度（0〜1）
particleAlphaMax: 0.75,   // 最大透明度（0〜1）
particleColors: [
  'rgba(0,200,100,',    // ← 末尾のカンマまで含めること
  'rgba(203,162,88,',
  ...
],
```

---

## [16] ヒーロー背景オーブ（光の玉）— CSS

`<style>` 内の `.orb1` 〜 `.orb5` を編集します。

```css
.orb1 {
  width: 600px; height: 600px;   /* サイズ */
  background: radial-gradient(circle at 40% 40%, rgba(0,180,100,.55), ...);
  /*                                              ↑ 色          ↑ 濃さ（0〜1） */
  top: -180px; left: -180px;     /* 位置 */
  animation: orbFloat1 5s ease-in-out infinite; /* 秒数で速さ調整 */
}
```

消したい場合: HTML内の `<div class="orb orb1">` 〜 `orb5` の行を削除。

---

## [17] ヒーロービーム・オーロラ — CSS

```css
.hero-beam  { animation: beamSpin 8s linear infinite; }         /* 速さ調整 */
.hero-beam2 { animation: beamSpin 12s linear infinite reverse; }
.hero-aurora { animation: auroraPulse 4s ease-in-out infinite; }
```

消したい場合: HTML内の `<div class="hero-beam">` `<div class="hero-beam2">` `<div class="hero-aurora">` `<div class="hero-aurora2">` を削除。

---

## [18] 色テーマ — CSS 変数

`<style>` の最上部 `:root` ブロックを編集します。

```css
:root {
  --gd:   #1E3932;  /* ダークグリーン（ヒーロー・ナビ・フッター背景） */
  --gm:   #00704A;  /* ミドルグリーン（ボタン・アクセント） */
  --gl:   #D4E9E2;  /* ライトグリーン（バッジ背景など） */
  --gold: #CBA258;  /* ゴールド（強調テキスト・ボーダー） */
  --gold2:#E8C97A;  /* ライトゴールド（グラデーション用） */
  --cream:#F2F0EB;  /* クリーム（明るいセクション背景） */
  --ww:   #FDFAF5;  /* オフホワイト（ドリンクセクション背景） */
  --td:   #1A1A1A;  /* テキスト ダーク */
  --tm:   #444;     /* テキスト ミドル */
  --ts:   #888;     /* テキスト サブ（グレー） */
}
```

---

## [19] フォント

`<head>` 内の Google Fonts を変更します。

```html
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+JP:wght@400;700;900&family=Noto+Sans+JP:wght@400;500;700&display=swap" rel="stylesheet">
```

使用箇所（`<style>` 内）:
```css
body    { font-family: 'Noto Sans JP', sans-serif; }  /* 本文 */
.hero h1 { font-family: 'Noto Serif JP', serif; }     /* 見出し */
```

---

## [20] ナビゲーションリンク

```html
<!-- デスクトップナビ -->
<ul class="nav-links">
  <li><a href="#info">開催情報</a></li>      ← テキスト変更可
  <li><a href="#howto">参加方法</a></li>
  <li><a href="#drinks">ドリンク</a></li>
  <li><a href="#status">販売店舗</a></li>
  <li><a href="#routeSection">ルート提案</a></li>
</ul>

<!-- スマホ用ドロワー（同様に変更） -->
<div class="nav-drawer">
  <a href="#info" onclick="closeNav()">📅 開催情報</a>
  ...
</div>
```

---

## [21] シェアカードのテキスト

```html
<!-- HTML の share-modal 内 -->
<div class="share-title">群馬DC 限定ドリンク<br><span class="g">全5種類制覇！</span></div>
<div class="share-sub">STARBUCKS COFFEE — EAST GUNMA 2026</div>
```

**SNS投稿文（JS内を検索）:**
```js
var text = '【スターバックス 群馬DC】限定ドリンク全5種類制覇しました！🏆☕\n' + ...
```

---

## ❓ よくある問題

| 症状 | 原因 | 対処 |
|------|------|------|
| マップにピンが出ない | Leafletのサイズ未計算 | ページをスクロールしてマップを表示エリアに入れる |
| ルートが選択できない | 未選択状態 | リストから店舗を選んでから「ルートを生成」 |
| 画像が表示されない | URLが無効 | 別の画像URLを試すか `photo: ''` に戻す |
| スマホでナビが消える | ハンバーガー表示 | ≡ ボタンをタップ |
| 編集後に表示が壊れた | 構文ミス | GitHubのHistoryから前バージョンに戻す |

---

## 🔄 新しいキャンペーンへの使い回し手順

1. `CONFIG.campaignName` / `campaignSub` を新しいキャンペーン名に変更
2. `DRINKS` を新しいドリンク情報に書き換え
3. `STORES` を新しい店舗情報に書き換え
4. `CONFIG.totalDrinks` を DRINKS の件数に合わせて変更
5. INFO セクションの開催期間テキストを更新
6. ヒーローの数字（`heroNum1〜3`）を更新
7. JS内の `var KEY = 'gunma_dc_v4'` の末尾番号を上げる（例: `v5`）
   → 前回のコレクションデータがリセットされます

---

*Built with ❤️ — index.html single file, no server required*
