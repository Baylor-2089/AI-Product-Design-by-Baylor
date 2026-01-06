---
description: 「もっと良い聞き方があったかも」課題を自動的に改善する
icon: sparkle
---

# Claude用-汎用プロンプト強化SKILL

{% embed url="https://github.com/Baylor-2089/claude-prompt-enhancer-skill" %}

### なぜこのスキルが必要か？

LLMに話しかけるとき、「もっと良い聞き方があったかも」と感じたこと絶対あると思います。

実は、同じ質問でもプロンプトの構造や詳細な工夫次第で回答の質は大きく変わります。

しかし、毎回最適なプロンプトを考えるのは難しいです。

このスキルは、その作業を**自動化**します。

### 仕組み

このスキルは「認知階層フレームワーク」に基づき、すべてのプロンプトを5つのカテゴリに分類します：

| カテゴリ               | 用途    | 例              |
| ------------------ | ----- | -------------- |
| **Generation**     | 新規作成  | メール作成、記事執筆     |
| **Manipulation**   | 変換・加工 | 要約、翻訳、フォーマット変換 |
| **Analysis**       | 分析・抽出 | 感情分析、キーポイント抽出  |
| **Reasoning**      | 論理的思考 | 比較検討、問題解決      |
| **Meta-Cognition** | 行動制御  | ペルソナ設定、品質改善    |

分類後、各カテゴリに最適な強化パターンを**内部で自動適用**。ユーザーは普段通り話しかけるだけで、最適化されたプロンプトで処理されます。

### 主な機能

* **曖昧度判定**: プロンプトが曖昧な場合、的確な質問で意図を確認
* **多言語対応**: 英語・日本語・中国語・韓国語など主要言語をサポート
* **透明な動作**: 強化プロセスはユーザーに見せず、自然な会話を維持

### インストール方法

1. [Releases](https://github.com/Baylor-2089/claude-prompt-enhancer-skill/releases)から`.skill`ファイルをダウンロード
2. Claude.ai → Settings → Profile → Skills でアップロード
3. 自動的に全会話に適用されます

### 他LLMでの使用

`SKILL.md`の内容は、ChatGPTのCustom InstructionsやGeminiのSystem Instructionsにそのまま貼り付けて使用できます。



## 経由

Courseraで「[ChatGPT Prompt Engineering for Developers](https://www.coursera.org/projects/chatgpt-prompt-engineering-for-developers-project)」に参加。

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

主に初心者向けのプロンプトエンジニアリングクラスだが、コアフレームワークとなる４つの要素をみて、「確かに！」となって、

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Claudeに

{% code overflow="wrap" %}
```
First Principleで考えると、LLM向けのPromptをSummarizing、Inferring、Transforming、Expandingよという四つの分類にできると自分的に考えているが、LLMスペシャリストとして、私の考えを補完し、改善してください。
```
{% endcode %}

と相談したところ

```md
素晴らしい着眼点です。「First Principles（第一原理）」に基づいて、物事を構成要素に分解して考えるアプローチは、LLMの理解を深める上で非常に有効です。

あなたの提示された **「Summarizing（要約）」「Inferring（推論）」「Transforming（変換）」「Expanding（拡張）」** という4つの分類は、DeepLearning.AI（Andrew Ng氏）の講座でも採用されている非常にスタンダードかつ強力なフレームワークです。これは、**「テキストを入力して、テキストを出力する（Text-to-Text）」** というタスクベースの視点ではほぼ完璧に機能します。

しかし、**LLMスペシャリスト**として、「第一原理（LLMの仕組みと能力の本質）」からこの分類をさらに補完・改善し、一段階上のレベルへ引き上げる提案をさせてください。

### ---

**1\. 現状の分類（SITE）の分析と評価**

あなたの分類は、**「情報の操作（Information Manipulation）」** の観点において非常に理にかなっています。

* **Summarizing (情報量の圧縮):** 長文 $\\rightarrow$ 要点  
* **Expanding (情報量の増幅):** アイディア $\\rightarrow$ 文章、メール作成  
* **Transforming (形式の変更):** 翻訳、トーン変更、フォーマット変換 (JSON等)  
* **Inferring (意味の抽出):** 感情分析、タグ付け、情報の抜き出し

欠けている視点:  
これらはすべて「入力された情報をどう加工するか」という\*\*処理（Processing）に焦点が当たっています。しかし、最新のLLM活用（特にGPT-4やClaude 3.5 Sonnetなど）において重要となる「思考プロセス」や「外部との接続」\*\*の視点が少し不足しています。

### ---

**2\. スペシャリストによる改善案：認知能力に基づく「6つの階層」**

第一原理（LLMは確率的な次トークン予測器でありながら、文脈内学習と推論能力を持つ）に基づいて考えると、プロンプトは単なる「テキスト処理」だけでなく、\*\*「認知タスクの制御」\*\*と捉えるべきです。

あなたの4分類を包含しつつ、より現代的なLLM活用に対応する **「6つの機能階層（Cognitive Hierarchy）」** を提案します。

#### **① Processing (処理) \- あなたの4分類はここに集約されます**

既存の「Summarizing, Inferring, Transforming, Expanding」は、この「処理」レイヤーにおける中核機能です。これらは\*\*「既知の情報に対する操作」\*\*です。

#### **② Reasoning (推論・論理思考) \- 【追加推奨】**

単なる変換や推論（Inferring）を超え、論理的なステップを踏ませるプロンプトです。

* **Chain of Thought (CoT):** 「ステップバイステップで考えて」  
* **Few-Shot Reasoning:** 例題を与えて論理構造を学ばせる  
* **Math/Logic:** 計算や論理パズルの解決  
* *なぜ必要か？:* LLMは直感的な回答（System 1）をしがちですが、論理的思考（System 2）を強制する必要があるからです。

#### **③ Role-Playing / Persona (役割・ペルソナ) \- 【追加推奨】**

「何をするか」だけでなく「誰として振る舞うか」を定義します。これにより、出力のバイアス、専門性、トーンを一括制御します。

* **例:** 「あなたは10年の経験を持つシニアPythonエンジニアとして振る舞ってください」  
* *第一原理的視点:* 文脈確率分布を特定の専門領域（ドメイン）に強く固定する（Conditioning）効果があります。

#### **④ Critique & Refinement (評価・自己改善) \- 【追加推奨】**

生成した結果を、LLM自身に評価・修正させるプロセスです。

* **Self-Correction:** 「上記のコードにバグがないか確認し、あれば修正せよ」  
* **Evaluation:** 「この文章の論理的整合性を0-10点で採点せよ」  
* *重要性:* 単発の生成（Expanding）では品質に限界があるため、ループ構造を作るために必須です。

#### **⑤ Instruction / Constraint (制約・指示)**

これはすべてのベースになりますが、明確に「やってはいけないこと（Negative Prompting）」や「出力形式の厳格な指定（System Prompt）」を含みます。

#### **⑥ Tool Use / Action (行動・外部接続) \- 【最先端】**

テキストを生成するのではなく、関数を呼び出したり、Web検索を行ったりするためのプロンプトです。

* **Function Calling:** APIを叩くためのJSONを生成する  
* **RAG (Retrieval-Augmented Generation):** 外部知識を参照して答える

### ---

**3\. 統合された新フレームワーク案**

あなたの4つの分類をベースに、上記を統合して再構築すると、以下のようになります。

| 分類カテゴリー | 定義 | 具体的なプロンプト要素 (あなたの分類 \+ α) |
| :---- | :---- | :---- |
| **1\. Generation (生成系)** | 0から1、または1から10を生み出す | **Expanding**, Creative Writing, Code Generation |
| **2\. Manipulation (操作系)** | 入力を加工・変形する | **Summarizing**, **Transforming**, Translation, Formatting |
| **3\. Analysis (分析系)** | 入力から意味や構造を抽出する | **Inferring**, Extraction, Classification, Sentiment Analysis |
| **4\. Reasoning (思考系)** | 論理的ステップを踏んで解を導く | **Chain of Thought**, Planning, Problem Solving (**New**) |
| **5\. Meta-Cognition (メタ認知系)** | 出力を評価・改善・制御する | **Role-Playing**, **Critique/Refinement**, Guardrails (**New**) |

### ---

**まとめ**

あなたの「Summarizing, Inferring, Transforming, Expanding」は、**「コンテンツ（情報）をどう扱うか」** という視点では非常に完成度が高い分類です。

そこに、スペシャリストとしての視点である **「LLMにどう思考させるか（Reasoning）」** と **「LLMをどう制御するか（Meta-Cognition）」** という要素を加えることで、よりFirst Principle（確率的生成モデルをどう知能として振る舞わせるか）に近い、包括的なフレームワークになります。

### **次のステップ**

あなたの現在の業務や学習において、特に\*\*「推論（Reasoning）」**や**「評価（Critique）」\*\*のプロンプトが必要になる場面はありますか？もしあれば、あなたの分類にそれらを組み込んだ具体的なプロンプトのテンプレートを作成します。

```

このフレームワークを身に付けたいが、フル活用できるか心配ですので、

スキルにして毎回のpromptでチェック・改善してくれるようにしたのがこのプロジェクトです。

README.md

````md
# Prompt Enhancer Skill

A Claude skill that automatically analyzes and enhances user prompts to maximize LLM output quality.

## Overview

This skill implements a **Cognitive Hierarchy Framework** based on first principles thinking about how LLMs process information. It classifies every incoming prompt into cognitive categories and applies targeted enhancements internally before processing.

## Features

- **Automatic Prompt Classification** - Categorizes prompts into 5 cognitive types
- **Ambiguity Detection** - Identifies vague prompts and asks clarifying questions
- **Internal Enhancement** - Improves prompts without user-visible changes
- **Multilingual Support** - Works with English, Japanese, Chinese, Spanish, French, German, Korean, and more
- **Cultural Awareness** - Adapts to direct vs. indirect communication styles

## Cognitive Categories

| Category | Description | Example Triggers |
|----------|-------------|------------------|
| **Generation** | Create new content | "write", "create", "draft" |
| **Manipulation** | Transform existing content | "summarize", "translate", "convert" |
| **Analysis** | Extract meaning/structure | "analyze", "classify", "extract" |
| **Reasoning** | Logical multi-step thinking | "why", "compare", "evaluate" |
| **Meta-Cognition** | Control behavior/quality | "act as", "review your answer" |

## Installation

### For Claude.ai Users

1. Download the `.skill` file from [Releases](../../releases)
2. Go to Claude.ai → Settings → Profile → Skills
3. Upload the `.skill` file
4. The skill activates automatically for all conversations

### For Developers

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/prompt-enhancer-skill.git

# The skill structure:
prompt-enhancer/
├── SKILL.md                           # Main skill definition
└── references/
    └── enhancement-patterns.md        # Detailed enhancement patterns
```

## How It Works

1. **Classify** → Identifies prompt's cognitive type(s)
2. **Assess** → Rates ambiguity level (1-5)
3. **Decide** → Clarify if vague (≥4), enhance if clear
4. **Enhance** → Applies structural improvements internally
5. **Process** → Executes the enhanced prompt
6. **Respond** → Replies in user's language

## Framework Background

This skill is based on the "Cognitive Hierarchy" framework for understanding LLM capabilities:

- **Processing Layer** (Generation, Manipulation, Analysis) - How LLMs handle information
- **Reasoning Layer** - How LLMs think through problems step-by-step
- **Meta-Cognition Layer** - How to control and improve LLM behavior

Inspired by [DeepLearning.AI](https://www.deeplearning.ai/)'s prompt engineering principles and extended with reasoning and meta-cognitive capabilities.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### Areas for Improvement

- Additional language support
- Domain-specific enhancement patterns (code, legal, medical, etc.)
- Integration with other LLM tools

## License

MIT License - see [LICENSE](LICENSE) for details.

## Credits

- Framework concept based on discussions with Claude and Gemini
- Cognitive classification inspired by Andrew Ng's prompt engineering courses
- Built for the [Claude Skills](https://docs.anthropic.com/) ecosystem

````
