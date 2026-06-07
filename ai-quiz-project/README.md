# AIクイズ問題集プロジェクト
## シラバス駆動型・資格学習Webアプリ

---

## プロジェクト概要

資格試験のシラバスを起点に、問題集を自分で作成・公開するシステム。  
GitHub Pagesで無料ホスティング。問題データはJSONファイルで管理。

**差別化ポイント**
- 市販問題集に頼らない（シラバス改訂に即対応）
- 自分の弱点に合わせてカスタマイズ可能
- 製造業×AI の実績として副業・コンサル活動に活用できる

---

## 対象資格ロードマップ

| フェーズ | 資格 | ステータス |
|---|---|---|
| Phase 1 | 生成AIパスポート | 🔨 構築中 |
| Phase 2 | G検定 | 📋 計画中 |
| Phase 3 | ITパスポート | 📋 計画中 |
| Phase 4 | 情報セキュリティ系 | 📋 計画中 |

---

## 技術スタック

```
フロントエンド : HTML / CSS / JavaScript（フレームワーク不使用）
データ管理    : JSON（章ごとにファイル分割）
ホスティング  : GitHub Pages（無料）
問題生成      : Claude / ChatGPT（章単位で投入）
バージョン管理: Git / GitHub
```

---

## ディレクトリ構成

```
ai-quiz-project/
├── README.md                 ← このファイル（企画書・外部記憶）
├── PROMPT_GUIDE.md           ← 問題生成プロンプト集
│
├── ai-passport/              ← 生成AIパスポート
│   ├── index.html            ← アプリ本体（全ロジック含む）
│   └── data/
│       ├── chapter1.json     ← 第1章：AI
│       ├── chapter2.json     ← 第2章：生成AI
│       ├── chapter3.json     ← 第3章：現在の生成AI
│       ├── chapter4.json     ← 第4章：情報リテラシー・AI社会原則
│       └── chapter5.json     ← 第5章：プロンプト
│
├── g-kentei/                 ← 将来：G検定（同じ構成をコピー）
└── it-passport/              ← 将来：ITパスポート（同じ構成をコピー）
```

---

## 問題追加の手順（章単位ワークフロー）

```
① 対象章のシラバス or テキスト抜粋を用意する
      ↓
② PROMPT_GUIDE.md のプロンプトにテキストを貼り付けてAIに投入
      ↓
③ JSON形式で問題が生成される（20〜30問）
      ↓
④ data/chapterN.json に保存
      ↓
⑤ GitHubにpush → 自動で公開
```

**1章あたりの目安作業時間：30〜60分**

---

## 問題JSONフォーマット

```json
{
  "chapter": 1,
  "chapter_name": "AI",
  "questions": [
    {
      "id": "AI001",
      "chapter": 1,
      "type": "multiple_choice",
      "q": "問題文",
      "choices": ["選択肢A", "選択肢B", "選択肢C", "選択肢D"],
      "answer": [0],
      "exp": "解説文"
    },
    {
      "id": "AI002",
      "chapter": 1,
      "type": "true_false",
      "q": "問題文",
      "choices": ["○ 正しい", "× 誤り"],
      "answer": [0],
      "exp": "解説文"
    },
    {
      "id": "AI003",
      "chapter": 1,
      "type": "multi_select",
      "q": "問題文（複数選択）",
      "choices": ["選択肢A", "選択肢B", "選択肢C", "選択肢D"],
      "answer": [0, 2],
      "exp": "解説文"
    }
  ]
}
```

**typeの種類**
- `multiple_choice` : 4択（answer は `[0]` のように1つ）
- `true_false`      : ○× （answer は `[0]`=正しい、`[1]`=誤り）
- `multi_select`    : 複数選択（answer は `[0, 2]` のように複数）

---

## GitHub Pages 公開手順

```
1. GitHubアカウント作成（無料）
2. 新規リポジトリ作成（例：ai-quiz）
3. このフォルダをpush
4. Settings > Pages > Source: main branch / root
5. https://ユーザー名.github.io/ai-quiz/ で公開完了
```

---

## 将来拡張アイデア

- [ ] 弱点問題の優先出題（正答率の低い問題を多く出す）
- [ ] 問題ごとの解説リンク（Obsidian連携）
- [ ] 企業研修向けカスタマイズ版（副業・コンサル展開）
- [ ] 多言語対応（英語版で海外展開）
