<img width="215" height="38" alt="image" src="https://github.com/user-attachments/assets/a228bddd-c116-4215-bc18-5a7689f4a458" />## Step 2: Copilot を使用して作業を完了する

前のステップでは、GitHub Copilot がプロジェクトへの参加を支援してくれました。それだけでも時間を大幅に節約できますが、次は作業を進めてみましょう。

最近、学生が同じアクティビティに 2 回登録するというバグがあることがわかりました。それは決して受け入れられないので、修正しましょう。

残念ながら、この問題を解決するための情報はほとんど提供されていませんでした。そこで、Copilot に問題領域の発見と潜在的な解決策の作成を手伝ってもらいましょう。

その前に、Copilot についてもう少し詳しく学びましょう 🧑‍🚀

### Copilot はどのように機能しますか？

端的に言えば、Copilot は非常に専門化された同僚のように考えることができます。彼らに対して効果的に対応するには、背景情報 (コンテキスト:context) と明確な指示 (プロンプト:prompts) を提供する必要があります。さらに、人々（Copilot）は独自の経験 (モデル:models) によって得意分野が異なります。

- **コンテキストを提供するにはどうすればよいでしょうか？:** 私たちのコーディング環境では、Copilot は自動的に近くのコードを考慮してタブを開きます。チャットを使用している場合は、ファイルを明示的に参照することもできます。

- **どのモデルを選択すればよいでしょうか？:** 今回の演習では、それはそれほど重要ではありません。さまざまなモデルを試してみるのも楽しみの 1 つですが、今回の本筋ではありません。 🤖

- **プロンプトを作成するにはどうすればよいですか？:** 明示的かつ明確であることは、Copilot が最高の仕事をするのに役立ちます。ただし、一部の従来のシステムとは異なり、フォローアップのプロンプトでいつでも自分の方向性を明確にすることができます。

> [!TIP]
> 他にも、[chat participants](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-participants), [chat variables](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-variables), [slash commands](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#slash-commands-1), [MCP tools](https://code.visualstudio.com/docs/copilot/chat/mcp-servers)など、Copilot の知識と機能を補う方法がいくつかあります。

### :keyboard: Activity: Copilot を使用して登録されたバグを修正する :bug:

1. Copilot にバグの原因を示唆してもらいましょう。**Copilot Chat** パネルの **Ask mode** を使い次のように質問します。

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > @workspace 学生は 1 つのアクティビティに 2 回登録できます。
   > このバグはどこから来たのでしょうか？
   > ```

   <details>
   <summary>@workspace とは？</summary>

   素晴らしい質問です！これは、プロジェクト リポジトリを探索し、関連する追加コンテキストを含めようとする特殊な [chat participant](https://docs.github.com/en/copilot/using-github-copilot/copilot-chat/github-copilot-chat-cheat-sheet?tool=vscode#chat-participants) です。

   </details>

1. 問題が `src/app.py` ファイルと `signup_for_activity` メソッドにあることがわかったので、Copilot の推奨に従って、(半手動で) 修正してみましょう。コメントから始めて、Copilot に修正を完了させます。

   1. VS Code で、**エクスプローラー タブ** からファイルを選択して`src/app.py` ファイルを開きます。

   1. ファイルの下部付近をスクロールして、`signup_for_activity` メソッドを見つけます。

   1. 生徒の追加について説明しているコメント行(Add student)を見つけます。この上で、登録チェックを行うのが論理的と思われます。

   1. 以下のコメントを入力し、Enter キーを押して次の行に進みます。しばらくすると、Copilot からの提案とともに一時的なシャドウ テキストが表示されます。 :tada:

      ```python
      # 学生がまだサインアップしていないことを確認する
      ```

   1. `Tab` を押して、Copilot の提案を受け入れ、シャドウテキスト（確定前のグレーテキスト）をコードに変換します。

      > **Tip:** 他の候補を表示したい場合は、`Tab`を押す代わりに、シャドウテキストの候補の上にカーソルを置くと、ツールバーが表示されます。矢印を使用して他の候補を選択するか、3 つの点 `...` と `完了パネルを開く` オプションを使用してすべての候補を専用パネルに表示します。

   <details>
   <summary>結果の例</summary><br/>

   Copilot は日々成長しているため、常に同じ結果が得られるとは限りません。提案に満足できない場合は、この演習の作成中に生成された有効な提案結果の例を次に示します。それを使用して先に進むことができます。

   ```python
   @app.post("/activities/{activity_name}/signup")
   def signup_for_activity(activity_name: str, email: str):
      """Sign up a student for an activity"""
      # Validate activity exists
      if activity_name not in activities:
         raise HTTPException(status_code=404, detail="Activity not found")

      # Get the activity
      activity = activities[activity_name]

      # Validate student is not already signed up
      if email in activity["participants"]:
        raise HTTPException(status_code=400, detail="Student is already signed up")

      # Add student
      activity["participants"].append(email)
      return {"message": f"Signed up {email} for {activity_name}"}
   ```

   </details>

### :keyboard: Activity: Copilot にサンプル データを生成させる 📋

新しいプロジェクトの開発では、テスト用に現実味のある偽のデータを用意しておくと役立つことがよくあります。 Copilot はそのようなタスクに優れているため、さらにサンプル アクティビティを追加し、**Inline Chat** を使用して Copilot と対話する別の方法を紹介しましょう。

**Inline Chat** と **Copilot Chat** パネルは非常によく似たツールですが、自動コンテキストが若干異なります。そのため、Copilot Chat はプロジェクトについて説明するのに適していますが、特定の行や機能について質問する場合はインライン チャットの方が自然かもしれません。

1. まだ開いていない場合は、`src/app.py` ファイルを開きます。

1. 上部付近 (約 23 行目) で、`activities` 変数を見つけます。ここで、例の課外活動が設定されています。

1. 関連する行のいずれかをクリックし、キーボード コマンド `Ctrl + I` (Windows) または `Cmd + I` (Mac) を使用して Copilot インライン チャットを起動します。

   > **Tip:** Copilot インライン チャットを起動するもう 1 つの方法は、選択した行のいずれかを `right click` -> `Copilot` ->`Editor Inline Chat`です。

1. 次のプロンプト テキストを入力し、Enter キーを押すか、**Send and Dispatch** ボタンを押します。

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > スポーツ関連のアクティビティを 2 つ、芸術的なアクティビティを 2 つ、
   > 知的アクティビティを 2 つ追加します。
   > ```

1. しばらくすると、Copilot はコードへの変更を直接開始します。追加と削除を簡単に識別できるように、変更は異なるスタイルで表示されます。少し時間をかけて内容を確認し、**Accept** ボタンを押してください。

   <details>
   <summary>結果の例</summary><br/>

   Copilot は日々成長しているため、常に同じ結果が得られるとは限りません。提案に満足できない場合は、この演習の作成中に生成された結果の例を次に示します。問題が発生した場合は、これを使用して先に進むことができます。

   ```python
   # In-memory activity database
   activities = {
      "Chess Club": {
         "description": "Learn strategies and compete in chess tournaments",
         "schedule": "Fridays, 3:30 PM - 5:00 PM",
         "max_participants": 12,
         "participants": ["michael@mergington.edu", "daniel@mergington.edu"]
      },
      "Programming Class": {
         "description": "Learn programming fundamentals and build software projects",
         "schedule": "Tuesdays and Thursdays, 3:30 PM - 4:30 PM",
         "max_participants": 20,
         "participants": ["emma@mergington.edu", "sophia@mergington.edu"]
      },
      "Gym Class": {
         "description": "Physical education and sports activities",
         "schedule": "Mondays, Wednesdays, Fridays, 2:00 PM - 3:00 PM",
         "max_participants": 30,
         "participants": ["john@mergington.edu", "olivia@mergington.edu"]
      },
      "Basketball Team": {
         "description": "Competitive basketball training and games",
         "schedule": "Tuesdays and Thursdays, 4:00 PM - 6:00 PM",
         "max_participants": 15,
         "participants": []
      },
      "Swimming Club": {
         "description": "Swimming training and water sports",
         "schedule": "Mondays and Wednesdays, 3:30 PM - 5:00 PM",
         "max_participants": 20,
         "participants": []
      },
      "Art Studio": {
         "description": "Express creativity through painting and drawing",
         "schedule": "Wednesdays, 3:30 PM - 5:00 PM",
         "max_participants": 15,
         "participants": []
      },
      "Drama Club": {
         "description": "Theater arts and performance training",
         "schedule": "Tuesdays, 4:00 PM - 6:00 PM",
         "max_participants": 25,
         "participants": []
      },
      "Debate Team": {
         "description": "Learn public speaking and argumentation skills",
         "schedule": "Thursdays, 3:30 PM - 5:00 PM",
         "max_participants": 16,
         "participants": []
      },
      "Science Club": {
         "description": "Hands-on experiments and scientific exploration",
         "schedule": "Fridays, 3:30 PM - 5:00 PM",
         "max_participants": 20,
         "participants": []
      }
   }
   ```

   </details>

### :keyboard: Activity: Copilot を使用して仕事を説明する 💬

バグを修正し、サンプルアクティビティを拡張できたのは素晴らしい仕事です。今度は、再び Copilot の助けを借りて、作業をコミットして GitHub にプッシュしましょう。

1. 左側のサイドバーで`ソース管理`タブを選択します。

   > **Tip:** ソース管理領域からファイルを開くと、単にファイルを開くのではなく、元のファイルとの違いが表示されます。

1. `app.py` ファイルを見つけて `+` 記号を押して、ステージング領域に変更をまとめて収集します。

   ![image](https://github.com/user-attachments/assets/7d3daf4e-4125-4775-88a7-33251cd7293e)

1. 段階的変更のリストの上にある **メッセージ** テキスト ボックスを見つけます。ただし、今は **何も入力しないでください**。

   - 通常、ここに変更の簡単な説明を書きますが、今では Copilot が手伝ってくれます。

1. **メッセージ** テキスト ボックスの右側にある **コミットメッセージの生成** ボタン (きらきらアイコン) を見つけてクリックします。

1. **コミット** ボタンと **変更の同期** ボタンを押して、変更を GitHub にプッシュします。

1. Mona があなたの作業をチェックし、フィードバックを提供し、次のレッスンを共有するまでお待ちください。

<details>
<summary>Having trouble? 🤷</summary><br/>

If you don't get feedback, here are some things to check:

- Make sure your pushed the `src/app.py` file changes to the branch `accelerate-with-copilot`.

</details>
