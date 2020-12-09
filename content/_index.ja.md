# コマンドライン・インターフェイス・ガイドライン

よりよいコマンドライン・プログラムを書くための [オープンソース](https://github.com/cli-guidelines/cli-guidelines) のガイド。伝統的なUNIXの原則を元に、現代版にアップデートしています。  

## 著者 {#authors}

**Aanand Prasad** \
Engineer at Squarespace, co-creator of Docker Compose. \
[@aanandprasad](https://twitter.com/aanandprasad)

**Ben Firshman** \
Co-creator [Replicate](https://replicate.ai/), co-creator of Docker Compose. \
[@bfirsh](https://twitter.com/bfirsh)

**Carl Tashian** \
Developer Advocate at [Smallstep](https://smallstep.com/), first engineer at Zipcar, co-founder Trove. \
[tashian.com](https://tashian.com/) [@tashian](https://twitter.com/tashian)

**Eva Parish** \
Technical Writer at Squarespace, O’Reilly contributor.\
[evaparish.com](https://evaparish.com/) [@evpari](https://twitter.com/evpari)

Design by [Mark Hurrell](https://mhurrell.co.uk/). Thanks to Andreas Jansson for early contributions, and Andrew Reitz, Ashley Williams, Brendan Falk, Chester Ramey, Dj Walker-Morgan, Jacob Maine, James Coglan, Michael Dwan, and Steve Klabnik for reviewing drafts.

<iframe class="github-button" src="https://ghbtns.com/github-btn.html?user=cli-guidelines&repo=cli-guidelines&type=star&count=true&size=large" frameborder="0" scrolling="0" width="170" height="30" title="GitHub"></iframe>

[Join us on Discord](https://discord.gg/EbAW5rUCkE) if you want to discuss the guide or CLI design.


## はじめに {#foreword}

1980年代には、パーソナル・コンピュータに何かやらせようと思うなら、`C:\>` とか `~$`を前にして、何をタイプしたらいいか知っている必要があった。
ヘルプといえるのは、リング綴じの分厚いマニュアルだけ。
エラーメッセージも不明快。
頼りになる Stack Overflow もまだなかった。
だが、運よくインターネットにつなぐことさえできれば、Usenet（初期のインターネット・コミュニティで、同じような不満を抱える人で満ち溢れていた）の力を借りることはできた。
問題解決を助けてくれることもあったし、少なくとも、精神的にサポートしたり、仲間意識を持たせてくれた。

40年経って、コンピュータは誰にとっても、ずっと近づきやすいものになった。その背後でよく割愛されるのがローレベルのユーザーコントロールだ。
多くのデバイスでは、そもそもコマンドラインでアクセスする手段がない。壁で仕切った箱庭とアプリストアによってもたらされる企業の利益に反するから、というのもその一因だろう。

今ではほとんどの人がコマンドラインの何たるかを知らない。わざわざそれを使いたいと思う理由などなおさらない。
コンピュータ界のパイオニア Alan Kay は、[2017 年のインタビュー](https://www.fastcompany.com/40435064/what-alan-kay-thinks-about-the-iphone-and-technology-now) でこう言っている。「コンピューティングとは何か、ということがわかっていないから、iPhone にそれが入っていると思ったりするわけだけど、こうした勘違いは『Guitar Hero』とホンモノのギターを同じだと考えるくらい、よくない勘違いだ」

Kay にとっての「ホンモノのギター」とは、厳密に言うと CLI ではない。
彼が言うのは CLI のパワーを備えつつ、ソフトウェアをテキストファイルで書くというやり方を超えたコンピュータ・プログラミングのあり方だ。
Kay の一派の間では、何十年も続いてきたテキストをベースにした局所的な最適化から開放されるべきだ、という信念がある。

将来、どれほど変わったやり方でコンピュータをプログラムするようになるのか、想像するのは楽しい。
今もすでに、スプレッドシートはぶっちぎりで人気のあるプログラム言語だし、ノーコードの動きも急速に盛り上がっている。才能あるプログラマに集中する需要の一部をこれで代替できるのでは、と見込まれているからだ。

だが、何十年来の制約であちこち軋みがあり、いわく言い難いクセを持ちながらも、コマンドラインは今なお、もっとも _万能な_ コンピュータの一角をなしている。
カーテンを開け、実際何が起こっているのかを見きわめ、マシンと創造的にやりとりする。こうしたことが、GUIには不可能な精巧さ、深さでできるのだ。
それはほとんどどんなラップトップにも入っていて、学ぶ気持ちさえあれば、誰にでも利用できる。
対話的に使うことも、自動化することもできる。
さらに、システムの中では、他の部分ほど早くは陳腐化しない。
安定の中に創造的な価値があるのだ。
