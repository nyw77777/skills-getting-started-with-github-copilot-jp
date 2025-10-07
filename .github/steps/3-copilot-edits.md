## Step 3: Copilot Edits を使用して作業をさらに _高速化_

前のステップでは、 GitHub Copilotへの具体的な指示を出し、結果として局所的な編集結果などを得ました。今回は、リポジトリでより総合的な作業を可能にする機能である Copilot Edits について説明します。

[Copilot - Edit Mode](https://code.visualstudio.com/docs/copilot/copilot-edits) は、**自然言語**を使用して**複数のファイル**に変更を加える AI を活用したコード編集セッションであり、編集内容をエディターで直接適用し、周囲のコードの完全なコンテキストを使用してその場で確認できます。

#### 主な特徴

- **複数ファイルの編集**: Copilot Edits はワークスペース内の複数ファイルに対して編集を加えることができます。
- **反復的なワークフロー**: 高速な反復を目的として設計されており、AI によって生成されたコードをレビュー、承認、または破棄できます。
- **インプレース 編集**: 生成されたコードをエディターに直接表示し、コード レビューのようなフローを提供します。
- **作業セット**: 編集を適用するファイルを定義できます。

#### 仕組み

1. **コンテキストを設定**: 作業セットに含めるファイルを選択します
1. **指示を入力**: 必要な変更内容を自然な言葉で記述します
1. **変更箇所のレビュー**: コード内で提案された変更を確認します
1. **承認(Accept)または破棄(Discard)**: 各提案を確認し、採用するかどうかを選択します
1. **反復**: 必要に応じて、追加の指示を出して変更を調整します

### :keyboard: Activity: Copilot を使用して新しい機能を追加する! :rocket:

1. Copilot Chat パネルが表示されていない場合は、再度開いてください。

1. Copilot Chat ウィンドウの下部にあるドロップダウンを使用して **Edit** モードに切り替えます。

   <img width="350" alt="image" src="https://github.com/user-attachments/assets/646fc94a-7d60-4821-b9cf-9ec6f4fd03d7" />

1. Web ページに関連するファイルを開いて、各エディタ ウィンドウ (またはファイル) をチャット パネルにドラッグし、それらをコンテキストとして使用するように Copilot に通知します。

   - `src/static/app.js`
   - `src/static/index.html`
   - `src/static/styles.css`

   > **Tip:** **コンテキストの追加** ボタンを使用して、GitHub の問題、コードベース全体、ターミナル ウィンドウの結果など、コンテキスト項目の他のソースを提供することもできます。

1. Copilot にプロジェクトを更新して、アクティビティの現在の参加者を表示するように依頼します。編集提案が到着して適用されるまでしばらく待ちます。

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > アクティビティ カードを編集して参加者セクションを追加してください。
   > そのアクティビティにすでにサインアップしている参加者が箇条書きリストとして表示されます。
   > 綺麗に作成することを忘れないでください。
   > ```

   - ファイル名の横に追加のアイコンが表示され、編集が提案されていることを示すエディタ ウィンドウが開きます。
   - エディター ウィンドウの右下に、推奨される編集パネルが表示され、推奨される変更にジャンプするためのコントロールが提供されます。

      <img width="200" alt="files with icons indicating they have been edited" src="https://github.com/user-attachments/assets/9c7c2e10-cd18-43c5-9947-cffd6dde0473" />

      <img width="250" alt="edit navigation panel" src="https://github.com/user-attachments/assets/a84965a5-2f43-4c93-a814-0fdeb3a06494" />

   <details>
   <summary>Need help? 🤷</summary><br/>

   関連するファイルを作業セットに追加することを忘れないでください。

   ![screenshot of working set](https://github.com/user-attachments/assets/d3eadc8e-583e-4a28-9e82-be128eab843b)

   </details>

1. 変更を単に受け入れる前に、Web サイトをもう一度チェックして、すべてが期待どおりに更新されていることを確認してください。以下は更新されたアクティビティカードの例です。アプリを再起動するか、ページを更新する必要がある場合があります。

   <img width="350" alt="Activity card with participant info" src="https://github.com/user-attachments/assets/c4d56187-4791-4c8e-87d7-d5ce7cdc0bee" />

   > **Note:** アクティビティカードの外観は異なる場合があります。 Copilot は常に同じ結果を生成するとは限りません。

   <details>
   <summary>Need help? 🤷</summary><br/>
   Web サイトが読み込まれない場合は、次の点を確認してください。

   - VS Code デバッガーを再起動して、Web サイトの最新バージョンが提供されていることを確認します。
   - URL を忘れた場合、またはウィンドウを閉じた場合は、Step 1 を確認してください。
   - Web ページを何度か更新するか、プライベートウィンドウを開いて新しいコピーを開いてみてください。

   </details>

1. 変更が適切であることを確認したので、パネルを使用して提案された各編集を順に実行し、**保持** を押して変更を適用します。

   > **Tip:** チャット インターフェイスを使用して、変更を直接受け入れたり、変更したり、追加の指示を提供して変更を調整したりできます。

1. 新機能が完成したら、変更を GitHub に **コミット**して**プッシュ**してください。

1. Mona があなたの作業をチェックし、フィードバックを提供し、最後のレッスンを共有するまでしばらくお待ちください。もうすぐ完成です！

1. (optional) If you would like an ungraded bonus step to briefly introduce Agent mode, **add an issue comment** asking **@professortocat** about Copilot Agent mode. 🚀

   ```txt
   Hey @professortocat, Agent mode sounds pretty cool. Can you please tell me more about it?
   ```

<details>
<summary>Having trouble? 🤷</summary><br/>

If you don't get feedback, here are some things to check:

- Make sure your commit the changes in the `src/static/` directory to the branch `accelerate-with-copilot` and pushed/synchronized to GitHub.
- If Mona found a mistake, simply make a correction and push your changes again. Mona will check your work as many times as needed.

</details>
