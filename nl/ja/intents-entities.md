---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-09"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# インテントとエンティティーの計画
{: #planning-your-entities}

アプリケーションの*インテント*を計画するには、お客様が何をしたいか、アプリケーションでどのような処理を可能にしたいかを検討する必要があります。 ユーザーの入力に対して正しいインテントを選択することが、意味のある応答を返すための最初のステップです。 アプリケーションのインテントを決定すると、作成すべきダイアログ・フローが決まります。また、お客様の要求を実行するためにアプリケーションと統合する必要があるバックエンド・システム (顧客データベースや決済処理システムなど) も決まります。

*エンティティー*とは、ユーザー入力に含まれる用語またはオブジェクトであり、特定のインテントの説明や明確なコンテキストを表すものです。 インテントが動詞 (ユーザーがしたいこと) を表す場合、エンティティーは名詞 (アクションの対象物やコンテキストなど) を表します。 エンティティーにより、単一のインテントで複数の具体的なアクションを表すことができます。 エンティティーは、オブジェクトのクラスを定義するものであり、そのクラスで使用可能なさまざまなオブジェクトを複数の特定の値で表します。

基本的には、要求を取り込みたい場合やアクションを実行したい場合に、インテントを使用します。 要求やアクションへの対応方法に影響を与える情報を取り込みたい場合に、エンティティーを使用します。

例として、ユーザーが付属品をオン/オフできるコグニティブ・カーのダッシュボード・アプリケーションを作成するとします。

1.  実際のお客様の質問やコマンド、その他の入力をできる限り多く収集します。 専門家に発話の候補リストを作成してもらうよりも、実際のユーザー入力を使用するほうが、予期される入力についてイメージできます。 同じ種類の要求がさまざまなフレーズで表されることを忘れないでください。 例えば、次のサンプル発話はすべて、何かをオフにする要求を表しています。

    - `ヘッドライトをオフにして`
    - `ラジオのスイッチを切って`
    - `エアコンを停止して`

1.  サンプル・リストができたら、アプリケーションでサポートする機能に基づくカテゴリー別にサンプルを分類します。それらのカテゴリーが、定義するインテントになります。一方、アプリケーションでは、サンプルを使用して、新しい入力に含まれているインテントを検出できます。

    似すぎるインテントは作成しないでください。 類似するインテントは {{site.data.keyword.conversationshort}} サービスで区別することが難しい場合があります。 意味が近いインテントが複数あることがわかった場合は、それらを 1 つのインテントに統合し、エンティティーを使用して複数の応答をそのインテントで提供することができないか検討してください。
    {: tip}

    上記のサンプルはすべて同じインテント (何かをオフにする) を表しているので、このカテゴリーを `#turn_off` と呼ぶことができます。
お客様の入力がサンプルのいずれかと完全一致する必要はありません。インテントは、自然言語処理を利用して認識されます。
    {: tip}

1.  次に、エンティティーを使用して、ユーザーがオフにしたいものを表します。 そのためには、`@accessory` というエンティティーを作成し、受け入れ可能な次の値を設定します。

    - `ヘッドライト`
    - `ラジオ`
    - `エアコン`

    それぞれの値に対して、シノニムを指定することもできます。 例えば、`AC` や`冷房`を`エアコン`のシノニムとして指定できます。これらの 3 つの文字列はすべて同じ値として処理されます。 同じ値を指す複数の言い回しをリストすると、アプリケーションの正確性を向上させることができます。
1.  ユーザー入力を受け取ると、Conversation はインテントとエンティティーの両方を認識します。 すると、ダイアログ・フローがそれらを使用して最も適した回答を提供します。 エンティティーは、インテントに対するアプリケーションの応答が変わるという点で重要なモノについてのみ作成してください。
    定義するエンティティーに加えて、サービスには、既に定義済みですぐに利用できるシステム・エンティティーのセットが用意されています。 詳細については、[システム・エンティティーを有効にする](entities.html#enable_system_entities)を参照してください。
    {: tip}

1.  必要に応じてインテント、エンティティー、サンプルの改良を続けます。 インテントやエンティティーのセットを、完成品と見なさないでください。 [ダイアログを設計](dialog-build.html)しているときに、インテントとエンティティーを追加しなければならないことに気付く場合があります。 別のお客様からの入力を収集し、新しいサンプルの追加に利用することもできます。この反復的なプロセスにより、インテントとエンティティーを正確に認識するアプリケーションの能力を向上させることができます。