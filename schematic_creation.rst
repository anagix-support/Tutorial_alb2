.. header::
  Anagix Corp. confidential ### this is not working yet
.. _schematic_creation:
============================================================================
インバータとリングオシレータ回路図の作成
============================================================================
（2013年4月22日修正）

このチュートリアルでは、Cadence ADEから変換したanalogLibを例として使用して
います。analogLibが無い場合は、LTspiceのシンボルをお使いください。

回路ライブラリの作成
====================================
適当なプロジェクトに回路ライブラリを作ります（testLibとします）。

ALBタブの左側（回路側）で、マウスの右ボタンをクリックし、Newを選択します。


.. http://alb.anagix.com:8180/myGyazo/data/e37284c7b79c11662cb86b2a110b9fcb.png

.. image:: images/e37284c7b79c11662cb86b2a110b9fcb.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e37284c7b79c11662cb86b2a110b9fcb.png

モデルライブラリの参照
====================================

今回使用するモデルライブラリの入っているプロジェクトを選択します
----------------------------------------------------------------

ALBタブの右側（モデル側）の下方にあるModel Projectのプルダウンから
適当なプロジェクト（この例の場合は、ALTA sample2）を選択します。


.. http://alb.anagix.com:8180/myGyazo/data/948baf70c9b47c352bc7f6d26ea049e3.png

.. image:: images/948baf70c9b47c352bc7f6d26ea049e3.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/948baf70c9b47c352bc7f6d26ea049e3.png

（Spectre用のモデルファイルを読み込んで、ALB上にモデルライブラリを作成することもできますが、
今回は簡単のため、既存のモデルライブラリを使用します。）

回路ライブラリ(testLib)と使用するモデルライブラリ(tsmc_0p35.mod)を結びつけます
------------------------------------------------------------------------------
回路ライブラリとモデルライブラリが選択された状態で、右ボタンをクリックし、
ALTA->addModelsを実行します。

.. http://alb.anagix.com:8180/myGyazo/data/e187735717d7c486156c56dcac15c529.png

.. image:: images/e187735717d7c486156c56dcac15c529.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e187735717d7c486156c56dcac15c529.png

以下の図のように、画面の左側（回路側）のtestLibの下に[model references]が作成され、
tsmc_0p35.modへのリンクが作成されます。

.. http://alb.anagix.com:8180/myGyazo/data/e0cc11eb7f5d63112829bdc5a158e912.png

.. image:: images/e0cc11eb7f5d63112829bdc5a158e912.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e0cc11eb7f5d63112829bdc5a158e912.png

これ以降、この回路ライブラリで作成する回路では、このモデルライブラリを使用することができます。

インバータを作成
====================================
1. インバータ（myinv）を作成するためにtestLibの上で右ボタンをクリックし、newChildを
選択します。

注意：　invという名前にすると、後で回路シンボルを作成する際にLTspiceの備え付けの
Digitalライブラリにinvが存在するので不都合です。そのため名前をmyinvにしています。

.. http://alb.anagix.com:8180/myGyazo/data/b189d309e5ca5f13c88bfd2881ccbcaf.png

.. image:: images/b189d309e5ca5f13c88bfd2881ccbcaf.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b189d309e5ca5f13c88bfd2881ccbcaf.png
すると、以下のようにLTspiceが開きます。


.. http://alb.anagix.com:8180/myGyazo/data/11875f7c269d283dac397fc91e2abf51.png

.. image:: images/11875f7c269d283dac397fc91e2abf51.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/11875f7c269d283dac397fc91e2abf51.png

FirefoxのMozreplの設定が不十分な場合、エラーメッセージがでます。その場合、Mozreplを設定し、
myinvを一度削除（myinvの上で右ボタンからDeleteを選択）した後、myinvを作成しなおしてください。

モデルライブラリ（tsmc_0p35.mod）を参照する記述（ディレクティブ）が生成されています。
適当に移動してください。

2. LTspiceのコンポーネントボタン（右上のANDアイコン）をクリックし、analogLibから
素子を選択します。analogLibに入るためには[analogLib]をダブルクリックします。

.. http://alb.anagix.com:8180/myGyazo/data/d979bc08f1bff260e084da80188ae043.png

.. image:: images/d979bc08f1bff260e084da80188ae043.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/d979bc08f1bff260e084da80188ae043.png
analogLibに入ると、以下のように素子を選ぶことができます。（ただし、gndは、LTspiceのものを使用してください。）

.. http://alb.anagix.com:8180/myGyazo/data/04f1471d1997b54aa775105cf28e3dbd.png

.. image:: images/04f1471d1997b54aa775105cf28e3dbd.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/04f1471d1997b54aa775105cf28e3dbd.png

3. myinvの回路図を作成します

.. http://alb.anagix.com:8180/myGyazo/data/d49f03fa88b4d56c8a56cbbd46413485.png

.. image:: images/d49f03fa88b4d56c8a56cbbd46413485.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/d49f03fa88b4d56c8a56cbbd46413485.png
MOSのパラメータは、素子の上で、コントロールキーを押しながら右ボタンをクリック
すると下図に示すような汎用のフォームが開きます。

.. _mistake:


.. http://alb.anagix.com:8180/myGyazo/data/da9cc9695df0494edcda9b4808e2ef8e.png

.. image:: images/da9cc9695df0494edcda9b4808e2ef8e.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/da9cc9695df0494edcda9b4808e2ef8e.png

Valueのところに、モデル名(nmosやpmos)、ｌ，ｗなどをValue2に入れます。
素子の上で、右ボタンをクリックした場合は、下図のような専用フォームを使うことが
できます。（PDKによっては、汎用フォームでないとすべてのパラメータを入力できません。）

.. http://alb.anagix.com:8180/myGyazo/data/4738e10bbf67db2ba22b321c3ac38e56.png

.. image:: images/4738e10bbf67db2ba22b321c3ac38e56.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4738e10bbf67db2ba22b321c3ac38e56.png

直流電圧源の電圧値は、素子の上で右ボタンをクリックすれば、下図のフォームを使って入力できます。

.. http://alb.anagix.com:8180/myGyazo/data/f1e7694fc433c6100b1a5631537f47f1.png

.. image:: images/f1e7694fc433c6100b1a5631537f47f1.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/f1e7694fc433c6100b1a5631537f47f1.png

V2にサイン波を入力するには、Advancedボタンをクリックしてください。下図のようなフォームを使うことができます。

.. http://alb.anagix.com:8180/myGyazo/data/71417f502db63a6f5b74012767b30e25.png

.. image:: images/71417f502db63a6f5b74012767b30e25.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/71417f502db63a6f5b74012767b30e25.png

インバータのシミュレーション
====================================
1. シミュレーションを実行するRunボタン（人が走っているようなアイコン）をクリック
すると、下図のようなフォームが出てきます。OKすると実行を開始します。

.. http://alb.anagix.com:8180/myGyazo/data/85c4d624439f83a75f330be3578c3d05.png

.. image:: images/85c4d624439f83a75f330be3578c3d05.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/85c4d624439f83a75f330be3578c3d05.png

2. 実行結果を示します。波形は以下の方法で表示することができます。

* 波形表示のウィンドウでマウスの右ボタンをクリックし Visible TracesやAdd Traceから見たいノードを選択する

* 回路図上でマウスの左ボタンを使って電圧あるいは電流プローブをたてる


.. http://alb.anagix.com:8180/myGyazo/data/17ae55a240feeb1389721434fe547562.png

.. image:: images/17ae55a240feeb1389721434fe547562.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/17ae55a240feeb1389721434fe547562.png

インバータをアップロード
====================================
ここでいったん作業を終了するために、LTspiceのウィンドウを閉じます。
回路をローカルのディスクにセーブしていない場合、以下のようなフォームが出ます
のでYesしてください。

.. http://alb.anagix.com:8180/myGyazo/data/b1fdbb8b85ee55365361301433356b67.png

.. image:: images/b1fdbb8b85ee55365361301433356b67.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b1fdbb8b85ee55365361301433356b67.png
（デフォルトでは、LTspice終了後に、ローカルディスクの回路データは削除されます。
削除されないように変更するには、ALTA画面のSchematicタブで、Remove job dir.のチェックを
外してください。

回路データがALBサーバにセーブされると、ALTAの画面が以下のように変わります。

.. http://alb.anagix.com:8180/myGyazo/data/534cd86ab85e010a4f80930e52ef4224.png

.. image:: images/534cd86ab85e010a4f80930e52ef4224.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/534cd86ab85e010a4f80930e52ef4224.png

インバータのシンボルを作成する
====================================
1. 再度、myinvを開きます。今回は、myinvをダブルクリックしてみてください。

.. http://alb.anagix.com:8180/myGyazo/data/7906dbe0368ebcfbda303682f7298786.png

.. image:: images/7906dbe0368ebcfbda303682f7298786.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/7906dbe0368ebcfbda303682f7298786.png


2. リングオシレータからインバータ（myinv）を呼び出すことができるように、
myinvのシンボルを作成します。そのために、myinv回路図を以下のように変更し、
inとoutのピンを作成します。

.. http://alb.anagix.com:8180/myGyazo/data/9131009de36ec5a1807258200a375fe9.png

.. image:: images/9131009de36ec5a1807258200a375fe9.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/9131009de36ec5a1807258200a375fe9.png

シンボルを自動的に作成するために、Hierarchyというプルダウンから、Open this Sheet's Symbolを選択します。

.. http://alb.anagix.com:8180/myGyazo/data/74db3ee165cd0fe4153f60f0decf3ef8.png

.. image:: images/74db3ee165cd0fe4153f60f0decf3ef8.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/74db3ee165cd0fe4153f60f0decf3ef8.png

回路にはまだシンボルがないので、シンボルを作成するかを聞いてくる以下のフォームが出ます。

.. http://alb.anagix.com:8180/myGyazo/data/e92f1e0c86abd5b45ce2d2765c9478db.png

.. image:: images/e92f1e0c86abd5b45ce2d2765c9478db.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e92f1e0c86abd5b45ce2d2765c9478db.png

Yesすると、シンボルが作成されます。ピンの配置が気に入らなければ移動してください。
手のひらの形をしたアイコンを使うと、シンボルの形状を変えることが
できます。新たにシンボルの図形を入力することもできます。

.. http://alb.anagix.com:8180/myGyazo/data/aa028e584f7a0f2e388b7175aefcf87a.png

.. image:: images/aa028e584f7a0f2e388b7175aefcf87a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/aa028e584f7a0f2e388b7175aefcf87a.png

リングオシレータの作成
====================================
1. ここでALTAに戻って、リングオシレータ（ring_osc）を作成します。
testLibの上で右ボタンをクリックしてnewChildを選択するか、またはmyinvの上で右ボタンをクリックし、New
をクリックします。

ring_osc回路が開きますが、実はこのままでは、myinvを呼び出すことはできません。
ローカルのコンピュータ上にmyinvのデータが存在しないからです。

ALTA画面は、schematicタブの表示になっているので、まずALBタブをクリックしてALBブラウザの
画面にしてください。

次に、myinvを右ボタンでクリックし、ALTA->altaAppendを実行して、ローカルのコンピュータ上に
myinvの回路データを追加してあげる必要があります。

.. http://alb.anagix.com:8180/myGyazo/data/5111a4bf89a6cc6a7c2a9a80959e5d43.png

.. image:: images/5111a4bf89a6cc6a7c2a9a80959e5d43.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/5111a4bf89a6cc6a7c2a9a80959e5d43.png

2. これで、ようやくring_oscからmyinvを呼び出すことができます。
コンポーネントボタン（ANDアイコン）をクリックし、以下のフォームを出してください。そして、
右上のc:\Program Files\LTC\LTspiceIV\lib\symが表示されているプルダウンを、c:\...ALBDATA\1234の
ような数字の表示に変更します。この数字名のディレクトリが、ローカルのコンピュータ
上にLTspiceの回路データが置かれる場所です。

.. http://alb.anagix.com:8180/myGyazo/data/6b29d684fb1d397462f7808e0a4dd17b.png

.. image:: images/6b29d684fb1d397462f7808e0a4dd17b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/6b29d684fb1d397462f7808e0a4dd17b.png

myinv を選択すると　ring_oscにmyinvのシンボルが置かれます。

.. http://alb.anagix.com:8180/myGyazo/data/6f334c27587c51728c0d2a4f212bd536.png

.. image:: images/6f334c27587c51728c0d2a4f212bd536.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/6f334c27587c51728c0d2a4f212bd536.png

3. ring_oscの回路図を作成してください。


リングオシレータのシミュレーション
====================================
早速シミュレーションを実行しましたが発振しません。（後述するように、myinvで使用したnmosと
pmosのモデル名の設定にミスがあったのが原因です。モデル名をcmosnとcmospに変えれば容易に
発振します。）


.. http://alb.anagix.com:8180/myGyazo/data/783a9bb2cb966a0d8fa68e9b221eda6b.png

.. image:: images/783a9bb2cb966a0d8fa68e9b221eda6b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/783a9bb2cb966a0d8fa68e9b221eda6b.png

スタートアップのためにパルス電源を入れます。

.. http://alb.anagix.com:8180/myGyazo/data/29a892dcecf1daa3642e03c300e94d67.png

.. image:: images/29a892dcecf1daa3642e03c300e94d67.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/29a892dcecf1daa3642e03c300e94d67.png

各段の出力に容量負荷を追加することで、発振を確認できました。

.. http://alb.anagix.com:8180/myGyazo/data/5708c212405ff05fd155d45b3a5d357d.png

.. image:: images/5708c212405ff05fd155d45b3a5d357d.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/5708c212405ff05fd155d45b3a5d357d.png

実は、この回路では、myinvで使用したnmosとpmosのモデル名の設定にミスがあったために、
非常に高速な（理想的な）トランジスタでシミュレーションを実行していました。
myinvの回路図を作成し、:ref:`モデル名を入力した際<mistake>` のモデル名が間違って
いました。正しくは、nmosではなくcmosn、pmosではなくcmospでした。

LTspiceのデフォルト状態では、nmos、pmosという理想モデルがネットリストに追加されます。
そのため理想モデルを使ったシミュレーションが実行されてしまいました。

LTspiceで、Tools->ControlPanelを実行する、あるいは、金槌のアイコンをクリックすると、
以下のようなフォームが出ます。Netlist Optionsのタブで、Semiconductor Modelsの
Default Devicesのチェックを外すと、理想モデルはネットリストに追加されなくなります。


.. http://alb.anagix.com:8180/myGyazo/data/736db9130e42e7154a76601eb1ce2c9d.png

.. image:: images/736db9130e42e7154a76601eb1ce2c9d.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/736db9130e42e7154a76601eb1ce2c9d.png

ついでに、

.. raw:: html

   <input type="checkbox" value="true">Convert 'μ' to 'u'</input>

にはチェックを入れておいた方が良いです。

:ref:`モデル名を入力した際<mistake>` のモデル名を正しいもの（cmosnとcmosp）に変えて、シミュレーションを
実行してみてください。

.. raw:: html

   <DIV align="right">以上</DIV>

   <!-- DIV style="text-align: right;" >以上</DIV -->

