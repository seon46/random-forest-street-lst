# Random Forestを用いた街路スケールの地表面温度推定手法の提案

衛星リモートセンシングと3D日影モデリングを組み合わせ、Random Forestによるダウンスケーリングで**1m解像度の街路レベル地表面温度(LST)推定**を実現した卒業研究です。

> Estimation of street-scale Land Surface Temperature using Random Forest with satellite remote sensing and 3D shade modeling.

---

## 📋 概要

- **著者**: 遠藤 瀬音 (Endo Sene)
- **所属**: 埼玉大学 工学部 情報工学科 堤田研究室
- **指導教員**: 堤田 成政 准教授
- **提出**: 令和8年2月10日
- **学籍番号**: 22TI040

---

## 🔬 研究内容

### 背景
急速な都市化は都市ヒートアイランド(UHI)現象を悪化させ、都市居住者の熱ストレスや熱中症などの健康リスクを増大させています。衛星リモートセンシングによる地表面温度(LST)モニタリングは広域評価には有効ですが、空間解像度と再帰周期の間にトレードオフがあり、街路空間の微細な熱的不均質性をとらえることができていません。

### 目的
歩行者の熱曝露評価に必要な **1m解像度の街路レベルLST** を、衛星データ・3D日影モデリング・現地サーマルカメラ観測から推定する手法を開発すること。

### 手法のポイント
- **Random Forest** を用いて、低解像度の衛星LSTデータを街路レベルにダウンスケーリング
- 建物と植生の両方の日影を考慮した新たな説明変数 **Shade NDVI** を導入
- FLIRサーマルカメラによる現地観測データで検証

### 結果
- 構築モデルは実測熱画像に対して **決定係数 R² = 0.72** を達成
- 日影分布を考慮しないモデルを大幅に上回る精度
- 日向と日影の路面間の急激な温度勾配の再現には、日影の冷却効果を考慮することが重要であることを示した

### 研究対象地域
埼玉県さいたま市の埼大通り(埼玉大学西端〜北浦和駅西口付近)

---

## 📁 リポジトリ構成

```
.
├── README.md
├── LICENSE
├── .gitignore
├── thesis/                       # 卒業論文本体
│   ├── 2026B22TI040.pdf          # 提出版PDF
│   └── 2026B22TI040.tex          # LaTeXソース
├── code/                         # 解析コード
│   ├── dataset.ipynb             # データセット作成
│   ├── model.ipynb               # Random Forestモデル構築・評価
│   └── requirements.txt          # Python依存パッケージ
└── research_plan/                # 研究計画書
    ├── ResearchPlan.md
    └── ref.bib
```

---

## ⚙️ ワークフロー

1. FLIRサーマルカメラで撮影した熱画像を ImageJ の IRImage で処理してLSTデータを取得
2. ShadeMap を用いて3D日影分布を取得
3. `code/dataset.ipynb` でLandsat/Sentinel-2衛星データと日影データを統合してデータセットを作成
4. `code/model.ipynb` でRandom Forestモデルを構築し、街路レベルLST分布を推定

---

## 🚀 動作環境

### 必要なもの
- Python 3.10+
- Jupyter Notebook
- 主要パッケージ: `scikit-learn`, `numpy`, `pandas`, `rasterio`, `geopandas`, `matplotlib`

### セットアップ

```bash
pip install -r code/requirements.txt
```

### 外部ツール
- **ImageJ + IRImage プラグイン**: サーマル画像処理用
- **ShadeMap**: 3D日影分布の取得

### 使用データ
リポジトリのデータ容量制約のため、生データ(衛星画像・サーマル画像など)はリポジトリに含めていません。詳細は卒業論文本文をご覧ください。

---

## 📄 論文

論文本体: [`thesis/2026B22TI040.pdf`](thesis/2026B22TI040.pdf)

---

## 📝 ライセンス

本リポジトリのコードは [MIT License](LICENSE) の下で公開しています。
論文本文・図表については、引用の際は出典を明記してください。
