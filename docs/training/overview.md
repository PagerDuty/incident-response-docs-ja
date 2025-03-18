---
cover: assets/img/covers/training_overview.png
title: トレーニング概要
description: PagerDutyの重大なインシデント対応プロセスについて学ぶことは、PagerDutyでオンコールエンジニアとして効果的に活動するための重要な部分です。このセクションでは、インシデント対応に関わる様々な役割のトレーニング資料と、政府機関からの追加情報やトレーニング資料について説明します。
---
PagerDutyの重大なインシデント対応プロセスについて学ぶことは、PagerDutyでオンコールエンジニアとして効果的に活動するための重要な部分です。このセクションでは、インシデント対応に関わる様々な役割のトレーニング資料と、政府機関からの追加情報やトレーニング資料について説明します。

## トレーニングガイド
トレーニングガイドは役割ごとに分かれていますが、自分が属していない役割のトレーニングガイドも読むことをお勧めします。それによって、重大なインシデント中にそれらの人々がどのように行動するかについての良い洞察を得ることができます。

* [インシデントコマンダートレーニング](../training/incident_commander.md) - 「IC」は重大なインシデントを解決に導く人物です。他の全員を指示する人です。
* [副指揮官トレーニング](../training/deputy.md) - 副指揮官はインシデントコマンダーをサポートし、必要に応じて代わりを務めることができる人物です。
* [書記官トレーニング](../training/scribe.md) - これはインシデント中に書記官として活動する個人向けです。
* [SME / 対応者トレーニング](../training/subject_matter_expert.md) - これはPagerDutyの任意のチームでオンコールをしている全ての人に関連します。
* [カスタマーリエゾントレーニング](../training/customer_liaison.md) - これは公に私たちを代表し、顧客と対話する個人向けです。
* [インターナルリエゾントレーニング](../training/internal_liaison.md) - これはインシデント中に社内チームと協力するよう呼ばれる可能性のある人に関連します。

## トレーニングコース
また、トレーニングコースのスライドとビデオもいくつか公開しています。元々はPagerDuty内部でスタッフをトレーニングするために使用されていましたが、その後、より広い視聴者向けに適応させたので、あなた自身の組織でも利用することができます。

* [インシデント対応トレーニングコース](../training/courses/incident_response.md) - インシデント対応とインシデントコマンダーの役割に関する入門コース。

## インシデント例
この録音された通話は、[2017年1月](https://status.pagerduty.com/incidents/510k1bnvwv6g)にPagerDutyで実際に発生した重大なインシデントの再現です。簡潔さとプライバシーの観点からいくつかの詳細が変更されていますが、インシデント自体は大部分そのまま残っています。録音の詳細については、[PagerDutyのブログ記事](https://www.pagerduty.com/blog/incident-response-reenactment/)をお読みください。

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/yoY_pDxc0TA?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## 国家インシデント管理システム（NIMS）
私たちのインシデント対応プロセスは、[米国国家インシデント管理システム（NIMS）](https://www.fema.gov/national-incident-management-system)を緩やかに基にしています。これは以下のように説明されています：

  _脅威や危険に関わるインシデント（原因、規模、場所、複雑さを問わず）を管理するために、あらゆるレベルの政府機関、非政府組織、民間セクターがシームレスに協力するための体系的、積極的なアプローチであり、生命、財産、環境への害を減らすことを目的としています。_

これがITオペレーション環境に適用できるとは最初は思えないかもしれませんが、これらの状況での重大なインシデントから学んだ多くの教訓が私たちの業界にも直接適用できることがわかりました。原則は同じであり、多くの異なる環境にまたがっています。

[![NIMS](../assets/img/thumbnails/nims_core.png)](https://www.fema.gov/pdf/emergency/nims/NIMS_core.pdf) [![NIMS Training](../assets/img/thumbnails/nims_training.png)](https://www.fema.gov/pdf/emergency/nims/nims_training_program.pdf)

NIMSについてもっと学びたい場合は、[ICS-100](https://training.fema.gov/is/courseoverview.aspx?code=IS-100.b)と[ICS-700](https://training.fema.gov/is/courseoverview.aspx?code=IS-700.a)のオンライントレーニングコースをお勧めします。これらはNIMSとインシデントコマンドシステムについて説明しています（トレーニング後にオンライン試験を受けて、FEMAから証明書を取得することもできます）。また、NIMSに関する[FEMAからの追加のトレーニング資料とコース](https://training.fema.gov/nims/)も豊富にあり、ぜひ見てみることをお勧めします。

米国を拠点としており、コミュニティでより積極的なインシデント対応の役割を担うことに興味がある場合は、地域の[CERTプログラム](https://www.ready.gov/cert)（コミュニティ緊急対応チーム）を調査することをお勧めします。多くの都市がCERTトレーニングを提供しており、その後、コミュニティ内でCERT貢献者としてボランティアをすることができます。災害対応の実世界の経験を得る機会であるだけでなく、学んだスキルは日常生活にも適用できます。

また、[追加の読み物](../resources/reading.md)のページもご覧ください。

## 世界中のインシデント対応
NIMSは米国のインシデント対応フレームワークですが、多くの国々が独自の類似したフレームワークを持っています。一部は米国のシステムに基づいていますが、多くは独自に開発されました。世界中の国々で使用されている方法やフレームワークを調査することで、さらに多くの追加情報を学ぶことができます。

「[比較緊急管理：世界中の災害政策、組織、イニシアチブの理解](https://training.fema.gov/hiedu/aemrc/booksdownload/compemmgmtbookproject/)」という本（[FEMAのウェブサイト](https://training.fema.gov/hiedu/aemrc/)から入手可能）は、約30の異なる国々で使用されているシステムを比較しており、世界中で使用されている緊急管理フレームワークに関する情報の素晴らしいコレクションです。

以下は、PagerDutyでの私たち自身のプロセスを適応し改善するために、より詳細に調査したシステムのいくつかです。

### イギリス

イギリスの緊急サービスは、主要な作戦のために[**ゴールド-シルバー-ブロンズコマンド構造**](https://en.wikipedia.org/wiki/Gold%E2%80%93silver%E2%80%93bronze_command_structure)と呼ばれるコマンド階層を使用しています。このフレームワークには、戦略的（ゴールド）、戦術的（シルバー）、運用的（ブロンズ）コマンド決定を担当する3つのレベルが含まれています。

もっと学びたい場合は、以下の有用な読み物があります：

* [UK.GOV - 緊急対応と回復](https://www.gov.uk/guidance/emergency-response-and-recovery)。
* [UK.GOV - インシデントコマンド - 第3版（2008）](https://www.gov.uk/government/publications/fire-and-rescue-manual-volume-1-incident-command)。
* [UK Home Office - 重大インシデント管理](https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/735103/critical-incident-management-v12.0ext.pdf)（PDF）。


### ニュージーランド

ニュージーランドのシステムは[**調整インシデント管理システム（CIMS）**](https://en.wikipedia.org/wiki/Coordinated_Incident_Management_System)と呼ばれ、米国で使用されているインシデントコマンドシステムに基づいています。CIMSの特に気に入った点の一つは、共通の用語に焦点を当てていることです。これはインシデント中の混乱を防ぎ、より迅速で効果的な対応を可能にします。一部の用語はICSから変更されていますが（例えば、管理機能を説明するために「コマンド」の代わりに「コントロール」）、それでも馴染みがあるはずです。

もっと学びたい場合は、以下の有用な読み物があります：

* [民間防衛・緊急管理省 - ニュージーランド調整インシデント管理システム（CIMS）](https://www.civildefence.govt.nz/resources/coordinated-incident-management-system-cims-third-edition/)（[PDF](https://www.civildefence.govt.nz/assets/Uploads/CIMS-3rd-edition-FINAL-Aug-2019.pdf)）。
* [Devereux-Blum Training & Development - 緊急管理トレーニング](https://www.emergencymanagement.co.nz/)

### オーストラリア

オーストラリアは[**オーストラレーシア機関間インシデント管理システム（AIIMS）**](https://en.wikipedia.org/wiki/Australasian_Inter-Service_Incident_Management_System)と呼ばれるシステムを使用しています。これは米国で使用されているNIMSフレームワークの派生物です。ICSに基づいていますが、AIIMSは他のフレームワークよりも_管理範囲_に大きな焦点を当てています。ニュージーランドのシステムと同様に、使用されている用語にはいくつかの違いがあります（例えば、「インシデントコマンダー」の代わりに「インシデントコントローラー」）が、ICSを知っている人にはまだ馴染みがあるはずです。

もっと学びたい場合は、以下の有用な読み物があります：

* [オーストラレーシア機関間インシデント管理システム、第3版](https://training.fema.gov/hiedu/docs/cem/comparative%20em%20-%20session%2021%20-%20handout%2021-1%20aiims%20manual.pdf)（PDF）。
* [オーストラリアのインシデント管理ハンドブック](https://knowledge.aidr.org.au/resources/handbook-14-incident-management-in-australia/)

### カナダ

カナダは独自の[**インシデントコマンドシステム**](https://www.icscanada.ca/images/upload/ICS%20OPS%20Description2012.pdf)（PDF）を使用しています。その標準は[ICS Canada](https://www.icscanada.ca/en/home.html)と呼ばれる組織のネットワークによって維持されています。彼らのウェブサイトには、州に応じてカナダでのローカルトレーニングコースを見つける方法に関する情報のコレクションがあります。

もっと学びたい場合は、以下の有用な読み物があります：

* [ICSCanada - I-100 インシデントコマンドシステム入門](https://www.svffa.ca/s/ICS100-Self-Paced-Student-Workbook_2016.pdf)（PDF）。
* [カナダICSフォーム](https://www.icscanada.ca/en/Forms.html) - _ダウンロードして独自のインシデントで使用できる標準ICSフォーム（[FEMAには米国の同等品があります](https://training.fema.gov/icsresource/icsforms.aspx)）。_
