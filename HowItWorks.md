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

トークンのパワーとタフネスは繊細な調整を必要とします．
[腐れ肺の再生術師/Rotlung Reanimator][Rotlung Reanimator]は通常は2/2のトークンを出します．
マシンのヘッドによって生み出されたそれぞれのトークンは，2体の[ドラルヌの十字軍/Dralnu's Crusade][Dralunu's Crusade]の影響によって+2/+2の修正を受け，また，[死の支配の呪い/Curse of Death's Hold][Curse of Death's Hold]と[仕組まれた疫病/Engineered Plague][Engineered Plague]によって-2/-2修正を受けます．

## チューリングマシンのヘッド
Yurii Rogozhinが[1996年に出した論文](http://www.sciencedirect.com/science/article/pii/S0304397596000771)に載っている，最も簡単な2つの状態と18のテープの色を持つ万能チューリングマシンを使います．
それぞれの色の空間をそれぞれの状態の時に読んだ時，どう動くかをこのマシンのルールは明記しています．
このルールの最初の数行はこのようになっています:

- 状態B，色16: 状態Bのまま，色を18にして，1つ右にずれる．
- 状態B，色17: 状態Aになり，色を18にして，1つ左にずれる．
- 状態B，色18: 状態Bのまま，色を13にして，1つ左にずれる．
- 状態A，色16: 状態Bになり，色を17にして，1つ右にずれる．
- 状態A，色17: 停止!
- 状態A，色18: 状態Aのまま，色を 3にして，1つ右にずれる．

チューリングマシンの心臓部のキーカードは，[腐れ肺の再生術師/Rotlung Reanimator][Rotlung Reanimator]と[人口進化/Artificial Evolution][Artificial Evolution]です．
たくさんの再生術師のコピーを使い，それぞれがそれぞれを監視し，クリーチャー・タイプの異なるペアを作成するように[変更][Artificial Evolution]します．

実際には，なんと再生術師の43体のコピーをヘッドに用いるのです!
彼らは次のようなルールがエンコードされるように変更されています:

- フェイズ・アウトしている再生術師16Bは，「Pegasus	ペガサス(P0)が死亡するたび，Siren	サイレン(S2)を1体戦場に出す」
- フェイズ・アウトしている再生術師17Bは，「Rat	鼠(R0)が死亡するたび，[時空の満ち干/Time and Tide][Time and Tide]を唱え，Slith	スリス(S1)を1体戦場に出す」
- フェイズ・アウトしている再生術師18Bは，「Shade	影(S0)が死亡するたび，[時空の満ち干/Time and Tide][Time and Tide]を唱え，Moonfolk	ムーンフォーク(M1)を1体戦場に出す」
- フェイズ・インしている再生術師16Aは，「Pegasus	ペガサス(P0)が死亡するたび，[時空の満ち干/Time and Tide][Time and Tide]を唱え，Rigger	装具工(R2)を1体戦場に出す」
- フェイズ・インしている再生術師17Aは，「Rat	鼠(R0)が死亡したとき，マシンを終了する」
- フェイズ・インしている再生術師18Aは，「Shade	影(S0)が死亡するたび，Carrier	キャリアー(C2)を1体戦場に出す」

これと(2, 18)チューリングマシンとの対応ができていることがわかるでしょうか．新しく作られたトークンのタイプはそこの空間が何色なのか(AからQを飛ばしてSまで)と，どちらに動くのか(右か左か)，を示しています．
[時空の満ち干/Time and Tide][Time and Tide]を唱えることは，状態を変えることに対応しています．

![腐れ肺の再生術師/Rotlung Reanimator](http://gatherer.wizards.com/Handlers/Image.ashx?type=card&name=Rotlung%20Reanimator)
![人口進化/Artificial Evolution](http://gatherer.wizards.com/Handlers/Image.ashx?type=card&name=Artificial%20Evolution)

もちろん，普通は再生術師のテキストを「Shade	影(S0)が死亡するたび，[時空の満ち干/Time and Tide][Time and Tide]を唱え，Moonfolk	ムーンフォーク(M1)を1体戦場に出す」に改竄することはできません．
誘発型能力の結果としてインスタントが唱えられるということは，このチューリングマシンが乗り越えなければならない最大のハードルです．

## 状態の変更
何回もこのインスタントを唱えるために，このチューリングマシンのバージョンでは，[尖塔の大長/Chancellor of the Spires][Chancellor of the Spires]を使います．
これは，[梅澤俊郎/Toshiro Umezawa][Toshiro Umezawa]と[呪文冊子/Spellbinder][Spellbinder]を使っていた前のバージョンよりもずっと簡単です．

![時空の満ち干/Time and Tide](http://gatherer.wizards.com/Handlers/Image.ashx?type=card&name=Time%20and%20Tide)
![尖塔の大長/Chancellor of the Spires](http://gatherer.wizards.com/Handlers/Image.ashx?type=card&name=Chancellor%20of%20the%20Spires)

[屍滑り/Necroskitter][Necroskitter]と[標本集め/Gather Specimens][Gather Specimens]を[尖塔の大長/Chancellor of the Spires][Chancellor of the Spires]を戦場に出すために用い，[荒廃の鎌/Blight Sickle][Blight Sickle]を装備した[タジュールの射手/Tajuru Archer][Tajuru Archer]でそれを死なせます．
大長が解決された時にこのインスタントはキャシーの墓地にあるので，[時空の満ち干/Time and Tide][Time and Tide]を手に入れるのに，何も特別なトリックは必要としません．

だから,状態を変更する必要のあるリアニメイターは，通常の状態の[有毒グール/Noxious Ghoul][Noxious Ghoul]と[カズールの大将軍/Kazuul Warlord][Kazuul Warlord]の能力の誘発を避けるために，実際には違うクリーチャー・タイプのトークンを生成し，状態を変える能力を誘発させます．
私はこれらの「メッセンジャー」クリーチャー・タイプを最後に「M」が付くようにして示します．

- 再生術師の17Bは，実際には「Rat	鼠(R0)が死亡するたび，Sliver	スリヴァー(S1M)を1体戦場に出す」と書かれ，
- 再生術師の16Aは，実際には「Pegasus	ペガサス(P0)が死亡するたび，Rhino サイ(R2M)を1体戦場に出す」と書かれています．

これらのS1MやR2Mのような「メッセンジャー」トークンは，Yeti イエティやZombie ゾンビではありませんが，Reflection 反射です．
よってこれらでは[有毒グール/Noxious Ghoul][Noxious Ghoul]と[カズールの大将軍/Kazuul Warlord][Kazuul Warlord]の能力は誘発せず，代わりにアレックスのReflection 反射を参照するように[改竄][Artificial Evolution]された[タジュールの射手/Tajuru Archer][Tajuru Archer]の能力が誘発します．
メッセンジャー・トークンが死んだとき，実際の望むタイプのトークンを出すために更に幾つかの[腐れ肺の再生術師/Rotlung Reanimator][Rotlung Reanimator]の能力を誘発させます．
それらの誘発型能力が正しい順番でスタックに積まれるように，[標本集め/Gather Specimens][Gather Specimens]で[腐れ肺の再生術師/Rotlung Reanimator][Rotlung Reanimator]のコントローラーをボブにします．

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
[Toshiro Umezawa]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=94248
[Spellbinder]:http://gatherer.wizards.com/Pages/Card/Details.aspx?multiverseid=76264
