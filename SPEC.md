# ブロックバランス - 仕様書

## バージョン情報

### v1.9（2026-06-02）- /improve_auto P1・P2実装
**改善内容**:
- **P1-1**: PWA theme-color設定修正
  - 非標準の `media` 属性を削除
  - `<meta name="theme-color" content="#2563EB">` に統一
  - ブラウザアドレスバー色の安定化

- **P1-2**: manifest.json icon サイズ修正
  - 実装されていない 512x512 アイコンを削除
  - 192x192 アイコンに統一
  - `purpose` を "any maskable" に統一

- **P2-1**: Service Worker キャッシュバージョン更新
  - CACHE_NAME: v1.8 → v1.9
  - デプロイ時のキャッシュ自動更新を実現

- **P2-2**: Tailwind CSS 遅延読み込み実装
  - `media="print" onload="this.media='all'"` パターンで非ブロッキング読み込み
  - LCP（Largest Contentful Paint）改善
  - フォールバック用 `<noscript>` タグ追加

### v1.8以前
- ゲーム基本機能実装
- Schema.org マークアップ実装
- 多言語対応（日本語・英語）

## 次の改善候補（P3・P4）

### P3: Accessibility 改善
- テキストコントラスト比向上
- キーボードフォーカスインジケーター追加
- ARIA ラベル不足分追加

### P3: manifest.json scope 修正
- 相対パスに統一、環境依存性排除

### P4: Core Web Vitals 最適化
- PageSpeed Insights 90+ 目標
- CSS インライン化検討
- JavaScript 分割・遅延読み込み

### P4: サイトマップ作成
- `sitemap.xml` 実装
- SEO強化

## ゲーム仕様

### 機能
- ブロックドラッグ＆ドロップ配置
- リアルタイム物理演算
- スコアシステム
- ゲーム履歴保存
- 難易度選択（かんたん/ふつう/むずかしい）
- ゲームモード（通常/タイムアタック）
- キーボードショートカット対応
- コンボシステム
- 効果音トグル
- PWA対応（オフラインプレイ可能）

### ブロック種類（6種類）
1. 正方形 (48×48px, 赤)
2. 横長 (64×32px, 青)
3. 縦長 (32×64px, 緑)
4. 平べったい (48×24px, 黄色)
5. 小 (40×40px, 紫)
6. 大 (56×56px, ピンク)

### スコア計算
```
スコア = (高さ × 10 × 難易度倍率) + バランスボーナス + コンボボーナス
難易度倍率: かんたん=1.0, ふつう=1.5, むずかしい=2.0
```

## ページ構成
- ゲーム画面
- 使い方
- 利用規約
- プライバシーポリシー
- お問い合わせ

## 技術スタック
- HTML5 + CSS（Tailwind）
- Vanilla JavaScript（フレームワーク不使用）
- Service Worker（PWA対応）
- Web Audio API（効果音）
- LocalStorage（スコア保存）
