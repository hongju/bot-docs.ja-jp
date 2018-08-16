ユーザーは通常、"ヘルプ"、"キャンセル"、"やり直し" などのキーワードを使用して、ボット内の特定の機能にアクセスしようとします。 多くの場合、この状況は、会話の途中でボットが別の応答を期待しているときに起こります。 **グローバル メッセージ ハンドラー**を実装することで、そのような要求を適切に処理するようにボットを設計できます。
ハンドラーは "ヘルプ"、"キャンセル"、"やり直し" などの指定されたキーワードのユーザー入力を検証し、適切に応答します。 

![ユーザーの応答](~/media/designing-bots/capabilities/trigger-actions.png)

> [!NOTE]
> グローバル メッセージ ハンドラーでロジックを定義することで、すべてのダイアログにアクセスできるようになります。 個々のダイアログとプロンプトは、キーワードを無視しても問題ないように構成できます。