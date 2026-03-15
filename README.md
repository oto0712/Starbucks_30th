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

1. `index.html` を開く → 右上の **✏️ 鉛筆アイコン（Edit this file）** をクリック
2. 編集する
3. 右上の **Commit changes** で保存

> 壊してしまった場合: **History（📜アイコン）** から以前のバージョンに戻せます。

---

## 🗺️ 編集箇所のマップ

```
index.html
├── <head>          … ブラウザタブタイトル・フォント
├── <style>
│   └── :root       … ★★★ 全カラー・フォントサイズ・角丸・アニメーション速度 ★★★
├── HTML各セクション … 文章・見出し・ステップの絵文字など
└── <script>
    ├── CONFIG {}   … サイト基本情報・エフェクト設定
    ├── DRINKS []   … ドリンク情報
    └── STORES []   … 店舗情報
```

---

## ━━━━━━━━━━━━━━━━━━━━━━━━━
## PART 1: カラー / フォントサイズ / 角丸 / アニメーション
## ━━━━━━━━━━━━━━━━━━━━━━━━━

`<style>` の最上部にある `:root { }` ブロックを編集します。  
**ここを変えるだけでサイト全体の色・サイズ・動きが変わります。**

---

### [A] ブランドカラー（メインテーマ）

```css
--gd:    #1E3932;  /* ダークグリーン：ヒーロー・ナビ・フッター背景 */
--gm:    #00704A;  /* ミドルグリーン：ボタン・アクセント */
--gm2:   #009458;  /* グリーン（明）：ボタングラデーション終端 */
--gl:    #D4E9E2;  /* ライトグリーン：バッジ背景 */
--gold:  #CBA258;  /* ゴールド：強調テキスト・ボーダー */
--gold2: #E8C97A;  /* ライトゴールド：グラデーション用 */
--gold3: #FFE566;  /* ブライトゴールド：紙吹雪など */
```

**テーマカラーを一括変更する場合の例（青系）:**

```css
--gd:   #1a2a4a;  /* ネイビー */
--gm:   #1565A0;  /* ブルー */
--gm2:  #1976D2;
--gl:   #BBDEFB;
--gold: #FFB300;  /* アンバー（アクセント） */
```

---

### [B] 背景色

```css
--cream:    #F2F0EB;  /* 明るいセクション背景（INFO・DRINKS等） */
--ww:       #FDFAF5;  /* ドリンクセクション背景 */
--dark-bg:  #0D2419;  /* シェアモーダルの最暗グラデ */
--mid-bg:   #1A3A2F;  /* ドロップダウン・ポップアップ背景 */
--map-bg:   #e8ede0;  /* マップ読み込み前のプレースホルダー */
```

---

### [C] テキスト色

```css
--td:  #1A1A1A;  /* 本文テキスト（最も濃い） */
--tm:  #444444;  /* 中間テキスト */
--ts:  #888888;  /* サブテキスト・補足（グレー） */
```

---

### [D] ドリンクカードのアクセントカラー

各ドリンク（A〜E）のカード背景・ラベル・バッジ色を個別に設定できます。

```css
--d0:  #00704A; --d0b: #DCF2E8;  /* ドリンクA：前色・背景色 */
--d1:  #1565A0; --d1b: #DCEbf7;  /* ドリンクB */
--d2:  #B02050; --d2b: #F7DCE8;  /* ドリンクC */
--d3:  #6030A0; --d3b: #EEDCf7;  /* ドリンクD */
--d4:  #A06000; --d4b: #F7EDDC;  /* ドリンクE */
```

> `--d0` が文字色、`--d0b` がバッジ・背景色です。  
> 明るい背景色（`--d0b`）に対して濃い文字色（`--d0`）を合わせると読みやすくなります。

---

### [E] 開催中バッジ（点滅ドット）

```css
--dot-color: #00704A;  /* 点滅ドットの色 */
--dot-bg:    #D4E9E2;  /* バッジ全体の背景色 */
--dot-text:  #1E3932;  /* 「開催中」テキストの色 */
```

**カラー例：**

| 雰囲気 | dot-color | dot-bg | dot-text |
|--------|-----------|--------|----------|
| グリーン（現在） | `#00704A` | `#D4E9E2` | `#1E3932` |
| 赤・緊急感 | `#E53E3E` | `#FED7D7` | `#742A2A` |
| オレンジ・秋 | `#DD6B20` | `#FEEBC8` | `#7B341E` |
| ピンク・春 | `#D53F8C` | `#FED7EE` | `#702459` |
| ゴールド | `#CBA258` | `#FEF3C7` | `#1E3932` |
| ブルー | `#2B6CB0` | `#BEE3F8` | `#1A365D` |

---

### [F] 店舗マーカー色（マップ・店舗リスト）

```css
--mb: #8B5E3C;  /* 前橋市のピン・バッジ色（茶） */
--ib: #1A6B91;  /* 伊勢崎市（青） */
--ob: #2E7D5A;  /* 太田市（緑） */
```

---

### [G] UIコンポーネント色

```css
--rank2-color:  #5A8F7B;  /* 最寄り店舗 2位バッジ */
--rank3-color:  #7BA89A;  /* 最寄り店舗 3位バッジ */
--success:      #4ade80;  /* 成功色（✓チェック・コピー完了） */
--btn-line:     #06C755;  /* LINEシェアボタン */
--btn-twitter:  #000000;  /* X(Twitter)シェアボタン */
--warn-bg:      #fff3cd;  /* 警告ボックス背景（位置情報エラー等） */
--warn-border:  #ffc107;  /* 警告ボックスボーダー */
--warn-text:    #856404;  /* 警告テキスト */
```

---

### [H] フォントサイズ

```css
--fs-xs:   10px;   /* 極小：バッジ・上部ラベル・注釈 */
--fs-sm:   11px;   /* 小：住所・補足説明・ドリンク説明 */
--fs-base: 13px;   /* 基本：本文・ボタン文字・リスト項目 */
--fs-md:   14px;   /* 中：ヒーローリード文・カード説明 */
--fs-lg:   16px;   /* 大：カード見出し・重要ラベル */
--fs-xl:   22px;   /* 特大：開催日付の数字 */
--fs-hero: 5rem;   /* ヒーローアイコン（☕）のサイズ */
--fs-num:  2.8rem; /* ヒーロー数字カード（5・13・3）のサイズ */
```

> `rem` は基本フォントサイズ（16px）の倍率です。  
> `5rem` = 80px。大きくしたい場合は `6rem`、小さくしたい場合は `4rem` に変更。

---

### [I] 角丸（border-radius）

```css
--r-sm:   8px;    /* 小：タグ・小バッジ */
--r-md:   14px;   /* 中：ポップアップ・ドロップダウン */
--r-lg:   20px;   /* 大：ドリンクカード・店舗カード */
--r-pill: 100px;  /* 完全丸型：ボタン・タブ・バッジ */
```

> 四角っぽくしたい場合は全部 `4px` などに変更。  
> 完全な丸は `50%`（正方形要素の場合）。

---

### [J] ボックスシャドウ（影）

```css
--shadow-sm:    0 2px 12px rgba(0,0,0,.06);   /* ほぼなし */
--shadow-md:    0 4px 16px rgba(0,0,0,.08);   /* 標準 */
--shadow-lg:    0 8px 32px rgba(0,0,0,.12);   /* 強め */
--shadow-xl:    0 24px 60px rgba(0,0,0,.5);   /* モーダル */
--shadow-green: 0 6px 20px rgba(0,112,74,.4); /* グリーンボタン */
--shadow-gold:  0 6px 20px rgba(203,162,88,.4); /* ゴールドボタン */
```

> 影を消したい場合は `none` に変更。  
> `rgba(0,0,0,.5)` の最後の数字（0〜1）が透明度です。

---

### [K] アニメーション速度（秒単位）

**大きくすると遅く、小さくすると速くなります。`0s` にすると完全停止。**

#### イントロアニメーション
```css
--anim-intro-cup:  2.2s;  /* カップに液体が入る速さ */
--anim-steam:      2.5s;  /* 湯気が揺れる速さ */
--anim-ripple:     2.0s;  /* 液面のリップル（波紋） */
--anim-intro-out:  0.8s;  /* イントロがスライドアウトする速さ */
```

#### ヒーロー画面（テキスト出現）
```css
--anim-hero-appear: 0.9s;  /* 各テキストがフェードインする速さ */
--anim-hero-float:  4.0s;  /* ☕アイコンが上下に浮く速さ（大きいほどゆったり） */
--anim-glow-text:   3.0s;  /* ゴールドテキストが輝く速さ */
--anim-scroll-pulse: 1.6s; /* スクロールキューの点滅 */
```

#### ヒーロー背景（オーブ = 光の玉）
```css
--anim-orb1: 5.0s;  /* 左上の大きなオーブ */
--anim-orb2: 4.2s;  /* 右下のゴールドオーブ */
--anim-orb3: 3.8s;  /* 中央のオーブ */
--anim-orb4: 3.0s;  /* 右上の小さなオーブ */
--anim-orb5: 4.5s;  /* 左下のオーブ */
```
> **速くすると激しく動き、遅くするとゆったりした印象になります。**  
> 全部 `0s` にすると完全に止まり、背景がシンプルになります。

#### ヒーロー背景（ビーム・オーロラ）
```css
--anim-beam1:       8.0s;  /* ビーム1（緑）の回転速さ */
--anim-beam2:      12.0s;  /* ビーム2（ゴールド）の回転速さ（逆方向） */
--anim-aurora:      4.0s;  /* オーロラが呼吸する速さ */
--anim-shimmer:     3.0s;  /* 光の筋が横切る速さ */
--anim-grid-drift: 20.0s;  /* グリッドパターンが流れる速さ */
```

#### サイト全体
```css
--anim-dot-pulse:  1.4s;  /* 開催中バッジのドット点滅 */
--anim-bar-shine:  2.0s;  /* 進捗バーの光沢アニメーション */
--anim-step-ico:   0.6s;  /* How toステップのアイコン出現 */
```

**アニメーションを完全に止めたい場合（軽量化）:**
```css
/* :root に追加する */
--anim-orb1: 0s;
--anim-orb2: 0s;
--anim-orb3: 0s;
--anim-orb4: 0s;
--anim-orb5: 0s;
--anim-beam1: 0s;
--anim-beam2: 0s;
--anim-aurora: 0s;
```

---

## ━━━━━━━━━━━━━━━━━━━━━━━━━
## PART 2: テキスト・文章の編集
## ━━━━━━━━━━━━━━━━━━━━━━━━━

---

### [1] ブラウザタブのタイトル

**場所:** `<head>` 内（ファイルの最上部）

```html
<title>群馬DC 限定ドリンク | Starbucks Coffee</title>
```

---

### [2] イントロ画面・フッター

**場所:** `<script>` 内の `CONFIG` ブロック

```js
siteTitle:    'Starbucks Coffee',             // イントロ大タイトル
campaignName: '群馬DC 限定ドリンク',          // イントロ・フッターのキャンペーン名
campaignSub:  'EAST GUNMA — COLLECTION 2026', // イントロのサブタイトル（英字）
footerNote1:  '※掲載情報は予告なく変更...',  // フッター注意書き1行目
footerNote2:  '※限定ドリンクは...',          // フッター注意書き2行目
```

---

### [3] ナビバー

```js
navBrand: '☕ 群馬東地区 限定ドリンク',  // ナビ左上のテキスト
```

**ナビリンクのテキスト（HTMLを直接編集）:**

```html
<ul class="nav-links">
  <li><a href="#info">開催情報</a></li>       ← テキスト変更可
  <li><a href="#howto">参加方法</a></li>
  <li><a href="#drinks">ドリンク</a></li>
  <li><a href="#status">販売店舗</a></li>
  <li><a href="#routeSection">ルート提案</a></li>
</ul>
<!-- スマホ用も同様に変更 <div class="nav-drawer"> 内 -->
```

---

### [4] ヒーロー（トップ画面）

```js
heroEyebrow: 'STARBUCKS COFFEE — 群馬 DC',     // バッジ文字
heroTitle1:  '群馬DC',                           // H1 1行目
heroTitle2:  '限定ドリンク',                     // H1 2行目（ゴールド色）
heroTitle3:  'コレクション',                     // H1 3行目
heroLead:    '各店舗でしか飲めない、<br>...',    // リード文（<br>で改行）
heroNum1: { n: '5',  l: '限定ドリンク' },        // 数字カード1
heroNum2: { n: '13', l: '対象店舗' },             // 数字カード2
heroNum3: { n: '3',  l: 'エリア' },               // 数字カード3
totalDrinks: 5,  // ドリンク総数（DRINKSの件数と一致させる）
```

---

### [5] 開催情報セクション

**場所:** HTML の `<section id="info">` 内

```html
<!-- 開催期間 -->
<div class="period-dates">
  2025年4月3日<span>（木）</span><br>
  〜 2025年5月6日<span>（火）</span>     ← 変更
</div>

<!-- 開催中バッジ（終了後は「終了」などに変更） -->
<div class="info-period"><span class="dot"></span>開催中</div>

<!-- エリアリスト -->
<ul>
  <li>前橋エリア（前橋市内 3店舗）</li>   ← 変更
  ...
</ul>

<!-- 注意書き -->
<p style="...">※在庫がなくなり次第終了となります</p>  ← 変更
```

---

### [6] 参加方法（How to）セクション

**場所:** HTML の `<section id="howto">` 内

```html
<div class="step rv s1">
  <span class="step-ico">🗺️</span>   ← 絵文字を変更
  <h3>マップを確認</h3>              ← 見出しを変更
  <p>説明文...</p>                   ← 説明文を変更
</div>
<!-- s1〜s4 の4ステップがあります -->
```

---

### [7] ドリンクセクション

```html
<!-- セクション見出し -->
<div class="sec-eye">Drink Collection</div>         ← 英字キャプション
<h2 class="sec-ttl">限定<em>ドリンク</em></h2>      ← <em>内がグリーン
<p class="sec-note">☝️ 飲んだドリンクカードを...</p> ← 注釈

<!-- 全制覇バナー -->
<h3>全5種類制覇おめでとうございます！</h3>          ← 変更
<p>限定ドリンクを全種類制覇しました！<br>...</p>    ← 変更
<button ...>🎉 シェアカードを開く</button>          ← ボタン文字変更
```

---

### [8] ドリンク情報 — `DRINKS` 配列

```js
const DRINKS = [
  {
    id:    0,            // 変更不可（0〜totalDrinks-1）
    name:  'ドリンク名', // カードに表示
    desc:  '説明文',     // カードの説明テキスト
    emoji: '🌿',        // 写真なし時のアイコン
    area:  'エリア名',   // カード上部・ルート提案に表示
    photo: 'https://...jpg', // 画像URL（'' で絵文字表示）
    link:  '',           // 詳細ページURL（'' でボタン非表示）
  },
];
```

---

### [9] 店舗情報 — `STORES` 配列

```js
const STORES = [
  {
    id:     1,
    city:   '前橋市',              // フィルタータブ・マップ色分けに使用
    name:   'けやきウォーク前橋店',
    addr:   '前橋市 文京町2-1-1',
    hours:  '10:00〜21:00',
    lat:    36.379396,             // 緯度（Googleマップ右クリックで取得）
    lng:    139.0783944,           // 経度
    drink:  0,                     // DRINKSのidと一致
    mapUrl: '',                    // 空白で住所から自動生成
  },
];
```

**フィルタータブの数も更新（HTML内を検索）:**
```html
<button ...>すべて（13）</button>  ← 13 を変更
<button ...>前橋市（3）</button>   ← 3 を変更
```

---

### [10] 販売店舗セクション

```html
<div class="sec-eye">Store & Drink Info</div>
<h2 class="sec-ttl">店舗別<em>販売情報</em></h2>
<p class="sec-note">カードをタップするとGoogleマップが開きます。</p>

<!-- 最寄りサブセクション -->
<strong>🧭 現在地から探す</strong>
<p>ボタンを押すと近い店舗を自動で表示します</p>
<button ...>現在地から探す</button>

<!-- マップサブセクション -->
<div class="sec-eye">Store Map</div>
<h2 ...>全店舗<em>マップ</em></h2>
<p class="sec-note">ピンをタップすると店舗情報が表示されます。</p>
```

---

### [11] ルート提案セクション

```html
<div class="sec-eye">Drink Tour Route</div>
<h2 ...>ドリンク<em style="color:var(--gold)">巡回ルート</em></h2>
<p class="sec-note">出発する店舗を選ぶと...</p>
<span class="route-start-label">🚀 出発店舗：</span>
<button ...>ルートを生成</button>
<button class="btn-route-map" ...>🗺️ Google マップで全ルートを開く</button>
```

---

### [12] シェアカード

```html
<!-- HTML share-modal 内 -->
<div class="share-title">群馬DC 限定ドリンク<br><span class="g">全5種類制覇！</span></div>
<div class="share-sub">STARBUCKS COFFEE — EAST GUNMA 2026</div>
```

**SNS投稿文（JS内を検索）:**
```js
var text = '【スターバックス 群馬DC】限定ドリンク全5種類制覇しました！🏆☕\n' ...
```

---

## ━━━━━━━━━━━━━━━━━━━━━━━━━
## PART 3: エフェクト・アニメーション詳細
## ━━━━━━━━━━━━━━━━━━━━━━━━━

---

### [13] イントロアニメーション時間

```js
// CONFIG 内
introDuration: 3200, // イントロ表示時間（ms）。2000 にすると速くなる
introFadeOut:  800,  // フェードアウト時間（ms）
```

---

### [14] 全制覇エフェクト（紙吹雪）

```js
// CONFIG 内
confettiCount:    150,   // 紙吹雪の数（スマホで重い場合は 80〜100 に）
confettiSizeMin:  8,     // 最小サイズ（px）
confettiSizeMax:  30,    // 最大サイズ（px）
confettiDurMin:   1.8,   // 落下アニメ最短時間（秒）
confettiDurMax:   4.6,   // 落下アニメ最長時間（秒）
confettiDelayMax: 1.8,   // 出現ディレイの最大（秒）
confettiColors: ['#CBA258','#E8C97A','#FFE566','#ffffff','#D4E9E2','#00704A','#4ade80','#fbbf24'],
// ↑ 16進カラーコードを追加・削除・変更できます
confettiShapes: ['★','✦','✧','◆','●','✿'],
// ↑ 絵文字も使えます（例: '🎉','❄️','🌸'）
```

---

### [15] ヒーロー背景パーティクル（浮遊する粒）

```js
// CONFIG 内
particleCount:    80,     // 粒の数（増やすと密になるがスマホで重くなる）
particleSizeMin:  0.4,    // 最小半径（px）
particleSizeMax:  2.2,    // 最大半径（px）
particleSpeedMax: 0.0004, // 移動速度（大きいほど速い）
particleAlphaMin: 0.15,   // 最小透明度（0〜1）
particleAlphaMax: 0.75,   // 最大透明度（0〜1）
particleColors: [
  'rgba(0,200,100,',    // ← 末尾のカンマまで含めること！
  'rgba(203,162,88,',   // 各行に rgba(R,G,B, の形式で追加・変更
  'rgba(100,220,150,',
  'rgba(255,220,100,',
  'rgba(180,255,200,',
],
```

**パーティクルを完全に消す場合:**
```js
particleCount: 0,
```

---

### [16] ヒーロー背景オーブ（光の玉）— CSS

`<style>` 内の `.orb1` 〜 `.orb5` を編集します。

```css
.orb1 {
  width: 600px; height: 600px;     /* サイズ（大きいほど範囲が広い） */
  background: radial-gradient(circle at 40% 40%,
    rgba(0,180,100,.55),           /* 中心色と濃さ（0〜1） */
    rgba(0,112,74,.18) 60%,        /* 中間 */
    transparent 80%);              /* 外側は透明 */
  top: -180px; left: -180px;       /* 位置（マイナス値で画面外から） */
  filter: blur(50px);              /* ぼかし量（大きいほどふんわり） */
  /* 速さは :root の --anim-orb1 で変更 */
}
```

**オーブを消したい場合:** HTML内の `<div class="orb orb1">` などを削除。

---

### [17] ヒーロービーム・オーロラ — CSS

```css
/* 速さは :root の --anim-beam1/2, --anim-aurora で変更 */

/* ビームの濃さ（透明度）を変える: */
.hero-beam {
  background: conic-gradient(from 0deg at 50% 50%,
    transparent 0deg,
    rgba(0,180,80,.06) 15deg,   /* ← .06 の部分が濃さ（0〜0.2程度） */
    transparent 30deg);
}

/* ビームを完全に消す: HTML から削除 */
<!-- <div class="hero-beam"></div>  ← この行を削除 -->
<!-- <div class="hero-beam2"></div> ← この行を削除 -->
```

---

## ━━━━━━━━━━━━━━━━━━━━━━━━━
## PART 4: フォント
## ━━━━━━━━━━━━━━━━━━━━━━━━━

---

### [18] フォントの変更

**場所:** `<head>` 内の Google Fonts の読み込み行

```html
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+JP:wght@400;700;900&family=Noto+Sans+JP:wght@400;500;700&display=swap" rel="stylesheet">
```

**別のフォントに変える例（Shippori Mincho + Zen Kaku Gothic）:**

1. [Google Fonts](https://fonts.google.com/?subset=japanese) でフォントを選ぶ
2. 上の行のフォント名を差し替える

**フォントの使い分け（`<style>` 内）:**
```css
body    { font-family: 'Noto Sans JP', sans-serif; }  /* 本文全体 */
.hero h1 { font-family: 'Noto Serif JP', serif; }     /* ヒーロー見出し */
.sec-ttl { font-family: 'Noto Serif JP', serif; }     /* セクション見出し */
```

---

## ━━━━━━━━━━━━━━━━━━━━━━━━━
## PART 5: マップ設定
## ━━━━━━━━━━━━━━━━━━━━━━━━━

```js
// CONFIG 内
mapCenter: { lat: 36.32, lng: 139.20 }, // 初期中心座標
mapZoom:   11,   // ズームレベル（10〜13 が目安。大きいほど拡大）
```

**マップの高さ（`<style>` 内を検索）:**
```css
#storeMap { height: 440px; }  /* デスクトップ */
/* @media (max-width:700px) 内 */
#storeMap { height: 280px; }  /* スマホ */
```

---

## ❓ よくある問題

| 症状 | 原因 | 対処 |
|------|------|------|
| マップにピンが出ない | Leafletのサイズ未計算 | ページをスクロールしてマップを表示エリアに入れる |
| ルートが選択できない | 未選択状態 | リストから店舗を選んでから「ルートを生成」 |
| 画像が表示されない | URLが無効 | 別のURLを試すか `photo: ''` に戻す |
| スマホでナビが消える | ハンバーガー表示 | ≡ ボタンをタップ |
| 編集後に表示が壊れた | 構文ミス | GitHubのHistoryから前バージョンに戻す |
| アニメーションが重い | 端末スペック不足 | `particleCount: 0`、各 `--anim-orb*: 0s` に変更 |

---

## 🔄 新しいキャンペーンへの使い回し手順

1. `CONFIG.campaignName` / `campaignSub` を新しいキャンペーン名に変更
2. `DRINKS` を新しいドリンク情報に書き換え
3. `STORES` を新しい店舗情報に書き換え
4. `CONFIG.totalDrinks` を DRINKS の件数に合わせて変更
5. INFO セクションの開催期間テキストを更新
6. `heroNum1〜3` の数字を更新
7. JS内の `var KEY = 'gunma_dc_v4'` の末尾番号を上げる（例: `v5`）
   → 前回のコレクションデータがリセットされます

---

## 🎨 テーマ変更の例

**ピンク・春テーマ:**
```css
--gd:   #4a1a2e;  --gm:   #d53f8c;  --gm2:  #e966a8;
--gl:   #fed7ee;  --gold: #FFB300;  --gold2: #FFCC44;
--dot-color: #d53f8c;  --dot-bg: #fed7ee;  --dot-text: #702459;
--mb: #9b4dca;  --ib: #d53f8c;  --ob: #e66000;
```

**青・海テーマ:**
```css
--gd:   #0a2540;  --gm:   #1a73e8;  --gm2:  #4285f4;
--gl:   #e8f0fe;  --gold: #fbbc04;  --gold2: #fdd663;
--dot-color: #1a73e8;  --dot-bg: #e8f0fe;  --dot-text: #0a2540;
--mb: #1a73e8;  --ib: #0f9d58;  --ob: #e91e63;
```

---

*Built with ❤️ — index.html single file, no server required*
