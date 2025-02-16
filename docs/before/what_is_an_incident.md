---
cover: assets/img/covers/incident.png
description: Before defining an incident response process, we should first define what an incident (and a major incident) is, along with how we should trigger the response for such incidents.
---
インシデント対応プロセスを定義する前に、インシデント（そして重大インシデント）とは何かを定義する必要があります。

## インシデントとは何か？
顧客のサービス利用に顕著な影響を及ぼす、計画外のサービスの中断や低下を指します。

## 重大インシデントとは何か？
複数のチームによる協調の取れた対応を必要とするインシデントを指します。

## インシデント対応とは何か？
インシデントへ対処し管理を行う、組織的な取り組みです。目的はインシデントを解決するのみならず、損害を最小限に留めながら回復にかかる時間とコストを減らせる形で状況に対処することです。

## インシデント対応プロセスの契機となるものは何か？

私たちのインシデント対応プロセスは、あらゆる重大インシデントにおいて開始されます。これにより、効果的な対応を行い早期解決を目指すためのフレームワークがもたらされます。インシデント対応プロセスは2つの方法でトリガーでき、1つは自動化されたモニタリングやアラート、もう1つは手動による人手のアクションです。

### 自動化されたモニタリング

システム全体において、私たちはさまざまな指標をモニタリングし、インシデントを解決する上で、統率の取れた人手の対処をシステムに対して行う必要があるかどうかを判断します。どの指標をモニタリングし、何のためにモニタリングするかを決めるためには、私たちは次のような問いかけを行います。もしこれらのいずれかに対する回答が "No" なのであれば、インシデント対応プロセスをトリガーすべきです。

1. 顧客は、すべてのプラットフォーム上で、PagerDutyによって提供されたすべてのインシデント対応機能を利用できるか？
    * 例：サポートされているすべての方法で、インシデントを確認し、再アサインし、解決することができるか？
1. 顧客は、SLA内で通知を受け取っているか？

### 人によるエスカレーション
Automatic monitoring is only part of the process. We may have parts of our functionality which lack the necessary monitoring. It's important to still be able to trigger a coordinated incident response in those cases. For example, if our Support team starts to receive requests that indicate a system issue, they need to have the power to trigger our response. Any PagerDuty employee has the ability to trigger our incident response process at any time.

We trigger on any unplanned disruption or degradation of service to which any PagerDuty employee deems necessary of requiring coordinated incident response.

!!! question "Is a response required?"
    If you are unsure of whether response is required, trigger our incident response process. All you need to do to start the process is page an Incident Commander in Slack with `!ic page`.

## インシデントの深刻度
Our [severity definitions](../before/severity_levels.md) determine how severe we _think_ an incident is based on some predefined guidelines. The intent is to guide responders on the type of response they can provide. For example, the higher the severity, the riskier the decisions you can take to return the system to normal.

Severities are useful to quickly determine whether something requires a more complex response, or whether it requires a coordinated response at all. However, they are not a black and white definition of what constitutes a major incident. If something is not covered by our severity definitions - but you think it requires incident response - then it requires incident response. We only need to know one thing: Is this a major incident? The severity level can be determined later and isn't a requirement of triggering our response process.

## メンタリティの転換
One of the more important concepts of our incident response process is the mentality shift that needs to be made during an incident. We typically call this the "Peacetime vs Wartime" mentality shift. The idea is that the decision making process changes when you are in an incident situation, and you are able to take riskier actions than you would normally consider during day-to-day operations. It can be hard for responders to grasp this concept, and your incident response process can be held up by responders who stick to the peacetime way of thinking to avoid proceeding with a potentially risky action. You can read more about peacetime vs wartime in the [Responder Training Guide](../training/subject_matter_expert.md#wartime-vs-peacetime).

!!!info "Normal vs Emergency"
    Some people don't like the "Peacetime vs Wartime" analogy, in which case you can use any other terms you feel appropriate. "Normal vs Emergency" is a common choice, but you could equally use "OK vs Not OK". It's not terribly important what name you give it, the important part is to make the mentality shift.
