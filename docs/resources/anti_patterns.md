cover: assets/img/covers/anti-patterns.png
description: これらは、うまく機能しないと判明したプロセスです。過去に試してみて後悔したか、十分に検討した上で最終的に却下したものです。私たちは、同じ過ちを繰り返さないようにするため、また後になって決定がなぜ行われたのか疑問に思わないようにするために、これらを文書化したいと考えています。
---
!!! warning "プロセスのアンチパターン"
    これらは、うまく機能しないと判明したプロセスです。過去に試してみて後悔したか、十分に検討した上で最終的に却下したものです。私たちは、同じ過ちを繰り返さないようにするため、また後になって決定がなぜ行われたのか疑問に思わないようにするために、これらを文書化したいと考えています。このリストに特定の順序はありません。

## 全員を会議に参加させる

信じられないかもしれませんが、PagerDutyでは以前、SEV-2インシデントが発生すると、すべてのエンジニアに連絡していました。SEV-2が午前3時に発生した場合、エンジニア部門全体に午前3時に連絡することになっていました。このような方法を取った理由はいくつかあります。

1. 会社が小規模だった頃は、エンジニアの数も少なかったため、このプロセスはうまく機能していました。実際に全エンジニアが会議に必要だったからです。
1. インシデントをトリアージしてから追加の人員に連絡するのではなく、最初から全員が会議に参加していれば、より迅速な対応ができるという考えでした。

エンジニア部門が成長するにつれて、このやり方はまったくスケールせず、問題がすぐに明らかになりました。

1. 会議に参加している人の大半は何もすることがありませんでした。彼らは理由もなく起こされていたのです。
1. 人に連絡することにはコスト影響があります。従業員の健康面でも、財政面でも。エンジニア部門全体を午前3時に起こすということは、翌日は部門全体で生産的なことが何もできないということです。
1. オンコールではない人にも連絡が行くことになります。

インシデント対応では**効果的な管理範囲**を維持することが重要です。[インシデントコマンダー]()に直接報告する人が7〜8人以上いると、状況はすぐに手に負えなくなる可能性があります。現在では、チーム全体ではなく、特定のサービスに対してオンコールしているエンジニアにのみ連絡します。さらに対応者が必要な場合は、[インターナルリエゾン]()によって対応に参加するよう動員されます。10回中9回は追加の対応者は必要ないため、エンジニア部門の残りのメンバーは邪魔されることなく休息を取ることができます。これにより、エンジニア部門はより幸せになり、対応プロセスも合理化されます。

## 全員に会議に残ることを強制する

当初の考えでは、対応会議に動員された場合、最後まで残る必要があるとされていました。一度必要とされた場合、インシデントが解決するまでに再び必要になる可能性が高いと考えられていたからです。しかし、実際にはそのようなことはほとんどないとわかりました。通常、対応者は特定のシステムを調査したり、特定のアクションを実行したりするために動員され、その後は彼らに必要なことは何もありません。何もすることがなく、睡眠に戻れたはずの人々で会議が満たされていました。これはまた、個人が会議に残らなければならないというプレッシャーを感じる「ヒーロー」的な考え方を助長することもあります。

現在では、もう必要ない場合は会議から退出するよう依頼しています。インシデントコマンダーが影響を受けているシステムを確認した後、他のシステムの担当者には会議から退出して休息を取るよう伝えます。本当に必要になれば、再び動員することもできます。ほとんどの場合、彼らが再び必要になることはないので、99%のケースに最適化しています。

## あまりにも頻繁なステータスアップデート

経営陣は何が起きているのかを知る必要があり、常に最新情報を得るために5分ごとにステータスアップデートを提供してほしいと思っています。問題は、インシデントを解決するよりも、ステータスアップデートの提供に時間を費やすことになってしまうことです。

大きなインシデント中は、20〜30分毎のステータスアップデート提供が、通常うまく機能するペースであることがわかりました。これにより、単にアップデートのためのアップデートを提供するのではなく、実際に有用な情報が含まれる可能性が高くなります。もちろん、本当に新しい情報を共有する必要がある場合は、より頻繁にアップデートを提供することもできますが、それが要件であるべきではありません。インシデントの修正にできるだけ多くの時間を費やしたいのと同時に、関係者へ最新情報を提供することも確実にしたいものです。これは間違えやすい繊細なバランスです。

## 沈黙＝進捗がないと思い込む

インシデント会議で沈黙が発生すると、何も行われていないのではないかと思い込むことがよくありますが、実際にはそうではないことがほとんどです。会議に参加する際は、会話のない状態が許容され、合理的であることを認識してください。沈黙は通常、全員が話したり更新を提供したりするのではなく、問題の解決に取り組んでいることを意味します。私たちは「話し続けなければ誰かが解雇されてしまう」ゲームをしているわけではありません。インシデントコマンダーが会議で最も多く話すべき人です。彼らは通常、適切であれば沈黙の代わりに状況アップデートを行いますが、組織内の他のメンバーは、会議での沈黙が悪いことではなく、進捗が停滞していることを意味するものではないことを事前に認識しておく必要があります。皆がこれを事前に認識していれば、インシデント会議中の気まずい会話を防ぎ、最終的にはインシデントの解決から注意をそらすことを防ぐことができます。

## インシデント会議中に重大度について議論する

PagerDutyの過去の多くのインシデント会議の冒頭では、本当にSEV-2の状況なのか、それともインシデント会議なしで対処できる小さな問題なのかについての議論が行われていました。この議論は通常かなりの時間を要し、全員が意見を述べたがりました。問題は、この議論をしている間にもインシデントは裏で進行しており、議論が終わる頃にはSEV-1になってしまい、重大度について10分を無駄にしてしまったことです。

現在は、ルールがあります：**インシデント会議中にインシデントの重大度について議論しない**、常により高い重大度を想定し、それに応じて対処します。つまり、SEV-2かSEV-3か確信が持てない場合は、SEV-2として扱い、先に進みます。すでにインシデント対応の歯車を回し対応者に連絡している以上、結果的にSEV-3だったとしてもプロセスを継続し、少なくとも練習として扱うのが良いでしょう。

## 他の対応者へのエスカレーションをためらう

午前3時にインシデントに対応していたときに、SME（対象分野の専門家）が問題のデバッグに行き詰まったものの、時間帯を考慮してチームの他のメンバーを巻き込むことをためらうケースがありました。これにより、インシデントが必要以上に長引くことになりました。

**「エスカレーションをためらわないこと」**が現在の私たちのマントラの一つです。問題に行き詰まったら、たとえ午前3時であっても、事態を解決するためにより知識のある人に連絡することをためらわないでください。ただし全員に連絡するのはやりすぎで、前述のアンチパターンに陥ります。しかし助けが必要な場合は、誰かに連絡してはだめだと感じるべきではありません。

## インシデント会議中にプロセスとポリシーの決定について議論する

対応者がインシデント対応のポリシーやプロセスに同意しないことがあります。これがインシデント会議中に議論を引き起こし、全員のプロセスを脱線させ、根本的なインシデントが長引いて対応を妨げることがあります。プロセスに不満を持ち、変更を望むこと自体は全く問題ありません（実際、これは私たちが奨励していることであり、プロセスを反復的に改善することができます）。しかし、インシデント中はその議論をする時ではありません。

重大度と同様に、**ポリシーとプロセスはインシデント中に議論すべきではありません**。インシデント中は現在のプロセスに従うべきであり、懸念事項はポストモーテム中か、インシデント対応プロセスを管理するチームに直接提起すべきです。

## ポストモーテムとフォローアップ活動を怠る

インシデントが解決したら、ポストモーテムを行わないという誘惑に駆られることがあります。原因がよく知られていると感じたり、価値がないと感じたりするかもしれません。この罠に陥らないでください！ ポストモーテムは常に価値があります。インシデントに対応するために人々が動員され、それにはコストがかかったのです。将来そのコストを避けるために、なぜそれが起こったのかを確実に理解したいと思います。

インシデント後にポストモーテムを怠るという誤りを避けましょう。ポストモーテムがなければ、何が正しく行われているか、どこを改善できるか、そして最も重要なことに、次回同じ間違いを避ける方法を認識できません。適切に設計された、非難のないポストモーテムにより、チームは継続的に学習し、インフラストラクチャとインシデント対応プロセスを反復的に改善する方法として機能します。

対応者を動員して「本当の」インシデントではないと判断した場合でも、ポストモーテムを実施すべきです。なぜなら、次回も対応者を動員して時間を無駄にすることになるからです。インシデント対応が必要ではなかったかもしれない場合に、なぜプロセスが開始されたのかを調査し、その問題を修正してください。

## 目の前の問題に過度に集中する

インシデントの対応者として、通常は目の前の特定のタスクに集中します。インシデントコマンダーは一般的に何が起きているかの全体像を把握している人です。SMEが、インシデントコマンダーからの指示を聞かずに同じ問題を繰り返し持ち出し、自分のシステム上の特定の問題に対する視野狭窄に陥る傾向があります。

インシデントコマンダーからの指示は常に従うべきです。彼らは通常、何が起きているかについてより全体的なコンテキストを把握しています。目の前の問題に過度に集中し、プロセスを脱線させるような罠に陥らないようにしてください。私たちはインシデントの症状ではなく、原因を治療したいのです。

## ポリシーとプロセスの変更に抵抗する

安定したプロセスが整い、インシデントが解決されると、そのプロセスを変更することに対して多くの躊躇や抵抗が生じることがあります。「壊れていないなら修正するな」などの考えです。会社が成長するにつれて、対応も変化する必要があります。古いプロセスや慣行を長く維持することは、今後のインシデント対応を妨げる可能性があります。もちろん、無謀にはならないようにしてください。しかし、**短期的には物事を遅くするかもしれないが、長期的には物事を速くする変更を恐れないでください**。これらは最も難しい変更であると同時に、多くの場合、最も価値のある変更です。

## 複数の役割を引き受けようとする

過去のPagerDutyのインシデントでは、インシデントコマンダーがSMEの役割を引き受け、自分で問題を解決しようとした例がありました。これは通常、インシデントコマンダーが普段エンジニアである場合に発生します。彼らは自分のよく知っているシステムに原因があり、修正するための必要な知識を持っているインシデントに遭遇します。インシデントを迅速に解決したいと思い、インシデントコマンダーは問題の解決を試み始めます。運が良ければインシデントが解決することもありますが、ほとんどの場合、すぐに見える問題がインシデントの根本的な原因であるとは限りません。それが明らかになる頃には、他のシステムに注意を払わず、目の前の一つの問題だけに集中しているインシデントコマンダーがいることになります。これは事実上、インシデントコマンダーがいないのと同等で、彼らは見えている問題の修正にかかりっきりです。必然的に、問題は予想よりもはるかに大きくなり、対応は完全に脱線してしまいます。

**インシデントコマンダーであると同時に別の役割を引き受けることはできません**。SMEとして参加したい場合、インシデントコマンダーであることは難しい場合がありますが、インシデントコマンダーの役割を放棄する誘惑に抵抗しなければなりません。本当に問題を解決できる唯一の人物である場合は、別のインシデントコマンダーに引き継ぎ、SMEの役割を引き受けるべきです。これにより、専任のインシデントコマンダーが対応プロセスを軌道に乗せ続けることができます。

インシデントコマンダーの仕事には、現在のアクションがインシデントを解決しない場合のバックアッププランの準備も含まれることを忘れないでください。特定の問題の修正にSMEとして行動している場合、バックアッププランを考慮していません。

## ヒーローになろうとする

SMEとして行動している場合、すべての問題を自分で解決しようとする誘惑に駆られることがあります。出てくるすべてのリクエストに飛びつき、自分が対処すると言いたくなります。あなたはすべての問題を解決する不可欠な存在になるでしょう。意図は高潔ですが、効率的な結果につながることはほとんどありません。インシデント中はできるだけマルチタスクを避け、一度に一つの問題に集中するのがよいです。**すべてを自分で解決しようとしないでください**。あなたの専門分野に関する複数のリクエストが出てきた場合、それらを他の専門家に委任し、必要であればバックアップの対応者に連絡してください。

同様に、別のSMEにタスクが割り当てられている場合、最初に彼らと相談せずに彼らの代わりにタスクを実行しないでください。あなたは助けようとしていますが、結局は二人の人が同じ問題に取り組み、予期せぬ方法で互いに干渉する可能性があるため、対応を妨げることになります。

## ポリシー変更を対応者に周知しない

過去には、内部文書（つまりこれ）を更新するだけでポリシーとプロセスの変更を行い、インシデント前に全員が文書を読むと想定するという罠に陥りました。もちろん、それは決して起こりません。

**ポリシーの変更は、インシデント中に驚きがないように、事前に適切に対応者に周知する必要があります**。これはメールやチャットルームへの更新の形で行うことができますが、大きなポリシー変更が対応者にとって驚きであってはなりません。

## インシデントコマンダーに深い技術的知識を要求する

これは、インシデント対応の初期段階で陥った罠です。新しいインシデントコマンダーに対していくつかの強い技術的要件を設け、深い技術的専門知識を持つインシデントコマンダーのみを目指していました。その意図は、彼らが問題を非常に迅速に診断できるようにするためでした。効果的なオンコール交代を維持するために多数のインシデントコマンダーが必要であることが明らかになったとき、私たちは潜在的なインシデントコマンダー候補のプールを人為的に制限していたことにすぐに気づきました。

**インシデントコマンダーは組織全体から募ることができ、技術的な専門家である必要はありません**。インシデントコマンダーは対応を調整するだけなので、役割を果たすためにシステムの深い技術的知識は必要ありません。深い技術的知識を必要とする人たちはSMEです。インシデントコマンダーはシステムの動作に関する高レベルの知識だけが必要です。データがどこから流れ込み、システムがそれをどのように使用し、データがどこに流れ出るか。技術的な詳細はSMEに任せ、インシデントコマンダーは関連する質問をします。

インシデントコマンダーに対する強い技術的要件を緩和することで、インシデントコマンダーのプールを劇的に増やし、対応の質と効率の高いレベルを維持し、オンコール業務への共感を会社のより大きな部分へ広げることができました。
