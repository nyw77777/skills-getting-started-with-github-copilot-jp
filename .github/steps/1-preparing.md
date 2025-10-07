## Step 1: Hello Copilot

 **"GitHub Copilot 入門"** 演習へようこそ! :robot:

この演習では、さまざまな GitHub Copilot 機能を使用して、マージントン高校の生徒が課外活動にサインアップできる Web サイトで作業します。 🎻 ⚽️ ♟️

<img width="600" alt="screenshot of Mergington High School WebApp" src="https://github.com/user-attachments/assets/472398fd-1aa1-4084-b443-4e242deb30d9" />

### GitHub Copilot とは?

<img width="150" align="right" alt="copilot logo" src="https://github.com/user-attachments/assets/4d22496d-850b-4785-aafe-11cba03cd5f2" />

GitHub Copilot は、より少ない労力でより迅速にコードを作成できるようにする AI コーディング アシスタントであり、問​​題解決とコラボレーションにより多くのエネルギーを集中できるようにします。

GitHub Copilot は、開発者の生産性を向上させ、ソフトウェア開発のペースを加速することが証明されています。詳細については [Research: quantifying GitHub Copilot’s impact on developer productivity and happiness in the GitHub blog.](https://github.blog/news-insights/research/research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/) を参照ください。

最も一般的なやり取りは次のとおりです。 :

- **Inline suggestions**: キー入力をすると、Copilot は近くのコンテキストを使用して、エディターにコードを直接提案します。 [Intellisense](https://code.visualstudio.com/docs/editor/intellisense) などのコード補完ツールを使用したことがある場合、これはよく知られた操作になりますが、補完が関数全体である場合がある点が異なります。
- **Copilot - Ask Mode**: コーディング関連の質問ができる専用のチャット パネル。オンライン AI アシスタント チャットを使用したことがある場合は、これに親しみを感じるでしょう。ただし、大きな違いは、プロジェクト ファイルが、カスタマイズされた応答を提供するための自動コンテキストを提供することです。
- **Copilot - Edit Mode**: Ask Modeに似ていますが、会話的ではありません。 Copilot は、選択したファイルに変更を加えてリクエストを実装します。
- **Copilot - Agent Mode**: Copilot は、リクエストが達成されるまで繰り返し実行されます。コンテキストを選択し、コードを変更し、ターミナル コマンドを実行し、ツールを実行します。そして最も重要なこととして、その作業を確認して調整を行います。

> [!TIP]
> 現在および今後の機能の詳細については、[GitHub Copilot Features](https://docs.github.com/en/copilot/about-github-copilot/github-copilot-features) ドキュメントを参照してください。さまざまな [models](https://docs.github.com/en/github-models) を選択して、独自の [extensions](https://github.com/features/copilot/extensions) を作成することもできますが、それは別のレッスンになります。

### GitHub Copilot を使用するにはどうすればよいですか?

作業を進めると、Web サイトのさまざまな場所や、VS Code、Jet Brains、Xcode などのお気に入りのコーディング環境で GitHub Copilot が役立つことがわかります。ただし、今日のコーディングでは、[Codespace](https://github.com/features/codespaces) として知られる事前構成された開発環境で VS Code を使用して練習します。

### :keyboard: Activity: Copilot Chat からプロジェクトの紹介を取得する

開発環境を起動し、copilot を使用してプロジェクトについて少し学習してから、テスト実行してみましょう。

1. 下のボタンを使用して、**Create Codespace** ページを新しいタブで開きます。デフォルトの構成を使用します。

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

1. **Repository**フィールドがオリジナルではなく演習のコピーであることを確認し、緑色の **Create Codespace** ボタンをクリックします。

   - ✅ コピー : `/{{full_repo_name}}`
   - ❌ オリジナル : `/matakaha/getting-started-with-github-copilot-jp`

1. Visual Studio Code がブラウザーに読み込まれるまでしばらく待ちます。

1. 左側のサイドバーで拡張機能タブをクリックし、 `GitHub Copilot` 拡張機能と `Python` 拡張機能がインストールされ有効になっていることを確認します。

   <img width="350" alt="copilot extension for VS Code" src="https://github.com/user-attachments/assets/ef1ef984-17fc-4b20-a9a6-65a866def468" />

   <img width="350" alt="python extension for VS Code" src="https://github.com/user-attachments/assets/3040c0f5-1658-47e2-a439-20504a384f77" />

1. VS Code の上部で **~~Copilot~~ Chat icon** を見つけてクリックし、Copilot Chat パネルを開きます。

   <img width="150" alt="image" src="https://github.com/user-attachments/assets/5e64db46-95cb-415d-badc-b6b8677f10c1" /> 

   <img width="147" height="50" alt="image" src="https://github.com/user-attachments/assets/5c9f8887-68f9-426d-9ad9-09066f341645" />

1. GitHub Copilot を初めて使用する場合、続行するには使用条件に同意する必要があります。

1. 以下のプロンプトを入力して、Copilot にプロジェクトを紹介するよう依頼します。このプロンプトには Copilot **Ask Mode** を使用します。

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > @workspace このプロジェクトの構成を簡単に説明してください。
   > 実行するにはどうすればよいですか?
   > ```

   > **Note**: Copilot が推奨する指示に従う必要はありません。すでに環境をご用意しております。

   <details>
   <summary>@workspace とは？</summary>
   細かな点に気づかれたことはステキですが、今はそのまま使ってみましょう🤓 次のステップで説明します。
   </details>

1. プロジェクトについて少し理解できたところで、実際に実行してみましょう。左側のサイドバーで「実行とデバッグ」タブを選択し、**デバッグの開始** アイコンを押します

   <img width="300" alt="image" src="https://github.com/user-attachments/assets/50b27f2a-5eab-4827-9343-ab5bce62357e" />

1. Web ページがブラウザーで実行されているのを確認したいので、URL とポートを見つけてみましょう。表示されていない場合は、下部パネルを展開して [**ポート**] タブを選択します。

1. リストでポート `8000` と関連リンクを見つけます。リンクの上にマウスを置き、**ブラウザで開く** アイコンを選択します。

   ![image](https://github.com/user-attachments/assets/92d5642e-ce99-4a66-850c-2d311a673596)

### :keyboard: Activity: Copilotをターミナルコマンドで利用する🙋

素晴らしい！アプリに慣れ、機能することがわかったので、いくつかのカスタマイズを行うことができるように、ブランチの開始を手伝ってもらうために copilot に依頼しましょう。

1. アプリを開いている場合、アプリはそのままにしてVS Codeに戻ります。

1. 下部パネルで、**ターミナル** タブを選択します。右側でプラス記号「+」をクリックして、新しいターミナル ウィンドウを作成します。

   > **Note:** これにより、Web アプリケーション サービスをホストしている既存のデバッグ セッションが停止するのを回避できます。

1. 新しいターミナル ウィンドウ内で、キーボード ショートカット `Ctrl + I` (Windows) または `Cmd + I` (Mac) を使用して、**Copilot のターミナル インライン チャット**を表示します。

1. Copilot に忘れていたコマンド、つまりブランチの作成と公開を思い出すのを手伝ってもらいましょう。（あなたは今、Gitのコマンドを完全に忘れたことになっています、お付き合いください。）

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > "accelerate-with-copilot"という新しい Git ブランチを作成して公開するにはどうすればよいですか？
   > ```

   > **Tip:** Copilot が希望どおりの結果を提供しない場合は、いつでも必要なことを説明し続けることができます。Copilotは、フォローアップ応答のために会話履歴を記憶します。

1. `実行` ボタンを押すと、Copilot が端末コマンドを挿入します。コピー＆ペーストする必要はありません。

1. しばらくしてから、VS Code の左側の下部ステータス バーを調べて、アクティブなブランチを確認します。 `accelerate-with-copilot`と表示されるはずです。そうであれば、このステップはすべて完了です。

1. ブランチが GitHub にプッシュされたので、Mona はすでに作業のチェックに忙しいはずです。少し待って、コメントを見てください。彼女が進捗状況と次のレッスンについて応答するのがわかります。

<details>
<summary>Having trouble? 🤷</summary><br/>

If you don't get feedback, here are some things to check:

- Make sure your created the branch with the exact name `accelerate-with-copilot`. No prefixes or suffixes.
- Make sure the branch was indeed published to your repository.

</details>
