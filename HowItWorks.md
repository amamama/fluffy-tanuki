Magic Turing Machine v5: 腐れ肺の再生術師/Rotlung Reanimator と 尖塔の大長/Chancellor of the Spires
---------------------------------------------------------------------------------------------------

動作原理
========
私はあなたが[チューリングマシン](https://ja.wikipedia.org/wiki/%E3%83%81%E3%83%A5%E3%83%BC%E3%83%AA%E3%83%B3%E3%82%B0%E3%83%9E%E3%82%B7%E3%83%B3)の基本的な考え方に精通していると仮定しています．
チューリングマシンをマジックの世界で組み立てるためにいくつかのパーツに分けます:
いくつかの異なる「色」のセルを格納する，二方向に伸びるテープ，現在のセルの色を読み，新しい色を書いて必要なら自身の状態を変えるヘッド，そして両方向に伸びる「仮想」無限テープ．

戦場とその他の領域にある全てのカードのリストは[カード](Cards.html)にあります．
このページでは，完全にそれを繰り返すことはしませんが， *なぜ* それらのカードが必要なのか説明します．

## チューリングテープ
テープのモデルは以下のようなものです．
アレックスがコントロールしている一連のゾンビ・トークンは，現在のヘッドの右側のテープを表します．
ヘッドの1つ右のクリーチャーはタフネスが1で，その右のクリーチャーはタフネスが2で…と続きます．
同じようにアレックスがコントロールしている一連のイエティ・トークンは，ヘッドの左側のテープを表します．

それぞれのトークンは2つの別のクリーチャー・タイプを持ち，テープ上の対応する空間がどの「色」なのかを指し示します．
簡単のために，この考察のいくつかの場面では，実際のクリーチャー・タイプを書く代わりに，A1のようなコードによってクリーチャー・タイプを参照します．
クリーチャー・タイプは以下のように割り当てられます:
(これらのタイプは全て[公式のクリーチャー・タイプ・リスト](http://www.wizards.com/magic/magazine/article.aspx?x=mtg/daily/arcana/1038)から取りました．
 可能であれば，「左(Left)」のクリーチャー・タイプが「L」を含むように，「右(Right)」のクリーチャー・タイプが「R」を含むように，「通常(common)」のクリーチャー・タイプはどちらも含まないようにしました．
 _(訳注: 日本語だとわかりづらいので変更しようと思ったが[サブタイプ一覧](http://mjmj.info/data/Subtypes.txt)を見るにわかりやすくはできなさそうだ．できるなら変更したい)_)

|	色番号	|	「通常」のタイプ	|	「左」のクリーチャー・タイプ	(Yeti	イエティを含む)	|	「右」のクリーチャー・タイプ	(Zombie	ゾンビを含む)	|	メッセンジャー・タイプと方向_(訳注: 訳に自信なし)_	|
|:----------|:----------------------|:----------------------------------|:----------------------------------|:--------------------------|
|1			|Ape	類人猿 (A0)		|Ally	同盟者 (A1)					|Archer	射手 (A2)					|							|
|2			|Bat	コウモリ (B0)	|Blinkmoth	ちらつき蛾 (B1)			|Bringer	運び手 (B2)				|Basilisk	バジリスク (B1M)	|
|3			|Cat	猫 (C0)			|Camel	ラクダ (C1)					|Carrier	キャリアー (C2)			|							|
|4			|Demon	デーモン (D0)	|devil	デビル (D1)					|Dragon	ドラゴン (D2)				|							|
|5			|Eye	眼 (E0)			|Elf	エルフ (E1)					|Efreet	イフリート (E2)				|							|
|6			|Fish	魚 (F0)			|Flagbearer	旗手 (F1)				|Faerie	フェアリー (F2)				|Frog	カエル (F2M)		|
|7			|Giant	巨人 (G0)		|Golem	ゴーレム (G1)				|Gorgon	ゴルゴン (G2)				|							|
|8			|Hag	ハッグ (H0)		|Hellion	ヘリオン (H1)			|Harpy	ハーピー (H2)				|							|
|9			|Imp	インプ (I0)		|Illusion	イリュージョン (I1)		|Incarnation	インカーネーション (I2)	|Insect	昆虫 (I1M)			|
|10			|Djinn	ジン (J0)		|Jellyfish	クラゲ (J1)				|Juggernaut	巨大戦車 (J2)			|							|
|11			|Kavu	カヴー (K0)		|Kobold	コボルド (K1)				|Kirin	麒麟 (K2)					|Knight	騎士 (K2M)			|
|12			|Leech	ヒル (L0)		|Licid	リシド (L1)					|Lizard	トカゲ (L2)					|Leviathan	リバイアサン (L1M)	|
|13			|Mutant	ミュータント (M0)	|Moonfolk	ムーンフォーク (M1)		|Myr	マイア (M2)					|							|
|14			|Ninja	忍者 (N0)		|Noggle	ノッグル (N1)				|Nightmare	ナイトメア (N2)			|							|
|15			|Ox	雄牛 (O0)			|Ooze	ウーズ (O1)					|Orc	オーク (O2)					|							|
|16			|Pegasus	ペガサス (P0)	|Plant	植物 (P1)					|Praetor	法務官 (P2)				|							|
|17			|Rat	ネズミ (R0)		|Rebel	レベル (R1)					|Rigger	装具工 (R2)					|Rhino	サイ (R2M)			|
|18			|Shade	シェイド (S0)	|Slith	スリス (S1)					|Siren	サイレン (S2)				|Sliver	スリヴァー (S1M)		|

したがって，例えば，すべてのArcher	射手 (A2)はApe	猿 (A0)でもあり，ゾンビでもあります．
ゾンビであるということは，それが現在のヘッドの右側にあるということを示しており，Ape	猿であるということは，その空間の色が1 (A)であるということを示しています．
ヘッドの左側にある同じ色の空間はAlly	同盟者かつApe	猿かつイエティです．

「右に1ステップ動く」という動作は，このマシンでは新しいイエティ・トークンを(ヘッドがあった場所のちょうど左に)作り，全てのイエティに+1修整を与え，全てのゾンビに-1修正を与えることによって表現されます．
詳細は以下のようになります:

![Kazuul Warload](http://gatherer.wizards.com/Handlers/Image.ashx?type=card&name=Kazuul%20Warlord)
![Noxious Ghoul](http://gatherer.wizards.com/Handlers/Image.ashx?type=card&name=Noxious%20Ghoul)
![Aether Flash](http://gatherer.wizards.com/Handlers/Image.ashx?type=card&name=Aether%20Flash)

マシンがアレックスのコントロール下で新しい2/2のイエティ・トークンを作った時，3つの能力がが誘発します: ボブの[有毒グール/Noxious Ghoul][Noxious Ghoul]，キャシーの[上天の閃光/AEther Flash][AEther Flash]，アレックスの[カズールの大将軍/Kazuul Warlord][Kazuul Warlord]です．
今はボブのターンなので，これらはスタックにこの順で積まれ，逆順で解決されます．
最初に，[改竄][Artificial Evolution]されている[カズールの大将軍/Kazuul Warlord][Kazuul Warlord]が解決され，全てのアレックスのイエティに+1/+1カウンターが置かれ，新しく3/3のイエティを作ることも含め，死亡から一歩遠ざけます．
次に，[上天の閃光/AEther Flash][AEther Flash]が新しいトークンに2ダメージ与え，必要に応じて，それのタフネスを死亡するまであと1にします．
最後に，[改竄][Artificial Evolution]されている[有毒グール/Noxious Ghoul][Noxious Ghoul]が，イエティでないクリーチャー全てに-1/-1修正を与え，一番タフネスが低いゾンビを殺します．
一番タフネスが低いゾンビの他のクリーチャー・タイプに応じて，違う能力が誘発します．
これでマシンは右に1ステップ動いたことになります．

もし新しいトークンがイエティではなくゾンビだった場合，別の[有毒グール/Noxious Ghoul][Noxious Ghoul]，別の[カズールの大将軍/Kazuul Warlord][Kazuul Warlord]が[上天の閃光/AEther Flash][AEther Flash]と同様に誘発します．
即ち，全てのゾンビが+1/+1修正を受け，全てのイエティが-1/-1修正を受けることを除き，全く同じことが起こります．
これでマシンは左に1ステップ動きます．

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
