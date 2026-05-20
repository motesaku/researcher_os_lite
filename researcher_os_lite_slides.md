---
marp: true
theme: default
size: 16:9
paginate: true
header: 'researcher_os_lite — AI agent駆動研究環境の最小単位'
footer: 'Qoosaku Moteki (JAMSTEC) · CC BY 4.0 / repo: Apache 2.0'
style: |
  section {
    font-family: -apple-system, "Hiragino Kaku Gothic ProN", "Yu Gothic UI", "Meiryo", sans-serif;
    background: #FAFBFC;
    color: #0B1F33;
    padding: 60px 70px;
  }
  section.lead {
    background: #21295C;
    color: #FFFFFF;
    text-align: left;
    padding: 80px 80px;
  }
  section.lead h1 {
    color: #FFFFFF;
    font-size: 56px;
    letter-spacing: -1px;
    margin: 0 0 16px 0;
    line-height: 1.15;
  }
  section.lead h2 {
    color: #67E8F9;
    font-size: 24px;
    font-weight: 400;
    font-style: italic;
    margin: 0 0 40px 0;
    border: none;
  }
  section.lead .meta {
    color: #94A3B8;
    font-size: 15px;
    margin-top: 60px;
  }
  section.dark {
    background: #21295C;
    color: #FFFFFF;
  }
  section.dark h1, section.dark h2, section.dark h3 {
    color: #FFFFFF;
  }
  section.dark a, section.dark code {
    color: #67E8F9;
  }
  h1 {
    color: #065A82;
    font-size: 38px;
    letter-spacing: -0.5px;
    margin-bottom: 8px;
    border-bottom: 2px solid #1C7293;
    padding-bottom: 10px;
  }
  h2 {
    color: #1C7293;
    font-size: 24px;
    font-weight: 400;
    font-style: italic;
    border: none;
    margin-top: 0;
  }
  h3 {
    color: #065A82;
    font-size: 22px;
    margin-top: 28px;
  }
  ul, ol {
    line-height: 1.75;
    font-size: 20px;
  }
  li {
    margin-bottom: 6px;
  }
  table {
    font-size: 18px;
    width: 100%;
    border-collapse: collapse;
    margin: 16px 0;
  }
  th {
    background: #065A82;
    color: #FFFFFF;
    padding: 10px 14px;
    text-align: left;
    font-weight: 600;
  }
  td {
    background: #FFFFFF;
    padding: 10px 14px;
    border-bottom: 1px solid #E2E8F0;
  }
  tr:nth-child(even) td {
    background: #F1F5F9;
  }
  code {
    background: #EFF6FB;
    color: #065A82;
    padding: 2px 8px;
    border-radius: 4px;
    font-family: "SF Mono", "Consolas", "Menlo", monospace;
    font-size: 0.92em;
  }
  pre {
    background: #0F2D4A;
    color: #E2E8F0;
    border-radius: 8px;
    padding: 20px 24px;
    font-size: 17px;
    line-height: 1.55;
    overflow-x: auto;
  }
  pre code {
    background: transparent;
    color: inherit;
    padding: 0;
  }
  blockquote {
    border-left: 4px solid #1C7293;
    background: #EFF6FB;
    color: #0B1F33;
    padding: 16px 24px;
    margin: 20px 0;
    font-style: italic;
    border-radius: 0 8px 8px 0;
  }
  strong {
    color: #065A82;
  }
  section.dark strong {
    color: #67E8F9;
  }
  .grid-2 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 28px;
  }
  .card {
    background: #FFFFFF;
    border: 1px solid #CBD5E1;
    border-left: 4px solid #1C7293;
    border-radius: 6px;
    padding: 18px 22px;
  }
  .card h3 {
    margin-top: 0;
    font-size: 18px;
    color: #065A82;
  }
  .card p, .card ul {
    font-size: 17px;
    margin: 6px 0;
  }
  .callout {
    background: #21295C;
    color: #FFFFFF;
    padding: 20px 28px;
    border-radius: 8px;
    font-size: 19px;
    margin: 24px 0;
  }
  .callout strong {
    color: #67E8F9;
  }
  .small {
    font-size: 15px;
    color: #64748B;
  }
  footer, header {
    color: #94A3B8;
    font-size: 12px;
  }
---

<!-- _class: lead -->
<!-- _paginate: false -->

# researcher_os_lite

## AI agent を「単発の作図補助」から
## 「研究文脈を持った共同作業者」に育てる最小テンプレート

<div class="meta">

茂木耕作 (RIGC, JAMSTEC) · 2026

公開リポジトリ：[github.com/motesaku/researcher_os_lite](https://github.com/motesaku/researcher_os_lite)

</div>

---

# このスライドが伝えること

研究者なら誰でも、6ファイルを clone するだけで、AI agent との対話に「研究の作法」を持ち込める。

これは大掛かりなシステムではなく、**思想の最小完全版**である。

<div class="callout">

**今日の到達点：** 聞き終わったあと、あなたの手元にも `researcher_os_lite` が clone され、5分後に hello_research のサンプル図が出る。

</div>

---

# 何が問題か

研究の現場で AI agent を使うとき、誰もが同じ壁に当たる。

- 毎回「私は気象研究者で、〇〇のデータを扱っていて...」と説明し直す
- AI に渡したコードが、自分のスタイル・規約と微妙に合わない
- 解析・作図・執筆が別々のツールに分断され、文脈が散逸する
- 数ヶ月前の自分のコードを再開するとき、思い出す作業に時間が消える

> これらは「AI の賢さ」の問題ではなく、**研究文脈を AI が扱える形に整えていない**ことから来る。

---

# このリポジトリの提案

AI agent に毎回ゼロから説明する代わりに、**少数のテキストファイル**を読ませる運用に切り替える。

| ファイル | 役割 | 比喩 |
|---|---|---|
| `AGENTS.md` / `CLAUDE.md` | AI agentへの基本ルール | オフィスの規則集 |
| `SKILL.md` | 何ができる/できないか | 作業者のスキルシート |
| `GROWING_YOUR_OS.md` | 育て方のガイド | 新人研修のテキスト |
| `examples/hello_research/` | 5分で動く最小サンプル | 試運転コース |

たったこれだけで、AI agent は **「毎回新人」から「文脈を持った同僚」** に変わる。

---

<!-- _class: dark -->

# 中心メッセージ

<br>

文脈ファイルは、

AI agent の **研究室内メモリ** である。

<br>
<br>

賢いが、文脈がなければ毎回「新人」に戻る AI に、

研究者の作法を **テキストとして** 渡しておくこと。

<br>

> Plan を読んで承認するという最軽量の方法で、
> 研究者は **「コードの正誤」ではなく「計画の正誤」** を握り続ける。

---

# リポジトリ構成（公開状態）

```
researcher_os_lite/
├── LICENSE                          Apache License 2.0
├── .gitignore                       研究現場向け除外設定
├── README.md                        入口・5分で読める全体像
├── AGENTS.md                        Codex / Cursor / Antigravity 用
├── CLAUDE.md                        Claude Code 用（AGENTS.md と同内容）
├── SKILL.md                         3つのスキル定義
├── GROWING_YOUR_OS.md               育て方のステップバイステップ
└── examples/hello_research/
    ├── HOW_TO_RUN.md                5分で動かす手順
    └── PROMPT.md                    漠然プロンプト + 比較体験ガイド
```

<div class="callout">

**8ファイル・展開後 約42KB。** 全部を1時間で読み切れる規模に意図的に絞ってある。

</div>

---

# AGENTS.md / CLAUDE.md：4つの動作ルール

<div class="grid-2">
<div class="card">

### Rule 1 : Plan First

いきなり実装しない。依頼の解釈、不明点、計画、リスクを順に提示し、研究者の承認を待つ。

</div>
<div class="card">

### Rule 2 : 破壊的操作は事前確認

ファイル削除、環境構築、外部アクセス、大規模リファクタリングは、必ず承認を取る。

</div>
<div class="card">

### Rule 3 : 検証を組み込む

読込直後の先頭5行表示、変換後の基本統計、出力前のサンプル提示を、常に研究者と一緒に確認する。

</div>
<div class="card">

### Rule 4 : 不確かなら止まる

データ仕様や研究文脈に不確かさがあれば、推測で進めず質問する。誤った推測で動いてしまうコードが最大のリスク。

</div>
</div>

<div class="callout">

これらは「絶対の掟」ではなく、**研究者と AI agent の間の合意書**。

</div>

---

# SKILL.md：「3つ」から始める

| Skill | 何のスキルか |
|---|---|
| `data_inspection` | 新規データの構造点検と仕様書との整合確認 |
| `analysis_planning` | 漠然な依頼から、実装前に詳細計画を立てる |
| `reproducible_implementation` | 承認された計画に従って、コードと出力を生成 |

### 追加の判断基準

- 同じ依頼を **3回以上頼んだ** か？（あれば追加価値あり）
- **できないこと**を書けるか？（書けないならまだ早い）
- 1つのスキルで完結するか？（複数にまたがるなら分解）

> **3回繰り返したパターンが、スキルになる。** 現場で持続する基準。

---

# 「複数AI agent対応」の実装上の判断

`AGENTS.md` と `CLAUDE.md` は、**同じ内容のファイルを2つ置いている**。

| AI agent | 自動認識する主なファイル |
|---|---|
| Claude Code | `CLAUDE.md` |
| Codex (OpenAI Desktop / CLI) | `AGENTS.md` |
| Cursor | `AGENTS.md`（近年版）/ `.cursor/rules/` |
| Antigravity | `AGENTS.md` / `.gemini/` |

シンボリックリンクではなく **単純コピー** にした理由：

- Windows ユーザーが詰まらない
- 初心者が「リンクって何？」で混乱しない
- 乖離リスクは小さい（年に数回しか書き換えないファイル）

---

# GROWING_YOUR_OS.md：育て方の時間軸

| 時期 | やること | 触るファイル |
|---|---|---|
| **Day 0** | hello_research を完了 | サンプルのみ |
| **Day 1** | 過去コード1本を `my_*_study/` に接続 | `notes/data_paths.md` |
| **第1週** | 研究文脈を3〜5行追加 | `AGENTS.md` / `CLAUDE.md` |
| **第2〜4週** | 繰り返しパターンをスキル化 | `SKILL.md`, project `README.md` |
| **第2〜3ヶ月** | 描画・主張・命名の規約を蓄積 | `AGENTS.md` |
| **半年〜** | 必要なら台帳・ログを外部から取り込み | 各自の過去解析ディレクトリ |

<div class="callout">

**完璧を目指さない。困ったときに少し足す。** これが唯一持続する育て方。

</div>

---

# 5分で試す

<br>

```bash
# clone
git clone https://github.com/motesaku/researcher_os_lite.git
cd researcher_os_lite/examples/hello_research

# あとは HOW_TO_RUN.md の手順に従う
# お手元の AI agent（どれでもOK）で、5分以内に最初の出力が出る
```

<br>

### 体験できること

1. 漠然なプロンプトを投げる
2. AI agent が **Plan（実装計画）** を返してくる
3. 計画を3分でレビューし、修正点があれば対話で詰める
4. 承認すると、コードと結果が出る → `figures/hello.png`

---

<!-- _class: dark -->

# あなたへの招待

<br>

このリポジトリを **clone してみてください**。

<br>

そして、第1週に3行だけ、

**「このプロジェクト固有の情報」** を書き換えてみてください。
それだけで、AI agent はあなたの研究文脈を持った同僚に変わり始めます。
> 実践者が増えれば、進捗管理もアイデア共有も飛躍的に効率化する。
> このliteは、その文化を育てるための種です。
**[github.com/motesaku/researcher_os_lite](https://github.com/motesaku/researcher_os_lite)**
Apache License 2.0 · 自由に複製・改変・再配布できます
