## Step 4: プルリクエスト内で GitHub Copilot を使用する

Congratulations! この演習 (および VS Code) のコーディングパートは終了です。今度は私たちの作業をマージする時が来ました :tada: 最後に、プル リクエストを高速化できる、アクセスが制限された 2 つの Copilot 機能について学びましょう

#### Copilot pull request summaries

通常は、メモを確認してメッ​​セージをコミットし、プル リクエストの説明として要約します。特にコミットメッセージに一貫性がない場合、またはコードが十分に文書化されていない場合、これには時間がかかることがあります。幸いなことに、Copilot はプル リクエスト内のすべての変更を考慮し、重要なハイライトと参照を提供できます。

> [!NOTE]
> この機能は、**GitHub Copilot Free**. [[docs]](https://docs.github.com/en/enterprise-cloud@latest/copilot/using-github-copilot/using-github-copilot-for-pull-requests/creating-a-pull-request-summary-with-github-copilot) ではご利用いただけません。

#### Copilot code review

私たちの仕事に対する多様な視点は役立つことが多いので、通常のピアコードレビュープロセスの前にCopilotに最初の作業を依頼しましょう。Copilot は、簡単な調整で修正できる一般的な間違いを見つけるのに優れていますが、利用者側（あなた）が責任を持って使用するということを忘れないでください。

> [!NOTE]
> この機能は、 **GitHub Copilot Free**. [[docs]](https://docs.github.com/en/copilot/using-github-copilot/code-review/using-copilot-code-review) ではご利用いただけません。

### :keyboard: Activity: Copilot を使用して PR(Pull Request) を要約して確認する

**Copilot pull request summaries** と **Copilot code review** はどちらも利用に制限があります。このため、このアクティビティはほとんどがオプションです。アクセスできる場合は、ぜひ試してみてください。そうでない場合は、オプションの手順をスキップできます。

1. Web ブラウザで別のタブを開き、この演習のリポジトリに移動します。

1. 新しいプル リクエストの作成を提案する **通知バナー** が表示される場合があります。それをクリックするか、上部の **Pull Requests** タブを使用して新しいプル リクエストを作成します。次の詳細を確認ください。

   - **base:** `main`
   - **compare:** `accelerate-with-copilot`
   - **title:** `Add registration validation and more activities`

1. (Optional) **Add a description** 領域で、必要に応じて編集モードに入り、**Copilot actions** アイコンと **Summary** アクションをクリックします。しばらくすると、Copilot が説明を追加します。 :memo:

   <img alt="Copilot summarize button " width="300px" src="https://github.com/user-attachments/assets/3fc5fab4-db03-4ab8-8a16-cdd71ec2ded0">

1. (Optional) 上部の右側の情報パネルで、**Reviewers** セクションを見つけて、**Copilot icon**の横にある **Request** ボタンをクリックします。 Copilot がプル リクエストにレビュー コメントを追加するまでお待ちください。

   <img alt="Copilot review button" width="300px" src="https://github.com/user-attachments/assets/39b15002-a235-4c25-b09d-6a8097e27b62">

   > **Tip:** Copilot がレビューを要求されたというログ エントリに注目してください。

1. 下部にある **Merge pull request** ボタンを押します。すばらしいですね！これで完了です  :tada:

1. Mona があなたの作業をチェックし、フィードバックを提供し、このレッスンの最終レビューを投稿するまでしばらくお待ちください。
