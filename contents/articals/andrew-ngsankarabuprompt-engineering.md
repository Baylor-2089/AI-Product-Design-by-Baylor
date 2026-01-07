---
description: 「Summarizing（要約）」「Inferring（推論）」「Transforming（変換）」「Expanding（拡張）」
icon: sparkle
---

# Andrew Ngさんから学ぶPrompt engineering+拡張

CourseraでAndrew Ngさんの「[ChatGPT Prompt Engineering for Developers](https://www.coursera.org/projects/chatgpt-prompt-engineering-for-developers-project)」を見かけて、1時間で終わる初心者向けの基礎プロンプトエンジニアリングクラスだが、そごく根本的なところを構造化で補完してくれました。

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

特に、コアフレームワークとなる４つのタイプを見て、「確かに！」となりました。

この４つのタイプに一旦分類して（自分の頭の中で）、タイプ別に特化したprompt形式・パターンで指示を出せばより安定した高品質なアウトプットができる。

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

でも同時にちょっと振り返りながら考えてみたら、欠けてる部分あるんじゃないかと思い、

Claudeに

{% code overflow="wrap" %}
```
First Principleで考えると、LLM向けのPromptをSummarizing、Inferring、Transforming、Expandingよという四つの分類にできると自分的に考えているが、LLMスペシャリストとして、私の考えを補完し、改善してください。
```
{% endcode %}

と相談したところ、すごい納得のいく形で拡張してくれたのでシェアします👇



素晴らしい着眼点です。「First Principles（第一原理）」に基づいて、物事を構成要素に分解して考えるアプローチは、LLMの理解を深める上で非常に有効です。

あなたの提示された **「Summarizing（要約）」「Inferring（推論）」「Transforming（変換）」「Expanding（拡張）」** という4つの分類は、DeepLearning.AI（Andrew Ng氏）の講座でも採用されている非常にスタンダードかつ強力なフレームワークです。これは、**「テキストを入力して、テキストを出力する（Text-to-Text）」** というタスクベースの視点ではほぼ完璧に機能します。

しかし、**LLMスペシャリスト**として、「第一原理（LLMの仕組みと能力の本質）」からこの分類をさらに補完・改善し、一段階上のレベルへ引き上げる提案をさせてください。

#### ---

**1. 現状の分類（SITE）の分析と評価**

あなたの分類は、**「情報の操作（Information Manipulation）」** の観点において非常に理にかなっています。

* **Summarizing (情報量の圧縮):** 長文->要点
* **Expanding (情報量の増幅):** アイディア -> 文章、メール作成
* **Transforming (形式の変更):** 翻訳、トーン変更、フォーマット変換 (JSON等)
* **Inferring (意味の抽出):** 感情分析、タグ付け、情報の抜き出し

欠けている視点:\
これらはすべて「入力された情報をどう加工するか」という処理（Processing）に焦点が当たっています。しかし、最新のLLM活用において重要となる「思考プロセス」や「外部との接続」の視点が少し不足しています。

#### ---

**2. スペシャリストによる改善案：認知能力に基づく「6つの階層」**

第一原理（LLMは確率的な次トークン予測器でありながら、文脈内学習と推論能力を持つ）に基づいて考えると、プロンプトは単なる「テキスト処理」だけでなく、「認知タスクの制御」と捉えるべきです。

あなたの4分類を包含しつつ、より現代的なLLM活用に対応する **「6つの機能階層（Cognitive Hierarchy）」** を提案します。

**① Processing (処理) - あなたの4分類はここに集約されます**

既存の「Summarizing, Inferring, Transforming, Expanding」は、この「処理」レイヤーにおける中核機能です。

* **Summarizing** : 情報量の圧縮
* **Expanding**: 情報量の増幅
* **Transforming**: 形式の変更
* **Inferring**: 意味の抽出

**② Reasoning (推論・論理思考)**&#x20;

単なる変換や推論を超え、論理的なステップを踏ませるプロンプトです。

* **Chain of Thought (CoT):** 「ステップバイステップで考えて」
* **Few-Shot Reasoning:** 例題を与えて論理構造を学ばせる
* **Math/Logic:** 計算や論理パズルの解決
* _なぜ必要か？:_ LLMは直感的な回答（System 1）をしがちですが、論理的思考（System 2）を強制する必要があるからです。

**③ Role-Playing / Persona (役割・ペルソナ)**&#x20;

「何をするか」だけでなく「誰として振る舞うか」を定義します。これにより、出力のバイアス、専門性、トーンを一括制御します。

* **例:** 「あなたは10年の経験を持つシニアPythonエンジニアとして.....」
* _第一原理的視点:_ 文脈確率分布を特定の専門領域（ドメイン）に強く固定する（Conditioning）効果があります。

**④ Critique & Refinement (評価・自己改善)**&#x20;

生成した結果を、LLM自身に評価・修正させるプロセスです。

* **Self-Correction:** 「上記のコードにバグがないか確認し、あれば修正せよ」
* **Evaluation:** 「この文章の論理的整合性を0-10点で採点せよ」
* _重要性:_ 単発の生成（Expanding）では品質に限界があるため、ループ構造を作るために必須です。

**⑤ Instruction / Constraint (制約・指示)**

これはすべてのベースになりますが、明確に「やってはいけないこと（Negative Prompting）」や「出力形式の厳格な指定（System Prompt）」を含みます。

**⑥ Tool Use / Action (行動・外部接続)**&#x20;

テキストを生成するのではなく、関数を呼び出したり、Web検索を行ったりするためのプロンプトです。

* **Function Calling:** APIを叩くためのJSONを生成する
* **RAGやMCPなどとの接続**



