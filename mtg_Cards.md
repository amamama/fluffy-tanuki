Magic Turing Machine v5: 腐れ肺の再生術師/Rotlung Reanimator と 尖塔の大長/Chancellor of the Spires
---------------------------------------------------------------------------------------------------

カード
======

このゲームの状態は以下のとおりです:
これは四人用ゲームです．アレックス(Alex)，ボブ(Bob)，キャシー(Cathy)，デンジル(Denzil)と呼ぶことにしましょう．
アレックスはクリーチャー・トークンからなるチューリング・テープをコントロールしています．
それぞれのプレイヤーのライフは1です．

AP-NAPルールのおかげで，正しい順序でスタック上の各種トリガーが積まれ，それを得るために，ボブのターンから処理が始まります．

## 戦場
たくさんのカードが[人口進化/Artificial Evolution][Artificial Evolution]を1回，もしくはそれ以上唱えることで改竄されます．
(もしも4回以上人口進化を唱えることが心配なら，[啓発のジン/Djinn Illuminatus][Djinn Illuminatus]と[イゼットのギルド魔道士/Izzet Guildmage][Izzet Guildmage]を使ってください．)
このリストにある\*が付いている全てのクリーチャーは[不自然な淘汰/Unnatural Selection][Unnatural Selection]によって組立作業員にクリーチャー・タイプを変えられ，またそれらは二枚の[改竄][Artificial Evolution]された[ドラルヌの十字軍/Dralnu's Crusade][Dralunu's Crusade]によってイエティ(Yeti)とゾンビ(Zombie)でもあるので，これらのクリーチャーはチューリングマシンの実行によって死ななくなります．

戦場にあるカードは次のようになります:
- [カズールの大将軍/Kazuul Warlord][Kazuul Warlord]\*，アレックスのコントロール下で，テキストは「~これ~か他のイエティが１体あなたのコントロール下で戦場に出るたび、あなたはあなたがコントロールする各イエティ・クリーチャーの上に、それぞれ＋１/＋１カウンターを１個置いてもよい。」に[改竄][Artificial Evolution]されています．
- [カズールの大将軍/Kazuul Warlord][Kazuul Warlord]\*，アレックスのコントロール下で，テキストは「~これ~か他のゾンビが１体あなたのコントロール下で戦場に出るたび、あなたはあなたがコントロールする各ゾンビ・クリーチャーの上に、それぞれ＋１/＋１カウンターを１個置いてもよい。」に[改竄][Artificial Evolution]されています．
- [有毒グール/Noxious Ghoul][Noxious Ghoul]\*，ボブのコントロール下で，テキストはオリジナルの「~これ~か他のゾンビ１つが戦場に出るたび、すべてのゾンビでないクリーチャーはターン終了時まで-1/-1の修整を受ける。」のままです．
- [有毒グール/Noxious Ghoul][Noxious Ghoul]\*，ボブのコントロール下で，テキストは「~これ~か他のイエティ１つが戦場に出るたび、すべてのイエティでないクリーチャーはターン終了時まで-1/-1の修整を受ける。」に[改竄][Artificial Evolution]されています．
- [上天の閃光/AEther Flash][AEther Flash]，キャシーのコントロール下です．
- [腐れ肺の再生術師/Rotlung Reanimator][Rotlung Reanimator]\*の36体のコピー，全てアレックスのコントロール下で，全て二重に[改竄][Artificial Evolution]されていて，全て[テフェリーの呪い/Teferi's Curse][Teferi's Curse]か[不可視の外套/Cloak of Invisibility][Cloak of Invisibility]によってフェイジングを持ち，18体は[次元のほころび/Reality Ripple][Reality Ripple]によってフェイズ・アウトしています．
  最初にフェイズ・インしている18体は[Yurii Rogozhinの (2, 18) 万能チューリングマシン](http://www.sciencedirect.com/science/article/pii/S0304397596000771)の状態q1の時の状態遷移をエンコードしています:

  - Ape	類人猿(A0)が死亡するたび，Siren	サイレン(S1)を1体戦場に出す．_(訳注: S2か?．フェイズ・アウトのペガサス参照)_
  - Bat	コウモリ(B0)が死亡するたび，Elf	エルフ(E2)を1体戦場に出す．
  - Cat	猫(C0)が死亡するたび，Slith	スリス(S1)を1体戦場に出す．
  - Demon	デーモン(D0)が死亡するたび，Archer	射手(A2)を1体戦場に出す．
  - Eye	眼(E0)が死亡するたび，devil	デビル(D1)を1体戦場に出す．
  - Fish	魚(F0)が死亡するたび，Harpy	ハーピー(H2)を1体戦場に出す．
  - Giant	巨人(G0)が死亡するたび，Juggernaut	巨大戦車(J2)を1体戦場に出す．
  - Hag	ハッグ(H0)が死亡するたび，Flagbearer	旗手(F1)を1体戦場に出す．
  - Imp	インプ(I0)が死亡するたび，Faerie	フェアリー(F2)を1体戦場に出す．
  - Djinn	ジン(J0)が死亡するたび，Illusion	イリュージョン(I1)を1体戦場に出す．
  - Kavu	カヴー(K0)が死亡するたび，Leviathan	リバイアサン(L1M)を1体戦場に出す．
  - Leech	ヒル(L0)が死亡するたび，Insect	昆虫(I1M)を1体戦場に出す．
  - Mutant	ミュータント(M0)が死亡するたび，Basilisk	バジリスク(B1M)を1体戦場に出す．
  - Ninja	忍者(N0)が死亡するたび，Orc	オーク(O2)を1体戦場に出す．
  - Ox	雄牛(O0)が死亡するたび，Praetor	法務官(P1)を1体戦場に出す．
  - Pegasus	ペガサス(P0)が死亡するたび，Rhino	サイ(R2M)を1体戦場に出す．
  - Rat	ネズミ(R0)が死亡するたび，Assassin	暗殺者(HALT)を1体戦場に出す．
  - Shade	シェイド(S0)が死亡するたび，Camel	ラクダ(C2)を1体戦場に出す．

  同様に，フェイズ・アウトしている18体は，状態q2のときの状態遷移をエンコードしています:

  - Ape	類人猿(A0)が死亡するたび，Camel	ラクダ(C2)を1体戦場に出す．
  - Bat	コウモリ(B0)が死亡するたび，Camel	ラクダ(C2)を1体戦場に出す．
  - Cat	猫(C0)が死亡するたび，Bringer	運び手(B1)を1体戦場に出す．
  - Demon	デーモン(D0)が死亡するたび，Efreet	イフリート(E2)を1体戦場に出す．
  - Eye	眼(E0)が死亡するたび，Ally	同盟者(A1)を1体戦場に出す．
  - Fish	魚(F0)が死亡するたび，Knight	騎士(K2M)を1体戦場に出す．
  - Giant	巨人(G0)が死亡するたび，Harpy	ハーピー(H2)を1体戦場に出す．
  - Hag	ハッグ(H0)が死亡するたび，Golem	ゴーレム(G1)を1体戦場に出す．
  - Imp	インプ(I0)が死亡するたび，Juggernaut	巨大戦車(J2)を1体戦場に出す．
  - Djinn	ジン(J0)が死亡するたび，Golem	ゴーレム(G1)を1体戦場に出す．
  - Kavu	カヴー(K0)が死亡するたび，Frog	カエル(F2M)を1体戦場に出す．
  - Leech	ヒル(L0)が死亡するたび，Juggernaut	巨大戦車(J2)を1体戦場に出す．
  - Mutant	ミュータント(M0)が死亡するたび，Orc	オーク(O2)を1体戦場に出す．
  - Ninja	忍者(N0)が死亡するたび，Orc	オーク(O2)を1体戦場に出す．
  - Ox	雄牛(O0)が死亡するたび，Noggle	ノッグル(N1)を1体戦場に出す．
  - Pegasus	ペガサス(P0)が死亡するたび，Siren	サイレン(S2)を1体戦場に出す．
  - Rat	ネズミ(R0)が死亡するたび，Sliver	スリヴァー(S1M)を1体戦場に出す．
  - Shade	シェイド(S0)が死亡するたび，Myr	マイア(M1)を1体戦場に出す．

  最初の16体の腐れ肺の再生術師は4人が4枚ずつ通常の方法で唱え，[バザールの交易商人/Bazaar Trader][Bazaar Trader]で寄付します．
  残りの20体は[クローン/Clone][Clone]と[ヴェズーヴァの多相の戦士/Vesuvan Shapeshifter][Vesuvan Shapeshifter]で腐れ肺の再生術師をコピーしてください．
  [テフェリーの呪い/Teferi's Curse][Teferi's Curse]，[不可視の外套/Cloak of Invisibility][Cloak of Invisibility]，[エンチャント複製/Copy Enchantment][Copy Enchantment]を含むフェイジングを与えるエンチャントは，任意のプレイヤーが唱え，[バザールの交易商人/Bazaar Trader][Bazaar Trader]で寄付します．
  これらのクリーチャーとオーラをトークンにしてしまうと，フェイズ・アウトの時に消滅してしまうため，トークンにしないでください．
  _(訳注: 現在(2015/12/6)なら，[賢いなりすまし/Clever Impersonator][Clever Impersonator]でも代用できます)_
  上に述べられたすべてのクリーチャーは，[公式のクリーチャー・タイプ](http://www.wizards.com/magic/magazine/article.aspx?x=mtg/daily/arcana/1038)にあります．なぜこれらを選んだかを知りたければ，[動作原理](mtg_HowItWorks.md#CreatureTypes)を見てください．
- すべて[改竄][Artificial Evolution]されている沢山の[ドラルヌの十字軍/Dralnu's Crusade][Dralunu's Crusade]．
  これらはトークンでも大丈夫です．
  例えば，[銀白の突然変異/Argent Mutation][Argent Mutation]と[カーンの接触/Karn's Touch][Karn's Touch]を使い，その後[複製の儀式/Rite of Replication][Rite of Replication]や[瓜二つ/Spitting Image][Spitting Image]を唱えることでたくさん作ることができます．
  ドラルヌの十字軍は次のようなテキストになっています:

  - すべてのA1は，イエティ(Yeti)でもA0でもある．
  - すべてのA2は，ゾンビ(Zombie)でもA0でもある．
  - すべてのB1は，イエティ(Yeti)でもB0でもある．
  - すべてのB2は，ゾンビ(Zombie)でもB0でもある．
  - すべてのC1は，イエティ(Yeti)でもC0でもある．
  - すべてのC2は，ゾンビ(Zombie)でもC0でもある．
  - ...
  - すべてのS1は，イエティ(Yeti)でもS0でもある．
  - すべてのS2は，ゾンビ(Zombie)でもS0でもある．
  - すべてのB1Mは，反射(Reflection)でもある．
  - すべてのF2Mは，反射(Reflection)でもある．
  - すべてのI1Mは，反射(Reflection)でもある．
  - すべてのK2Mは，反射(Reflection)でもある．
  - すべてのL1Mは，反射(Reflection)でもある．
  - すべてのR2Mは，反射(Reflection)でもある．
  - すべてのS1Mは，反射(Reflection)でもある．
  - すべてのConstruct	構築物は，A0でもある．
- アレックスにエンチャントされている[死の支配の呪い/Curse of Death's Hold][Curse of Death's Hold]，2枚の[仕組まれた疫病/Engineered Plague][Engineered Plague]，これはドラルヌの十字軍によるP/T修正を元に戻すために使い，1枚はイエティ(Yeti)に，もう一枚はゾンビ(Zombie)を選びます．
- 8枚の[腐れ肺の再生術師/Rotlung Reanimator][Rotlung Reanimator]\*，全てボブのコントロール下です．
  これらはフェイズ・アウトしないので，トークンでも大丈夫です．
  これらは以下のように[改竄][Artificial Evolution]されています:

  - Basilisk	バジリスク(B1M)が死亡するたび，Blinkmoth	ちらつき蛾(B1)を1体戦場に出す．
  - F2Mが死亡するたび，F2を1体戦場に出す．
  - I1Mが死亡するたび，I1を1体戦場に出す．
  - K2Mが死亡するたび，K2を1体戦場に出す．
  - L1Mが死亡するたび，L1を1体戦場に出す．
  - R2Mが死亡するたび，R2を1体戦場に出す．
  - S1Mが死亡するたび，S1を1体戦場に出す．
  - Construct	構築物が死亡するたび，Construct	構築物を1体戦場に出す．
- [尖塔の大長/Chancellor of the Spires][Chancellor of the Spires]，アレックスがオーナーでコントロールしています．
- [タジュールの射手/Tajuru Archer][Tajuru Archer]\*，アレックスのコントロール下で，テキストは「~これ~か他の反射があなたのコントロール下で戦場に出るたび、飛行を持つクリーチャー１体を対象とする。あなたは「~これ~はそれに、あなたがコントロールする反射の数に等しい点数のダメージを与える」ことを選んでもよい。」に[改竄][Artificial Evolution]されています．
  更に，[荒廃の鎌/Blight Sickle][Blight Sickle]が装備されています．
- 少なくとも6体のReflection	反射・トークン，アレックスのコントロール下です．
- [屍滑り/Necroskitter][Necroskitter]，キャシーのコントロール下です．
- [復讐に燃えた死者/Vengeful Dead][Vengeful Dead]，アレックスのコントロール下で，テキストは「~これ~か他の暗殺者が死亡するたび、各対戦相手は１点のライフを失う。」に[改竄][Artificial Evolution]されています．
- この状況を準備するのに必要な，任意のプレイヤーによってコントロールされる土地の数に制限はありません．
  また，他のアーティファクトやエンチャントも必要ならば存在することができ，他のクリーチャーもAssembly-Worker	組立作業員である限り存在することができます．

## 他の領域
他の領域にも同様に制限があります．

**キャシーの墓地**はただ1枚の[時空の満ち干/Time and Tide][Time and Tide]しか含んではいけません．
**他の人の墓地**はインスタント・カードとソーサリー・カードが存在してはいけません．
## このターンの初め
このターンの始めに以下のことを行う必要があります:
- アレックスは[標本集め/Gather Specimens][Gather Specimens]を唱えているひつようがあります．
- 更に，そのインスタント・カードは追放されているか，墓地にあってはいけません．
  例えば，[霊都の灯籠/Reito Lantern][Reito Lantern]などで実現できます．

## じゃあ，どのようにこれは動くのでしょう?
[ここにある詳細を全部読んでください!](mtg_HowItWorks.md)

_(訳注: Last Modified: 2015/12/6)_
[Artificial Evolution]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=39923
[Djinn Illuminatus]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=340186
[Izzet Guildmage]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=340191
[Unnatural Selection]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=26776
[Dralunu's Crusade]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=26840
[Kazuul Warlord]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=203945
[Noxious Ghoul]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=205420
[AEther Flash]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=25678
[Rotlung Reanimator]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=39640
[Teferi's Curse]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=3367
[Cloak of Invisibility]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=3329
[Reality Ripple]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=3358
[Bazaar Trader]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=210776
[Clone]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=372116&part=Clone
[Vesuvan Shapeshifter]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=133739
[Copy Enchantment]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=112558
[Clever Impersonator]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=388120
[Argent Mutation]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=248735
[Karn's Touch]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=19573
[Rite of Replication]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=407070
[Spitting Image]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=181150
[Curse of Death's Hold]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=274394
[Engineered Plague]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=13097
[Chancellor of the Spires]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=248739
[Tajuru Archer]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=401745
[Blight Sickle]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=174122
[Necroskitter]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=398181
[Time and Tide]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=3653
[Gather Specimens]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=187014
[Reito Lantern]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=382764
