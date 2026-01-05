---
description: >-
  GitBookをMCPとしてClaudeから呼び出す価値を解説。コンテキスト管理の効率化、知識の最新性維持、マルチプラットフォーム対応など、RAG-likeな仕組みが実現する新しいワークフローを紹介します。
icon: sunglasses
---

# GitBookスペースをMCPとして、Claudeコネクタから呼び出す

## 価値

* コンテキスト管理の効率化：RAG-likeな仕組みにより、毎回GitBookの内容全体をコンテキストとして渡す必要がなくなります。
* マルチソース統合の可能性：複数のGitBookスペースを単一のClaudeセッションから横断的に検索・参照できます。
* チーム協働の促進：チームメンバー全員が同じ知識ベースにアクセスできる環境を提供します。ドキュメントの「どこに何が書いてあるか」を探す時間を削減し、実作業に集中できます。
* 引用元の透明性：MCPを通じた検索結果には、元のGitBookページへのリンクが含まれ、情報の信頼性検証が容易になります。
* 知識の動的な最新性：GitBookのコンテンツが更新されれば、Claudeが参照する情報も自動的に最新化されます。Single Source of Truthとして機能します。
* マルチプラットフォーム対応の基盤：Claude、Gemini、Codexなど複数のLLMプラットフォームで作業する際、GitBookを中立的な知識ベースとして各プラットフォームから参照できます。プラットフォーム固有のメモリー機能に依存せず、ポータブルな知識管理が実現できます。
* プライベート情報の安全な管理：重要情報や内部プロセスなど、公開できない情報をGitBookのプライベートスペースで管理しつつ、Claudeから安全にアクセスできます。Web検索では取得できない組織固有の知識を活用できるようになります。

## Step-by-Step

### Step1: MCPサーバーのURLをコピー

＊自分は[ページ](https://baylor2089.gitbook.io/ai-product-design-by-baylor/naze2026hagitbookwomerubekikax-gitbookgano)ではなく直接[スペース](https://baylor2089.gitbook.io/ai-product-design-by-baylor/)からコピーしました。

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### Step2: Claudeの\[設定 - コネクタ]からカスタムコネクタを追加

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### Step3: 専用スキルを作成し、呼び出しパターンを定義する

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

### Step4: Claude(Web/Desktop)から必要に応じて呼び出す

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

## 関連ソース

* GitBook
  * [MCP servers for published docs](https://gitbook.com/docs/publishing-documentation/mcp-servers-for-published-docs)
  * [Site MCP servers](https://gitbook.com/docs/developers/gitbook-api/api-reference/docs-sites/site-mcp-servers)
* Claude
  * [Using the Connectors Directory to extend Claude’s capabilities](https://support.claude.com/en/articles/11724452-using-the-connectors-directory-to-extend-claude-s-capabilities)
