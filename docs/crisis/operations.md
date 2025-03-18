---
cover: assets/img/crisis/cover_crisisresponse.png
description: 危機管理計画の運用化は、必要なものを、必要な方法で、必要な時に確実に手に入れるための実践的な変更から始まります。
---

## 危機管理計画の運用化

危機管理計画の運用化は、必要なものを、必要な方法で、必要な時に確実に手に入れるための実践的な変更から始まります。例えば、より広範な危機管理計画だと、危機的状況でチームが答えを探すには扱いづらすぎます。一方、プレイブック（playbooks）は、より大きな計画の焦点を絞ったバージョンであり、実行、テスト、維持が容易です。また、シナリオ駆動型で、特定のパラメータ、考慮事項、タスクを提供します。

これらの重要なリソースを作成した後、それらを一元化し、最新バージョンを追跡することは困難な場合があります。PagerDutyでは、手順書、プレイブック、ポリシー、その他の危機対応[ドキュメントリンク](https://support.pagerduty.com/docs/service-profile#remediate)をPagerDutyで定義されたサービスに追加することができ、これを容易にします。

![PagerDutyのサービスに手順書とドキュメントへのリンクが含まれていることを確認する](../assets/img/crisis/04_remediationdocs.png)

## 危機分類スキーム

真夜中に経営危機管理チームをPagerDutyのアラートで起こすのは、よほどのことがない限り避けるべきです。イベントの実際のまたは予想される重要性をランク付けする[分類スキーム](https://support.pagerduty.com/docs/incident-priority#establish-an-incident-classification-scheme)を導入することで、オオカミ少年のシナリオを避けることができます。Low（低）、Medium（中）、High（高）やLevel 1、2、3などのシンプルな尺度が効果的です。

PagerDuty内では、[インシデントの優先度](https://support.pagerduty.com/docs/incident-priority)機能を使用して、危機の「重要度レベル」を追加できます。すべての危機が最初から危機として始まるわけではないことを覚えておいてください。進行中のインシデントから発展する可能性があるため、エスカレーションのしきい値（例：HVAC無しで90分、直接連絡なしで24時間、10万ドル以上の収益がリスクにさらされているなど）を事前に決定することは、ランク付けと同様に重要です。

![組織に適した優先度を設定し定義する](../assets/img/crisis/05_priorities.png)

優先度を定義したら、インテグレーションと[インシデントワークフロー（Incident Workflow）](https://support.pagerduty.com/docs/incident-workflows)を通じて、危機対応の一部を自動化するためにPagerDutyを活用し始めることができます。Slack、Teams、Zoomとの統合でコミュニケーションチャネルを作成したり、テンプレートから内部ステータスページに自動公開したり、ステークホルダーへのアラートや[サブスクリプション](https://support.pagerduty.com/docs/communicate-with-stakeholders#add-subscribers-at-incident-creation)を自動的に開始したりできます。

![インシデントワークフローを使用して対応を効率化する](../assets/img/crisis/06_incidentworkflows.png)

危機的状況では、時間の節約がすべてです。平均対応時間（mean time to respond）を短縮し、適切な人々と連携することは、危機の発生時にチームが取れる最も重要な行動です。

## 危機宣言

危機対応チームは、通常のビジネス活動時と同じような運営を危機時にも行なっていますか？ 答えは「いいえ」であるべきです。「危機モード」での運営は、すべての行動と決定が増幅され、テンポが速く、タイムリーな決定が物を言い、問題の複雑さが増し、リスクが高くなるといった特徴があります。

危機対応チームリーダーは、思考とプロセスのモードが変更されたことを明確かつ確定的に示す必要があります。PagerDutyのアラートを通じてその変更を示すことほど良い方法はありません。インシデントの優先度（Priority）機能は、必要なステークホルダーに対して、差し支えない公開範囲でその宣言を行う簡単な方法です。対応の終了を宣言することも、通常業務または新しい業務方法への移行する上で重要であり、これは危機にあったサービスで作成された[アラートを解決](https://support.pagerduty.com/docs/alerts#resolve-alerts)するか、内部ステータスページに投稿することで行えます。

## 危機対応管理オペレーション

これまでの内容を見てきた場合、本質的に危機対応のためのPagerDutyの利用例を詳細に学んできたことになります。対応中は、危機対応チームリーダーへの連絡方法や、使用すべき会議ブリッジ、最新のプレイブックの場所について心配する必要はありません。運用面は言うまでもなく機能するはずです。PagerDutyの組み込みアラート機能に加えて、プラットフォームには700以上の[統合](https://www.pagerduty.com/integrations/#Integrations-library)があり、APIを通じてさらに多くの統合が可能なため、既存のテクノロジースタックを活用できます。

危機対応のためのサービスに[インテグレーションを追加する](https://support.pagerduty.com/docs/services-and-integrations#add-integrations-to-an-existing-service)際は、最低限、メールのインテグレーション、Slack、Google Chatなどとのインスタントメッセージングのインテグレーション、Zoom、Microsoft Teamsなどのビデオ会議ツールを含めましょう。この標準的なグループ化により、複数の方法（ウェブ、モバイル、メール、API、インスタントメッセージングなど）でアラートをトリガーし、経営危機管理チームに何かが起きていることを警告または通知すること（メール、SMS、プッシュまたは音声によるPagerDutyアラート、自動グループチャネルメッセージ、サービスへの[サブスクライバー（Subscriber）](https://support.pagerduty.com/docs/communicate-with-stakeholders#subscribe-to-a-business-service)など）が可能になります。

[PagerDuty Operations Cloud](https://www.pagerduty.com/operations-cloud/)の範囲を考えると、プラットフォームを通じて運用を行っているのは組織内のあなたのグループだけではないかもしれません。カスタマーサービス組織が技術運用組織と並んでプラットフォームを使用している可能性があります。その結果、適切なレベルのプライバシーとコンプライアンスを維持するために、アラートをトリガーし、メモを追加し、ステータスページを公開する際には、いくつかの専門的な手法を展開する必要があります。

![PagerDuty Operations Cloud](../assets/img/crisis/07_operationscloud.png)
