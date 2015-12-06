Magic: the Gatheringはチューリング完全
======================================

私達は前から[Magic: the Gathering](http://www.wizards.com/Magic/TCG)は複雑なゲームだということを知っていますが，次のことが証明されました．
なんとマジックのカードからコンピュータを構築することができるのです．

Magic Turing Machine v5: 腐れ肺の再生術師/Rotlung Reanimator と 屍滑り/Necroskitter
-----------------------------------------------------------------------------------

[概要](mtg_index.html) - [カード](mtg_Cards.html) - [動作原理](mtg_HowItWorks.html) - [難点](mtg_Difficulties.html) - [過去のバージョン](mtg_Future.html) - [今後の方向性](mtg_Future.html#Future) - [これらのページについて](mtg_About.html)

### 「チューリング完全」とは？
システムがある特定の複雑性を持っていることを示す言葉として，「[チューリング完全](https://ja.wikipedia.org/wiki/%E3%83%81%E3%83%A5%E3%83%BC%E3%83%AA%E3%83%B3%E3%82%B0%E5%AE%8C%E5%85%A8)」という言葉があります．
すべてのチューリング完全なシステムは，他のシステムをエミュレートできることが理論的に知られています．
あるシステムがチューリング完全であることを示す1つの方法は，そのシステムの中で「チューリングマシン」を作ることです．
これは，チューリング完全であることを証明する唯一の方法というわけではありませんが，理解しやすいものの1つでしょう．
このページの考察で，マジック: ザ ギャザリングのカードから[万能チューリングマシン](https://ja.wikipedia.org/wiki/%E3%83%81%E3%83%A5%E3%83%BC%E3%83%AA%E3%83%B3%E3%82%B0%E3%83%9E%E3%82%B7%E3%83%B3#.E4.B8.87.E8.83.BD.E3.83.81.E3.83.A5.E3.83.BC.E3.83.AA.E3.83.B3.E3.82.B0.E3.83.9E.E3.82.B7.E3.83.B3)を構築します．

### マジックはカードテキストを実行するのにプレイヤーが要りませんか？
通常は確かにそのとおりです．
しかし，たまに通常のゲームでも，3つか4つのイベントの連鎖がカードやルールによって引き起こされます．
以下に説明するマシンは，このアイデアをたくさんの連続した選択肢に拡張したものです．

Magic Turing Machine のアイデアは，ゲームが選択肢をプレイヤーに提示したとき以外，プレイヤーは**何も**しません．

いったんゲームの中で「マシン」が動き始めれば，1つの例外を除き，プレイヤーに選択を迫ることなく処理は続きます．
マシンの中のカードには「あなたはXをしてもよい．そうした場合，Yする．」と書かれたカードがあり，この場合，マシンは，プレイヤーが正確に1つの方法で，Xを行うことができるように準備します．
これは，プレイヤーにいつでもゲームの終了を選択できることを意味するだけです．
_(訳注: 訳せなかった．原文は It just requires the players to always choose to take the game up on any options they're offered.)_

(「してもよい」カードを取り除けるかどうかの考察を見たければ，[今後の方向性](mtg_Future.html#Future)を見てください．)

## どのように動くのですか？
よくぞ聞いてくれました！このウェブサイトで[このマシンに必要なすべてのカード](mtg_Cards.html)のリストと，[詳細な動作原理の説明](mtg_HowItWorks.html)が見られます．さらに[こんな変なものを作った奴は一体どんな奴なのか](mtg_About.html)もわかります．楽しんでね！

## ニュース
**2012年9月20日: バージョン 5に更新**
最近のインターネットからの注目をあびて，また私の注目を引いた．バージョン1から4で使われていた(2, 3) 万能チューリングマシンは非常に特殊な状況でのみ適切な万能チューリングマシンである．コンボが実行するのに失敗した無限に長い反復なしのテープを伴うものだ．
_(訳注: 訳せなかった．原文は With all the recent attention from the Internet, it's been brought to my attention again how the (2, 3) universal Turing machine used in versions 1-4 is only a proper universal Turing machine in very specific circumstances, involving an infinitely long nonrepeating section of tape, which the combo failed to deliver.)_
これは，(2, 18) 万能チューリングマシンの代わりに新しいいバージョンを作る私の努力に拍車をかけました．そして今日，成果はオンラインで公開されています．楽しんでください．

**2012年9月16日: こんにちは，インターネット**
Magic Turing Machineのオンラインでの注目が突然爆発したように見えます．
もしあなたが他の人の考えも読みたいなら，これらのリンクが参考になるでしょう．
 [Reddit](http://www.reddit.com/r/magicTCG/comments/zoojk/magic_is_apparently_turing_complete/) ([2](http://www.reddit.com/r/compsci/comments/zp7c1/magic_the_gathering_is_turing_complete/), [3](http://www.reddit.com/r/programming/comments/zqt4d/magic_the_gathering_is_turing_complete/)), [BoingBoing](http://boingboing.net/2012/09/12/magic-the-gathering.html), [Kotaku](http://kotaku.com/5942472/dark-wizards-turn-magic-card-game-into-basic-computer?post=52599392), [Metafilter](http://www.metafilter.com/119840/Magic-the-Gathering-is-Turing-complete), [Slashdot](http://games.slashdot.org/story/12/09/12/0059200/magic-the-gathering-is-turing-complete), [Mark Rosewater's blog](http://markrosewater.tumblr.com/post/31451269236/did-you-see-the-post-that-demonstrated-that-magic-is), or [the Wizards of the Coast forums](http://community.wizards.com/go/thread/view/75842/29377357/Magic_is_Turing_Complete_(the_Turing_Machine_combo)).

 ---
 _(訳注: Last modified: 2015/12/1)_
