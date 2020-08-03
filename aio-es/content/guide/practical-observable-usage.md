# 実用的な observable の使用法

observable が特に便利な分野の例をいくつか紹介します。

## 事前サジェスト

Observableは、事前サジェストの実装を簡素化できます。一般的に、事前入力は一連の別々のタスクを実行する必要があります。

* 入力からデータを待ち受ける。
* 値をトリム (空白を削除) し、最短であることを確認する。
* デバウンス (すべてのキーストロークに対して API リクエストを送信しないようにする代わりに、キーストロークの中断を待つ)。
* 値が同じままであれば、リクエストを送信しない (たとえば、文字を急に打ち、次にバックスペースなど)。
* 更新された結果によって元の結果が無効になる場合、進行中の AJAX リクエストをキャンセルする。

これらすべてを JavaScript で書くとかなり複雑になる可能性があります。Observableでは、簡単な一連の RxJS 演算子を使用できます。

<code-example path="practical-observable-usage/src/typeahead.ts" header="事前サジェスト"></code-example>

## 指数関数的バックオフ

指数関数的バックオフは失敗後に API をリトライし、連続した各失敗の後のリトライの間隔を長くし、リクエストが失敗したと見なされる最大回数でリトライする方法です。これは Promise や AJAX 呼び出しを追跡する他の方法で実装するのは非常に複雑なことがあります。Observable では、非常に簡単です：

<code-example path="practical-observable-usage/src/backoff.ts" header="指数関数的バックオフ"></code-example>