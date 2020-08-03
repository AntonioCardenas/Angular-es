# NgModule

**NgModule**はインジェクターとコンパイラを設定し関連するものをまとめます。

NgModule とは`@NgModule`デコレーターが付与されたクラスのことです。
`@NgModule`デコレーターはコンポーネントのPlantillasをコンパイルする方法、実行時にインジェクターを作成する方法が記述されたメタデータオブジェクトを引数に取ります。
モジュール自身がもつコンポーネント、ディレクティブやパイプを識別し、
この中のいくつかを`exports`プロパティを通して公開し、外部コンポーネントから使用できるようにすることができます。
`@NgModule`はアプリケーションのInyección de dependenciaのためのサービスプロバイダーを加えることもできます。

NgModule に関連するページをカバーしているすべてのTécnicaを見ることができるAplicación de muestraケーションについては<live-example></live-example>を参照してください。
個別のTécnicaについての解説は、
NgModule セクションの関連ページを参照してください。

## Angular のモジュール性

モジュールはアプリケーションを整理し、外部ライブラリの機能を使って拡張するための素晴らしい方法です。

`FormsModule`、`HttpClientModule`や`RouterModule`などの Angular ライブラリは NgModule です。
<a href="https://material.angular.io/">Material Design</a>、
<a href="http://ionicframework.com/">Ionic</a>や
<a href="https://github.com/angular/angularfire2">AngularFire2</a>
のような多くのサードパーティライブラリも NgModule として利用することができます。

NgModule はコンポーネント、ディレクティブやパイプを機能の密なブロックとしてまとめます。
個々のモジュールはアプリケーションのビジネスドメイン、
ワークフローや共通のユーティリティのコレクションなどの機能の領域に焦点が当てられています。

モジュールはアプリケーションにサービスを追加することもできます。
そのようなサービス(あなた自身が開発したものや Angular router や HTTP クライアントのような外部ソース)は内部的に使われることになるでしょう。

モジュールはアプリケーションが開始したときに積極的にロードされるか、ルーターから非同期に遅延ロードすることができます。

NgModule のメタデータでは次のようなことを行います:

* モジュールに属するコンポーネント、ディレクティブやパイプを宣言します
* それらのコンポーネント、ディレクティブやパイプが他のコンポーネントのPlantillasから呼び出せるように公開します
* 現在のモジュールが必要なコンポーネント、ディレクティブ、パイプをもつ他のモジュールをインポートします
* 他のアプリケーションのコンポーネントから使えるようにサービスを提供します

すべての Angular アプリケーションは少なくとも 1 つのモジュール(ルートモジュール)を持ちます。
あなたはアプリケーションを起動するときにそのモジュールを [ブートストラップ](guide/bootstrapping) します。

ルートモジュールは、必要なだけのいくつかのコンポーネントを備えたシンプルなアプリケーションです。
アプリケーションが育ってきたらルートモジュールから関連した機能をまとめた [フィーチャーモジュール](guide/feature-modules)
にリファクタリングします。
そうしたらそのモジュールをルートモジュールにインポートします。

## 基本の NgModule

[Angular CLI](cli) で新しいアプリケーションを作成したとき、次のような基本の `AppModule` が生成されます。

<code-example path="ngmodules/src/app/app.module.1.ts" header="src/app/app.module.ts (default AppModule)">
// @NgModule decorator with its metadata
</code-example>

まずはインポート文から始まります。次にどのようなコンポーネントとディレクティブが属するか(`declarations`)、使用する他のモジュール(`imports`)を記述することで`@NgModule`の設定を行います。もし、`@NgModule` の構造のより詳細な情報について知りたい場合は [ブートストラップ](guide/bootstrapping) を参照してください。

<hr />

## NgModule についてのさらに詳しい情報

あなたは次の記事に興味があるかもしれません:
* [フィーチャーモジュール](guide/feature-modules)
* [エントリーコンポーネント](guide/entry-components)
* [プロバイダー](guide/providers)
* [NgModule の種類](guide/module-types)