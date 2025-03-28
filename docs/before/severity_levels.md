---
cover: assets/img/covers/severity_levels.png
description: インシデントは重大度や優先度によって分類されます。PagerDutyにおいては「SEV」のレベルを用いて、小さな数字の重大度であるほど緊急性の高いものであるとみなします。運用上の問題はこれらの重大度のレベルによって分類でき、一般的には重大度の高い問題であるほど、解決するためならばリスクの高いアクションを取れます。
---
インシデント対応の最初のステップは、実際に [インシデントがなにから構成されるのか](../before/what_is_an_incident.md) を定めることです。インシデントは、通常「SEV」の定義を用いた重大度（Serverity）によって分類され、数字の小さな重大度であるほど緊急性の高いものとされます。運用上の問題はこれらの重大度のレベルによって分類でき、一般的には重大度の高い問題であるほど、解決するためならばリスクの高いアクションを取れます。SEV-3よりも高い重大度のものは自動的に「重大インシデント」と考えられ、通常のインシデントよりも集中した対応が行われます。

!!! tip "常に最悪のケースを想定すること"
     インシデントの重大度の判断がつかないとき（SEV-2にすべきかSEV-1にすべきかなど）は、 **高いほうの重大度のものとして扱いましょう**。インシデント発生中は重大度を議論したり争ったりしている場合ではなく、いったんその時点で最も高い重大度を想定しておき、ポストモーテムの際にレビューすればよいのです。 

!!! question "SEV-3は重大インシデントになりうるか？"
     すべてのSEV-2は重大インシデントですが、すべての重大インシデントがSEV-2である必要はありません。たとえ低い重大度の問題であっても、協調的な対応が必要なのであれば、インシデント対応プロセスを開始しましょう。完全形のインシデント対応が必要とされるかどうか、インシデントコマンダーが判断できるでしょう。

<table class="custom-table">
  <thead>
    <tr>
      <th class="sev">重大度（Severity）</th>
      <th>内容</th>
      <th>一般的な対応</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="sev-1">SEV-1</td>
      <td>
        <p class="intent">社外に向けた公表と経営陣との連携が求められる重大な問題</p>
        <ul>
          <li>システムが致命的な状態にあり、多くの顧客へ影響している。</li>
          <li>機能が長時間にわたり深刻な影響を受け、SLAに違反している。</li>
          <li>顧客データの流出につながるセキュリティ脆弱性が明らかになっている。</li>
        </ul>
      </td>
      <td>
        <p class="response">重大インシデント対応</p>
        <ul>
          <li>Slackから <code>!ic page</code> コマンドで、インシデントコマンダーへ通知します。</li>
          <li><a href="/during/during_an_incident">インシデント発生中（During an Incident）</a> のドキュメントを参照します。</li>
          <li>内部の関係者へ知らせます。</li>
          <li>社外へ向けて公表します。</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td class="sev-2">SEV-2</td>
      <td>
        <p class="intent">システムに致命的な問題が発生し、プロダクトを利用する上で多くの顧客が影響を受けている状態</p>
        <ul>
          <li>通知のパイプラインが深刻な影響を受け、使えなくなっている。</li>
          <li>インシデント対応の主要機能（確認（Acknowledge）、解決（Resolve）など）が利用できなくなっている。</li>
          <li>Webアプリケーションが利用できないか、深刻なパフォーマンスの劣化が発生しており、大半またはすべてのユーザーが影響を受けている。</li>
          <li>重大インシデント発生時に、PagerDutyのシステムに対するモニタリングが機能していない。</li>
          <li>その他、PagerDutyの従業員がインシデント対応を要すると判断する事象が発生している。</li>
        </ul>
      </td>
      <td>
        <p class="response">重大インシデント対応</p>
        <ul>
          <li>Slackから <code>!ic page</code> コマンドで、インシデントコマンダーへ通知します。</li>
          <li><a href="/during/during_an_incident">インシデント発生中（During an Incident）</a> のドキュメントを参照します。</li>
        </ul>
    </tr>
    <tr>
      <td class="warning" colspan="3">このラインから上は、すべて「重大インシデント」と判断されます。私たちのインシデント対応プロセスは、あらゆる重大インシデントに対して開始されます。</td>
    </tr>
    <tr>
      <td class="sev-3">SEV-3</td>
      <td>
        <p class="intent">安定性の問題や顧客影響の小さな問題で、サービスオーナーへ直ちに伝える必要があるもの。</p>
        <ul>
          <li>部分的な機能の欠損で、多くの顧客には影響を与えないもの。</li>
          <li>なにも対処が行われなかった場合に、SEV-2になる可能性があるような問題。</li>
          <li>サービスの冗長性が失われた状態。（あと1つノードが落ちれば機能停止に陥る）</li>
        </ul>
      </td>
      <td>
        <p class="response">優先度高（High Urgency）でのサービスチームへの通知</p>
        <ul>
          <li>問題に対し、最も高い優先度で対応してください。</li>
          <li>対象システムの担当エンジニアと連携し、原因を突き止めましょう。</li>
          <li>もし直近のデプロイに関連したものならば、ロールバックしましょう。</li>
          <li>ステータスをモニタリングし、エスカレーションされた場合には注意を払いましょう。</li>
          <li>エスカレートする可能性があると思ったら、Slack上で言及しましょう。</li>
          <li>必要ならば、インシデント対応プロセスを開始しましょう。（<code>!ic page</code>）</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td class="sev-4">SEV-4</td>
      <td>
        <p class="intent">アクションを要する軽微な問題があるが、プロダクトを利用する上で顧客が影響を受けていない状態</p>
        <ul>
          <li>パフォーマンス問題が発生している。（遅延など）</li>
          <li>個別のホストに障害が発生している。（クラスタの中の1ノードなど）</li>
          <li>ジョブの遅延障害。（イベントや通知のパイプラインには影響しないもの）</li>
          <li>Cronジョブの失敗。（イベントや通知のパイプラインには影響しないもの）</li>
        </ul>
      </td>
      <td>
        <p class="response">優先度低（Low Urgency）でのサービスチームへの通知</p>
        <ul>
          <li>問題に対し、通常タスクよりも高い優先度で取り組みましょう。</li>
          <li>ステータスをモニタリングし、エスカレーションされた場合には注意を払いましょう。</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td class="sev-5">SEV-5</td>
      <td>
        <p class="intent">見た目の問題やバグで、顧客がプロダクトを利用する上での支障はない状態</p>
        <ul>
          <li>システムを利用する上ですぐに影響が発生するようなものではないバグがある。</li>
        </ul>
      </td>
      <td>
        <p class="response">JIRAチケットの起票</p>
        <ul>
          <li>JIRAチケットを作成し、対象システムのオーナーにアサインします。</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

!!! note "具体的にすることが大事"
    これらの重大度の定義は、PagerDutyの内部的な定義をより一般化したものです。あなた自身のドキュメンテーションにおいては、影響を受けたユーザーや顧客数など、きわめて具体的な定義にすることをお勧めします。重大度は通常、指標に基づいて判断できるように定義したいものです。
