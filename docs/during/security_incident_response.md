---
cover: assets/img/covers/security_incident.png
description: PagerDutyでのセキュリティインシデント対応のためのアクションチェックリストです。
---
<div id="reviewed-dates">
  <span><strong>最終レビュー日:</strong> <abbr title="プロセスを最後にレビューした日付をこの文書に含めることをお勧めします。">YYYY-MM-DD</abbr></span>
  <span><strong>最終テスト日:</strong> <abbr title="プロセスを最後にテストした日付をこの文書に含めることをお勧めします。">YYYY-MM-DD</abbr></span>
</div>

!!! warning "インシデントコマンダーが必要"
     PagerDutyでの他のすべての重大インシデントと同様に、セキュリティインシデントにもインシデントコマンダーが関与し、関連する対応者にタスクを委任します。タスクはインシデントコマンダーの割り当てに従って、並行して実行される場合があります。できるだけ早い機会に `!ic page` で通知してください。

!!! question "セキュリティインシデントかどうか不明ですか？"
    とにかくプロセスを開始してください。安全策を取る方が良いです。対応が必要かどうかはインシデントコマンダーが判断します。

## チェックリスト
各項目の詳細は次のセクションで説明します。

1. 進行中の攻撃を停止する。
1. 攻撃経路を遮断する。
1. 対応チームを編成する。
1. 影響を受けたインスタンスを隔離する。
1. 攻撃のタイムラインを特定する。
1. 侵害されたデータを特定する。
1. 他のシステムへのリスクを評価する。
1. 再攻撃のリスクを評価する。
1. 追加の緩和策、モニタリングへの追加などを適用する。
1. 侵害されたシステムのフォレンジック分析を行う。
1. 内部コミュニケーションを行う。
1. 法執行機関に関与する。
1. 攻撃経路として使用された可能性のある外部関係者に連絡する。
1. 外部コミュニケーションを行う。

---

## 攻撃の緩和
できるだけ早く、必要なあらゆる手段で攻撃を停止してください。サーバーをシャットダウンしたり、ネットワーク的に隔離したり、必要であればデータセンターの電源を切ったりしてください。試すべき一般的な方法は以下のとおりです：

* プロバイダーコンソールからインスタンスをシャットダウンします（可能であれば完全な削除や終了は控えます。追ってフォレンジック調査が必要なためです）
* もしボックス（サーバー）にログインしている場合は、以下を試してみてください：
    * トラフィックを制限するためにデフォルトのiptablesルールを復元する
    * 攻撃者と思われるアクティブなセッションを `kill -9` する
    * rootパスワードを変更し、/etc/shadowを更新して他のすべてのユーザーをロックアウトする
    * `sudo shutdown now`

## 攻撃経路の遮断
攻撃を停止した後、攻撃経路となったルートを特定し、修正して再度悪用されないようにします。

* サードパーティプロバイダーが侵害されたと疑われる場合は、自分自身（および物理的に同席している他の人）のアカウントを除くすべてのアカウントを削除し、すぐにパスワードとMFAトークンをローテーションしてください。
* サービスアプリケーションが攻撃経路だったと疑われる場合は、関連するコードパスを無効にするか、サービス全体をシャットダウンしてください。

## 対応チームの編成
セキュリティインシデントの主要な対応者を特定し、全員に情報を共有し続けてください。インシデントに関連するすべての情報を安全に通信する方法を確立してください。攻撃が内部から引き起こされている可能性がある場合は、攻撃が内部から発生していないと確信するまで、インシデントの詳細（またはインシデントが発生したという事実さえも）を対応者以外には非公開にしておいてください。

* まだ行っていない場合は、インシデントコマンダーへ通知してください。彼らは通常のインシデントコマンドの役割も任命します。インシデントコマンドチームは、取られたアクションの文書化と、適切な内部関係者への通知を担当します。
* プロジェクトに無害なコードネームを付けて、チャットやドキュメントで使用できるようにしてください。誰かが耳にしてもセキュリティインシデントだと気づかないようにするためです（例：sapphire-unicorn）。
* まだ進行中でない場合は、音声通話を開始してください。
* インシデントのコードネームを使用してチャットルームを設定してください。
* すべての対応者を音声通話とチャットルームに招待してください。
    1. **常にセキュリティチームを含めましょう。**
    1. 影響を受けるサービスの代表者を含めましょう。
    1. 経営幹部と法律顧問は可能な限り早いうちに招待すべきですが、まずは運用対応者を優先してください。
* フォレンジック調査が行われるまで、対応チーム以外の誰にもインシデントについて伝えないでください。攻撃は内部から行われている可能性があります。
* すべてのメールとチャットのトピックに「Attorney Work Project」というプレフィックスを付けてください。

## 影響を受けたインスタンスの隔離
攻撃の影響を受けたインスタンスは、他のインスタンスから直ちに隔離する必要があります。できるだけ早く、システムのイメージを取得し、後のフォレンジック分析のために読み取り専用のコールドストレージに保存する必要があります。

* 影響を受けたインスタンスのIPアドレスを、他のすべてのホストの拒否リストに登録してください。
* 攻撃を停止するために、まだ行っていない場合は、インスタンスの電源を切りすぐにシャットダウンしてください。
* インスタンスに接続されているディスクのディスクイメージを取得し、オフサイトのコールドストレージの設置場所へ送信してください。これらのイメージは読み取り専用で、改ざんできないようにする必要があります。

## 攻撃のタイムラインの特定
利用可能なすべてのツールを使用して、攻撃のタイムラインと攻撃者が行った正確な行動を特定してください。

* 攻撃開始前に攻撃者がシステムに対して行った偵察活動を確認する。
* 攻撃者がシステムへのアクセスを獲得した時期を特定する。
* 攻撃者がシステム上で実行したアクション、およびその時期を洗い出す。
* 攻撃者が検出される前、および排除される前にシステムへのアクセスを持っていた期間を特定する。
* 攻撃者がデータベースで実行したクエリを特定する。
* 攻撃者が別のバックドアを通じてシステムへのアクセスをまだ持っているかどうかの特定を試みる。異常なアクティビティのログを監視するなど。

## 侵害されたデータ
ログファイル、時系列グラフ、およびその他の情報/ツールのフォレンジック分析を使用して、侵害された情報（もしあれば）の特定を試みてください。

* 攻撃中に侵害されたデータを特定してください。
    * データベースからデータが流出しましたか？
    * システム上にあり、現在侵害されたと考えられるキーは何ですか？
    * 攻撃者はシステムの他のコンポーネントを特定できましたか？（ネットワークのマッピングなど）
* 侵害された顧客データがあれば、正確に特定してください。

## リスク評価
侵害されたデータに基づいて、他のシステムへのリスクを評価してください。

* 攻撃者は別の侵入経路を見つけるのに十分な情報を持っていますか？
* ホスト上にパスワードやキーが保存されていましたか？その場合、保存方法に関わらず、それらは侵害されたと見なすべきです。
* 最初の攻撃で使用されたユーザーアカウントは、アカウントを持つ他のすべてのシステムでキーとパスワードをすべてローテーションする必要があります。

## 追加の緩和策の適用
システムの他の部分に緩和策を適用し始めてください。

* 侵害されたデータをローテーションしてください。
* 同様の侵害を通知するために、必要な新しいアラートを特定してください。
* 攻撃に関連するIPアドレスをブロックしてください。
* 侵害されたキー/認証情報を特定し、直ちにそのアクセスを取り消してください。

## フォレンジック分析
システムが安全な状態にあり、別の攻撃が行われても検出できるような十分なモニタリングが行われていると確信したら、フォレンジック分析を行う段階に移ることができます。

* 作成した読み取り専用イメージ、残っているアクセスログなどを用い、攻撃に関する詳細情報を調べてください。
* 何が起こったのか、どのように起こったのか、将来どのように防止するかを正確に特定してください。
* 攻撃に関わるすべてのIPアドレスを追跡してください。
* 攻撃者によるシステムへの再アクセスの試みがないかログを監視してください。

## 内部コミュニケーション
**委任先：** エンジニアリング組織のVPまたはディレクター

フォレンジック分析を通じて、攻撃が内部から発生したものではないと確信した場合にのみ、内部的にコミュニケーションを行ってください。

* あまり詳細に立ち入らないでください。
* タイムラインの概要を説明してください。
* 取られた緩和策について説明してください。
* 詳細が判明したら、さらに情報を提供してフォローアップしてください。

## 法執行機関/外部関係者との連携
**委任先：** エンジニアリング組織のVPまたはディレクター

攻撃の発生源を特定するために法執行機関と協力し、管理下にあるシステムが侵害されている可能性があることをシステム所有者に通知するなどの対応を行ってください。

* 地元の法執行機関に連絡してください。
* FBI（米国の場合）に連絡してください。
* 攻撃に使用されたシステムの運営者に連絡してください。彼らのシステムも侵害されている可能性があります。
* リスク評価やPR対応などの支援のためにセキュリティ企業に連絡してください。
* サイバー保険プロバイダーに連絡してください。

## 外部コミュニケーション
**委任先：** マーケティングチーム

手元のすべての情報が正確であることを確認し、イベントのタイムラインを把握し、どの情報が侵害されたか、どのように侵害されたか、そして再発しないことを確信した後にのみ、公開声明を準備して顧客に発表し、侵害された情報と彼らが取るべき措置について知らせてください。

* 発表のタイトルには日付を含めて、新たな侵害と混同されないようにしてください。
* 「私たちはセキュリティをきわめて真剣に考慮しています」とは言わないでください。読む人全員が動揺します。
* 正直に責任を受け入れ、事実を提示し、将来このようなことを防ぐための具体的な計画を説明してください。
* タイムラインについてできるだけ詳細に説明してください。
* どの情報が侵害され、それが顧客にどのように影響するかについて、できるだけ詳細に説明してください。保存すべきでなかった情報を保存していた場合は、正直に認めましょう。後から明らかになると、さらに悪い状況になります。
* 侵害の原因となった可能性のある外部関係者を名指しで非難しないでください。やりかたとして不適切です。（すでに公表されている場合を除きます。その場合は彼らが開示している情報へのリンクを提供できます）。
* 外部コミュニケーションはできるだけ早く、できればセキュリティ侵害から数日以内に発表してください。待てば待つほど、状況は悪化します。
* 可能であれば、一般公開の知らせが送信される前に顧客の内部セキュリティチームに連絡してください。

---

## インシデント中のコミュニケーション

* 他の方法よりも音声通話とSlackを優先してください。
* メールは避けてください。しかし、何らかの理由でどうしても必要な場合は、
    * メールの件名は「Attorney Work Project」とだけ記載してください。
    * メールチェーンに **@pagerduty.comドメインではない** 連絡先が **一人でも** 含まれている場合は、メールが暗号化されていることを確認してください。
* SMSを使ってインシデントに関するコミュニケーションを取らないでください。
    * 唯一の例外は、より安全なチャネルに移動するよう誰かに伝える場合です。例：「すぐにSlackに参加してください。」
* 承認を得るまで、対応チーム外の人にインシデントに関する情報を広めないでください。

---

## 追加の読み物

* [Computer Security Incident Handling Guide - コンピュータセキュリティインシデント対応ガイド](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf) (NIST)
* [Incident Handler's Handbook - インシデント対応者ハンドブック](https://www.sans.org/reading-room/whitepapers/incident/incident-handlers-handbook-33901) (SANS)
* [Responding to IT Security Incidents - ITセキュリティインシデントへの対応](https://docs.microsoft.com/en-us/previous-versions/tn-archive/cc700825(v=technet.10)) (Microsoft)
* [Defining Incident Management Processes for CSIRTs: A Work in Progress - CSIRTのためのインシデント管理プロセスの定義：進行中の作業](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=7153) (CMU)
* [Creating and Managing Computer Security Incident Handling Teams (CSIRTS) - コンピュータセキュリティインシデント対応チーム（CSIRTS）の結成と管理](https://www.first.org/conference/2008/papers/killcrece-georgia-slides.pdf) (CERT)
