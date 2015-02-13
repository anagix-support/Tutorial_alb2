.. _alb_first_step:
==============
ALB最初の一歩
==============
(2013.4.27修正)

ALBにログインする
---------------
ALBにログインすると最初に表示されるページをHomeページと呼びます。


.. http://alb.anagix.com:8180/myGyazo/data/1ba368e12b519e685ab1587bee5c0962.png

.. image:: images/1ba368e12b519e685ab1587bee5c0962.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/1ba368e12b519e685ab1587bee5c0962.png

Choose a project you are involved: と表示された行の下に、Allという文字列が表示されたプルダウンメニュがあります。その中から
プロジェクトを選択してください。ここでは、ユーザ名と同じ名前のプロジェクトを選択します。


.. http://alb.anagix.com:8180/myGyazo/data/9787dcb17151ce230e7d43122c3b7def.png

.. image:: images/9787dcb17151ce230e7d43122c3b7def.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/9787dcb17151ce230e7d43122c3b7def.png

最初は、空なので表示されるライブラリはありません。

ライブラリを作る
---------------

New Libraryをクリックしてライブラリを作成します。


.. http://alb.anagix.com:8180/myGyazo/data/333722d28a988a66ff9ea612aa8d6ceb.png

.. image:: images/333722d28a988a66ff9ea612aa8d6ceb.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/333722d28a988a66ff9ea612aa8d6ceb.png

CreateLibraryをクリックして、testLibという名前のライブラリを作成しました。


.. http://alb.anagix.com:8180/myGyazo/data/2208f714629eaa90871bf3ede3d3d0d3.png

.. image:: images/2208f714629eaa90871bf3ede3d3d0d3.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/2208f714629eaa90871bf3ede3d3d0d3.png

表示されるセル（回路）はありません。この下に、回路を作成します。

セル（回路）を作る
----------------
simpleという名前で回路を作ります。


.. http://alb.anagix.com:8180/myGyazo/data/d2e0cfb8c452c32ffc150080b065720f.png

.. image:: images/d2e0cfb8c452c32ffc150080b065720f.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/d2e0cfb8c452c32ffc150080b065720f.png

このセルは、いわば箱で、この下に具体的なシミュレータに対応したネットリストを作成します。
今回は、LTspice用のネットリストを作成するので、LTspiceを選択し、Create Cellをクリック
してください。


.. http://alb.anagix.com:8180/myGyazo/data/cfebd9556821865c9cbba7b54fbb687b.png

.. image:: images/cfebd9556821865c9cbba7b54fbb687b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/cfebd9556821865c9cbba7b54fbb687b.png

以下のように simple というcellが作成されました。


.. http://alb.anagix.com:8180/myGyazo/data/d6cff31ae4580b6e5ad8e8c5332e58ee.png

.. image:: images/d6cff31ae4580b6e5ad8e8c5332e58ee.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/d6cff31ae4580b6e5ad8e8c5332e58ee.png

*注意１：* もしも、シミュレータを選択する前に Create Cellしてしまった場合は、Edit Cell
をクリックしてシミュレータを選択しなおしてください。

*注意２：* セルを作り直したいときは、Edit Cellの画面の右上にある、Remove This Cellを実行します。

ネットリストを作成する
-------------------
前述のように、作成されたセルは、さまざまなシミュレータに対応したネットリストを格納する箱です。
LTspice用のネットリストを作成するために、New Cell Implementationをクリックします。


.. http://alb.anagix.com:8180/myGyazo/data/9095a10ef6041d95d874cba45790427b.png

.. image:: images/9095a10ef6041d95d874cba45790427b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/9095a10ef6041d95d874cba45790427b.png

Create Cell Implementationをクリックするとネットリストが作成されます。

.dcや.printのようなシミュレータの制御コマンド（古い人は制御カードとも呼ぶ）を一緒に入力したことに
注意してください。シミュレーションするために必要なシミュレーションインスタンス
とテストベンチも自動的に作成されています。


.. http://alb.anagix.com:8180/myGyazo/data/c57d0e2c337779191e61e9ac008a0ae1.png

.. image:: images/c57d0e2c337779191e61e9ac008a0ae1.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/c57d0e2c337779191e61e9ac008a0ae1.png

このセルのページでは、素子の値を表示したり、ネットリストを表示したりすることができます。


.. http://alb.anagix.com:8180/myGyazo/data/0274900c865972f8275d47a504b514ea.png

.. image:: images/0274900c865972f8275d47a504b514ea.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/0274900c865972f8275d47a504b514ea.png

LTspiceでシミュレーションする
--------------------------

シミュレーションを実行するためには、シミュレーションインスタンス（Instanceと表示される）と呼ぶれているものが必要です。
すぐにシミュレーションできないので、ALBは面倒くさいと感じられるかも知れませんが、以下の理由により
シミュレーションインスタンスは必要だと考えております。

* シミュレーションインスタンスは、パラメータを使った回路やテストベンチに実際の値を与えるとともに、モデルライブラリを選択するものである。
* シミュレーションインスタンスは、複数のテストベンチを持つことができ、シミュレーションを実行すれば、実行をenableされたテストベンチがすべて実行される
* プロジェクト、ライブラリ、セルなどと同様に、シミュレーションインスタンスにはドキュメントを付加することができる。
* セル（回路）をプライベートなものから共有のものに変更すれば、インスタンス（およびテストベンチ）を別の回路に適用することが容易になる。

Instance0と表示されているシミュレーションインスタンスをクリックすると、シミュレーションインスタンスのページに移ります。


.. http://alb.anagix.com:8180/myGyazo/data/ad3e6a71e6fc5f60cc68d6f0b170f127.png

.. image:: images/ad3e6a71e6fc5f60cc68d6f0b170f127.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/ad3e6a71e6fc5f60cc68d6f0b170f127.png

この例の場合、テストベンチは１つしかありませんが、Simulateをクリックすると、テストベンチにEnabledのチェックが入った
シミュレーションが順次実行されます。

テストベンチの行の右側に表示されたSimulateをクリックすれば、個々のテストベンチをシミュレーションできます。

しばらく待つと、Statusに starting と表示が出ます。


.. http://alb.anagix.com:8180/myGyazo/data/22a447a149b477af3542bee81bd37187.png

.. image:: images/22a447a149b477af3542bee81bd37187.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/22a447a149b477af3542bee81bd37187.png

Update statusをクリックしてください。Statusに変化があれば更新されます。表示されるStatusにはstartingの他に、running, prepared, completed, failedがあります。


.. http://alb.anagix.com:8180/myGyazo/data/6c94c8c55ddd8783881a448483ea7aa3.png

.. image:: images/6c94c8c55ddd8783881a448483ea7aa3.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/6c94c8c55ddd8783881a448483ea7aa3.png

Status がpreparedと表示された場合、ポストプロセスに失敗しています。今回は、ポストプロセスをまだ設定していないので、失敗して当然です。

DCをクリックすると、以下のように、シミュレーションの最初の時点での、ノード電圧や、素子を流れる電流が表示されます。

ここで重要なのは、ノード電圧や素子を流れる電流にアクセスするために、正確な名前を知ることができるということです。
何故なら、ポストプロセスでこれらの名前を使用するからです。


.. http://alb.anagix.com:8180/myGyazo/data/85e9f12c0d0a21356cf668baecb697b4.png

.. image:: images/85e9f12c0d0a21356cf668baecb697b4.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/85e9f12c0d0a21356cf668baecb697b4.png

結果を見る
---------


.. http://alb.anagix.com:8180/myGyazo/data/4885f4666aeac2f5af1326c1cfc4eb8c.png

.. image:: images/4885f4666aeac2f5af1326c1cfc4eb8c.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4885f4666aeac2f5af1326c1cfc4eb8c.png

テストベンチの行の右側にあるいくつものコマンドの中から、Editをクリックしてください。テストベンチの中の
ポストプロセスを編集することができます。


.. http://alb.anagix.com:8180/myGyazo/data/e3753b036df05584b0d4f159645cd044.png

.. image:: images/e3753b036df05584b0d4f159645cd044.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e3753b036df05584b0d4f159645cd044.png

今は、直接テストベンチを編集しましたが、別の方法もあります。

tbと表示されているテストベンチをクリックして、テストベンチのページに移ることができます。次にEdit Testbench Implementationを
クリックする方法でも同じように、テストベンチを編集することができます。


.. http://alb.anagix.com:8180/myGyazo/data/1beaeda3804afcf1d4c44676f27a674d.png

.. image:: images/1beaeda3804afcf1d4c44676f27a674d.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/1beaeda3804afcf1d4c44676f27a674d.png

セル（回路）の場合と同様に、テストベンチは一種の箱です。Testbench Implementationの編集では、
シミュレータごとに異なる制御カード（ALBではControlと表示しています）やネットリストを記述します。


.. http://alb.anagix.com:8180/myGyazo/data/837105224e25d320dab0c5300dc2ad6a.png

.. image:: images/837105224e25d320dab0c5300dc2ad6a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/837105224e25d320dab0c5300dc2ad6a.png

'...'となっている部分を、I(V1)のように書き換えてください。この名前が、さきほどのDC動作点のウィンドウに表示されたものです。

Postprocessには、Ruby言語を使ってスクリプトを記述することができます。


.. http://alb.anagix.com:8180/myGyazo/data/4885f4666aeac2f5af1326c1cfc4eb8c.png

.. image:: images/4885f4666aeac2f5af1326c1cfc4eb8c.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4885f4666aeac2f5af1326c1cfc4eb8c.png

あらためてtbの行の右側に表示されている PP をクリックしてください。以下のように Plot instanceが表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/b0898d603df0c781f3fa24efed58cffe.png

.. image:: images/b0898d603df0c781f3fa24efed58cffe.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b0898d603df0c781f3fa24efed58cffe.png

Quick plotをクリックすると、以下の図のようにプロットが表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/779dd65f882529dbdbfa153c9bf1a4cb.png

.. image:: images/779dd65f882529dbdbfa153c9bf1a4cb.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/779dd65f882529dbdbfa153c9bf1a4cb.png

'Plot instances:' の下に表示されたプロットの表の中から、tbをクリックすると、以下のようなプロットページが表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/cf8478f546f7d6d54d50c074a7149cbb.png

.. image:: images/cf8478f546f7d6d54d50c074a7149cbb.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/cf8478f546f7d6d54d50c074a7149cbb.png

このページでは、タイトルやX軸、Y軸を簡単に変更することができます。Titleのところや、Xlabel, Ylabelの
下の部分をクリックしてみてください。その場で、書き換えることができます。Redrawボタンをクリックすると
グラフが置き換わります。

*注意：* 残念ながら、現在のバージョンでは、タイトルなどに日本語を使うことはできません。

このグラフは、ズームすることができます。右ボタンをクリックしながら、矩形の領域を選択してみてください。その部分が
ズームされます。（ズームを解除するには、右ボタンをクリックした同じ場所で離せばよいです。）


.. http://alb.anagix.com:8180/myGyazo/data/0a21daa03c606fd4009b79448078eefb.png

.. image:: images/0a21daa03c606fd4009b79448078eefb.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/0a21daa03c606fd4009b79448078eefb.png

グラフを左ボタンでクリックすると、以下のようなフォームが出ますので、X軸やY軸の範囲やきざみを変更することが
できます。また、detailsのところの記述を工夫すれば、背景色を変えたり、グラフの大きさを変えたりできます。


.. http://alb.anagix.com:8180/myGyazo/data/279bd62810a5797cfd866f6bfc3d28b4.png

.. image:: images/279bd62810a5797cfd866f6bfc3d28b4.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/279bd62810a5797cfd866f6bfc3d28b4.png

Spectre用に変換する
------------------
セル（回路）の記述は、LTspice用しか作成していないので、SpectreでシミュレーションするためにはSpectre用の記述を
作成しなくてはなりません。まず、セルのページに行き、Spectre用に変換します。


.. http://alb.anagix.com:8180/myGyazo/data/eca50565cdb02a8bedf729ec7ede7353.png

.. image:: images/eca50565cdb02a8bedf729ec7ede7353.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/eca50565cdb02a8bedf729ec7ede7353.png

上図のインスタンスのページには、インスタンスの上位の階層である、セル、ライブラリ、プロジェクトへのリンクが、
< Seijiro Moriyama < testLib < simpleのようにプロジェクト、ライブラリ、セルの順に表示されています。
simpleセルをクリックして、セルのページに移ります。


.. http://alb.anagix.com:8180/myGyazo/data/900c4835cfea8c53f593adcd69ec5455.png

.. image:: images/900c4835cfea8c53f593adcd69ec5455.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/900c4835cfea8c53f593adcd69ec5455.png

Simulatorの表示のところにあるプルダウンでは、現在はLTspiceしか選択できません。
LTspiceのネットリストからSpectreネットリストへの変換が終われば、Spectreにも switchできるようになります。

Edit Cellをクリックしてセルを編集するページに入り、一番下の Simulatorのプルダウンから Spectreを選択し
Saveしてください。Spectre用Cell Implementationは存在しないので、LTspice用のものから自動変換されます。
（ALBでは、このように存在しないものを選択すると、現在あるものを変換して新たに作り出すという動きをすることが
よくあります。）


.. http://alb.anagix.com:8180/myGyazo/data/1ec41bca4a891a762b0141d4439b564d.png

.. image:: images/1ec41bca4a891a762b0141d4439b564d.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/1ec41bca4a891a762b0141d4439b564d.png

セルのSimulatorの表示が Spectreに変わっています。セルが階層を持っている場合、変更したセル以下の
階層のセルがすべて変換されます。それとは別に、セルに含まれるテストベンチの変換も同時に実行されています。


.. http://alb.anagix.com:8180/myGyazo/data/425cfe5b92a0ebc7c86564b9956f3c34.png

.. image:: images/425cfe5b92a0ebc7c86564b9956f3c34.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/425cfe5b92a0ebc7c86564b9956f3c34.png

*注意：* ElementsとNetsが表示されていませんが、以下に示すように、ネットリストのフォーマットが
Spectreのnativeのものではないからです。

	| simulator lang=spice
	| r1 1 0 10K
	| v1 1 0 10
	| * .dc v1 0 10 0.01
	| * .print dc i(v1)

Edit Cell Implementationを実行し、以下のように nativeのフォーマットに変えれば、表示されるようになります。

     	  | r1 (1 0) resistor r=10K
	  | v1 (1 0) vsource dc=10


.. http://alb.anagix.com:8180/myGyazo/data/f0af0dc2f1875bbf871ca8ba2c85af1b.png

.. image:: images/f0af0dc2f1875bbf871ca8ba2c85af1b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/f0af0dc2f1875bbf871ca8ba2c85af1b.png

Spectreでシミュレーションする
--------------------------
Instance0をクリックして、インスタンスのページに戻ります。


.. http://alb.anagix.com:8180/myGyazo/data/efe22566101d45980fd6f9b574daa799.png

.. image:: images/efe22566101d45980fd6f9b574daa799.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/efe22566101d45980fd6f9b574daa799.png

Simulatorのプルダウンが Spectreになっていることを確認し、tbの行の右側から、Simulateを
クリックすればシミュレーションが始まります。LTspiceの場合と同様に、Statusが表示されます。
LTspiceの時は、startingでしたが、Spectreでは、runningと一歩先を行った状態が表示されました。
Status には以下の５つがあります。

       | starting --- 実行準備中
       | running --- 実行中
       | failed --- 実行に失敗
       | prepared --- 実行は成功したがポストプロセスに失敗
       | completed --- ポストプロセス成功


.. http://alb.anagix.com:8180/myGyazo/data/c202bf384193fe908e2f221bd0a0cd09.png

.. image:: images/c202bf384193fe908e2f221bd0a0cd09.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/c202bf384193fe908e2f221bd0a0cd09.png

Update statusをクリックすると、Statusが更新されます。


.. http://alb.anagix.com:8180/myGyazo/data/2cbd76afa4b699efaa4f859d3cbd6403.png

.. image:: images/2cbd76afa4b699efaa4f859d3cbd6403.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/2cbd76afa4b699efaa4f859d3cbd6403.png

preparedが出たので、DCをクリックしてノードの正確な名前を確認してください。


.. http://alb.anagix.com:8180/myGyazo/data/126e7b43d9410e81f1b5eace4af80334.png

.. image:: images/126e7b43d9410e81f1b5eace4af80334.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/126e7b43d9410e81f1b5eace4af80334.png

テストベンチを見ると、以下のように、'v1:p' であるべきところが'V1:p'となっていたことが
わかります。


.. http://alb.anagix.com:8180/myGyazo/data/60161c2eb189a0e154e4f70855b4035e.png

.. image:: images/60161c2eb189a0e154e4f70855b4035e.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/60161c2eb189a0e154e4f70855b4035e.png

インスタンスのページに戻り、テストベンチの行の右側にある PPをクリックしてください。今回は、
Statusが completedに変わり、プロットの表示が出ています。


.. http://alb.anagix.com:8180/myGyazo/data/0b056adade94e0f4e92732f590a09b63.png

.. image:: images/0b056adade94e0f4e92732f590a09b63.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/0b056adade94e0f4e92732f590a09b63.png

結果を比較する
------------

'Plot instances:' の下に表示されたプロットの表から、tbをクリックすると、以下のようなプロットが
表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/e4a87722861f244cd540753df72c32e7.png

.. image:: images/e4a87722861f244cd540753df72c32e7.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e4a87722861f244cd540753df72c32e7.png

最初のシミュレーション結果であるLTspiceのカーブが青色、Spectreのカーブが緑色で表示されます。
当然ながら重なっています。

カーブの表示順序を変えるには、Simfileが表示された行で、後ろに移動したいSimfileのところで、
Move lastをクリックしてください。ちなみに、DLをクリックすれば、Excelのcsv形式でシミュレーション
結果をダウンロードすることができます。

.. raw:: html

   <DIV align="right">以上</DIV>

   <!-- DIV style="text-align: right;" >以上</DIV -->

