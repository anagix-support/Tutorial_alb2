.. header::
  Anagix Corp. confidential ### this is not working yet

============================================================================
富士通65n PDKを使ったインバータとリングオシレータ回路図の作成
============================================================================
（2013年4月22日修正）

このチュートリアルでは、富士通65n PDKを使用しています。
インバータから構成されるリングオシレータのように、階層を持った回路を作成します。
回路データは、ALB上に保管されます。

回路ライブラリの作成
====================================
適当なプロジェクトに回路ライブラリを作ります（testLibとします）。

ALBタブの左側（回路側）で、マウスの右ボタンをクリックし、Newを選択します。


.. http://alb.anagix.com:8180/myGyazo/data/9aff03c0140cc96c680011c6d69b32be.png

.. image:: images/9aff03c0140cc96c680011c6d69b32be.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/9aff03c0140cc96c680011c6d69b32be.png

モデルライブラリの参照
====================================

今回使用するモデルライブラリの入っているプロジェクトを選択します
----------------------------------------------------------------

ALBタブの右側（モデル側）の下方にあるModel Projectのプルダウンから
富士通65n PDKのプロジェクト（この例の場合は、fpdk200l_3p5_1PDK1）を選択します。


.. http://alb.anagix.com:8180/myGyazo/data/4267afd4bfda6fcac0fb097c7334905d.png

.. image:: images/4267afd4bfda6fcac0fb097c7334905d.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4267afd4bfda6fcac0fb097c7334905d.png

回路ライブラリ(testLib)と使用するモデルライブラリ(fpdk200l_3p5_1PDK1)を結びつけます
------------------------------------------------------------------------------
回路ライブラリとモデルライブラリ(set_ms.scs）の中のセクション(top_tt)が選択された状態で、右ボタンをクリックし、
ALTA->addModelsを実行します。


.. http://alb.anagix.com:8180/myGyazo/data/91c9e8684a9ad9521e3ae06a5f715fe5.png

.. image:: images/91c9e8684a9ad9521e3ae06a5f715fe5.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/91c9e8684a9ad9521e3ae06a5f715fe5.png

以下の図のように、画面の左側（回路側）のtestLibの下に[model references]が作成され、
set_ms.scs(top_tt)へのリンクが作成されます。


.. http://alb.anagix.com:8180/myGyazo/data/2776745dfc2b5d23991697dac839dd3a.png

.. image:: images/2776745dfc2b5d23991697dac839dd3a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/2776745dfc2b5d23991697dac839dd3a.png

これ以降、この回路ライブラリで作成する回路では、このモデルライブラリを使用することができます。

インバータを作成
====================================
1. インバータ（myinv）を作成するためにtestLibの上で右ボタンをクリックし、newChildを
選択します。


.. http://alb.anagix.com:8180/myGyazo/data/05b0c35e5dc77b107e87343d8284d74e.png

.. image:: images/05b0c35e5dc77b107e87343d8284d74e.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/05b0c35e5dc77b107e87343d8284d74e.png

注意：　invという名前にすると、後で回路シンボルを作成する際にLTspiceの備え付けの
Digitalライブラリにinvが存在するので不都合です。そのため名前をmyinvにしています。

すると、以下のようにLTspiceが開きます。初めての場合、LTspiceが開くまでかなり待たされます。

ALBで、富士通65n PDKのモデルライブラリ（fpdk200l_3p5_1PDK1）をLTspice用に変換しますが、
富士通65n PDKは、モデルライブラリの作りが特殊なため、変換に時間がかかります。一度変換
されたものはキャッシュされますので、２度目以降は変換に時間はかかりません。


.. http://alb.anagix.com:8180/myGyazo/data/92e689df37154b3ab2681f3bb4b433d3.png

.. image:: images/92e689df37154b3ab2681f3bb4b433d3.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/92e689df37154b3ab2681f3bb4b433d3.png

モデルライブラリ（fpdk200l_3p5_1PDK1）を参照する記述（ディレクティブ）が生成されています。
回路を描きやすいように、適当に移動してください。

*注意１：* 回路データおよびモデルがダウンロードされるまで、あまりに時間がかかった場合、以下のようなエラーが出ることがあります。


.. http://alb.anagix.com:8180/myGyazo/data/340fdb671b8a18a8d57860065a4c4ad3.png

.. image:: images/340fdb671b8a18a8d57860065a4c4ad3.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/340fdb671b8a18a8d57860065a4c4ad3.png

その時は、OKした後で、myinvをダブルクリックするか、myinvを選択してEditボタンをクリックしてください。

*注意２：* FirefoxのMozreplの設定が不十分な場合、エラーメッセージがでます。その場合、Mozreplを設定し、
myinvを一度削除（myinvの上で右ボタンからDeleteを選択）した後、myinvを作成しなおしてください。

2. LTspiceのコンポーネントボタン（右上のANDアイコン）をクリックし、fprim200l_nonDFMから
素子を選択します。fprim200l_nonDFMに入るためには[fprim200l_nonDFM]をダブルクリックします。


.. http://alb.anagix.com:8180/myGyazo/data/78d2e0c8349ced39e7e3d8413a73b091.png

.. image:: images/78d2e0c8349ced39e7e3d8413a73b091.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/78d2e0c8349ced39e7e3d8413a73b091.png

fprim200l_nonDFMに入ると、以下のように素子を選ぶことができます。（ただし、gndは、LTspiceのものを使用してください。）


.. http://alb.anagix.com:8180/myGyazo/data/1173a5850ace37a2230127ee3563860a.png

.. image:: images/1173a5850ace37a2230127ee3563860a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/1173a5850ace37a2230127ee3563860a.png

3. myinvの回路図を作成します

この説明図では、素子名がM1とM2になっていますが、実際に作成した回路図ではU1とU2と表示されるはずです。
fprim200l_nonDFMシンボルライブラリでは、MOSモデルがサブサーキットで表現されているため、シンボルの
Prefixとして、サブサーキットを意味する’X’を使用しています。そのため、素子名は、U1, U2となります。
（analogLibのように、シンボル（この場合nchとpch）のPrefixがMOS素子を意味する'M'の場合、素子名は
M1,M2のように生成されます。）

実は、こチュートリアルを作成した際、使用したシンボルライブラリが古く、MOS素子のPrefixが’M’だったのが、この混乱の
原因です。そのため以下のフォームでは、Prefixが’M’となっていることに注目してください。あとで、これは
手作業により’X’に修正しました。（現在使用されているfprim200l_nonDFMシンボルライブラリでは、MOS素子の
Prefixがすでに’X’になっているので、ユーザが変更する必要はありません。）


.. http://alb.anagix.com:8180/myGyazo/data/c74e2e290ef4526e18fe86b769f50ca1.png

.. image:: images/c74e2e290ef4526e18fe86b769f50ca1.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/c74e2e290ef4526e18fe86b769f50ca1.png

MOSのパラメータは、素子の上で、コントロールキーを押しながら右ボタンをクリック
すると下図に示すような汎用のフォームが開きます。（実は、コントロールキーを押さなくても汎用のフォームが開きます。）

.. _mistake:


.. http://alb.anagix.com:8180/myGyazo/data/7f9e411b5eb8e26ed1714f5e44c5dbe2.png

.. image:: images/7f9e411b5eb8e26ed1714f5e44c5dbe2.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/7f9e411b5eb8e26ed1714f5e44c5dbe2.png

Valueには、モデル名がシンボルごとに設定されていますので、ｌ，ｗなどをValue2に入れます。

*注意：* 素子の上で、右ボタンをクリックした場合は、素子のPrefixが’X’以外の場合は下図のような専用フォームを
使うことができます。しかし、この例の場合、素子のPrefixが'X'なので、汎用フォームしか使用
できません。


.. http://alb.anagix.com:8180/myGyazo/data/3cafcb5a54c10c79e1f9a175f01bfc69.png

.. image:: images/3cafcb5a54c10c79e1f9a175f01bfc69.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/3cafcb5a54c10c79e1f9a175f01bfc69.png

直流電圧源の電圧値は、素子の上で右ボタンをクリックすれば、下図のフォームを使って入力できます。
電圧値は2.5となってますが、使用するプロセスの耐圧に合わせて適当に設定してください。


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


.. http://alb.anagix.com:8180/myGyazo/data/c2386f9014748b908b04a2da65038bf1.png

.. image:: images/c2386f9014748b908b04a2da65038bf1.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/c2386f9014748b908b04a2da65038bf1.png

注意: l, wの値を設定せずに、LTspiceシミュレーションを実行した場合、以下のようなモデルが見つからないというエラー
が発生します。


.. http://alb.anagix.com:8180/myGyazo/data/22e2ff16afbb78d95ba904922794369b.png

.. image:: images/22e2ff16afbb78d95ba904922794369b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/22e2ff16afbb78d95ba904922794369b.png

このPDKのMOSモデルでは、l, wの値の範囲によってモデルの領域を切り替えています。l, wの値が
与えられていないと領域を見つけることができないのでエラーになります。

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


.. http://alb.anagix.com:8180/myGyazo/data/8af27d6939ff8191ed1fab175937223f.png

.. image:: images/8af27d6939ff8191ed1fab175937223f.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/8af27d6939ff8191ed1fab175937223f.png


インバータのシンボルを作成する
====================================
1. 再度、myinvを開きます。今回は、myinvをダブルクリックしてみてください。


.. http://alb.anagix.com:8180/myGyazo/data/5c24c2fb5a0dda4c8b5683345ca08df2.png

.. image:: images/5c24c2fb5a0dda4c8b5683345ca08df2.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/5c24c2fb5a0dda4c8b5683345ca08df2.png

2. リングオシレータからインバータ（myinv）を呼び出すことができるように、
myinvのシンボルを作成します。そのために、myinv回路図を以下のように変更し、
inとoutのピンを作成します。


.. http://alb.anagix.com:8180/myGyazo/data/b6d703b1e356bcc49c1bd2e84118204d.png

.. image:: images/b6d703b1e356bcc49c1bd2e84118204d.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b6d703b1e356bcc49c1bd2e84118204d.png

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

.. http://alb.anagix.com:8180/myGyazo/data/de9a1024fd92abe4e03d787074d39424.png

.. image:: images/de9a1024fd92abe4e03d787074d39424.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/de9a1024fd92abe4e03d787074d39424.png

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
何も特に工夫しなくても、発振しました


.. http://alb.anagix.com:8180/myGyazo/data/447e2047b9a8b1bbb93593e78388dbce.png

.. image:: images/447e2047b9a8b1bbb93593e78388dbce.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/447e2047b9a8b1bbb93593e78388dbce.png

analogLibを使った、同じリングオシレータの例の場合、モデルを間違ったために、
発振が起きず、スタートアップのためにパルス電源を入れるなど工夫する必要がありました。

analogLibを使ったチュートリアルでは、その関連で、
LTspiceでデフォルトで追加されるモデルをなくす方法や、
'μ'がフォントの関係でおかしな表示になるのをさけるため、 'u'の表示に変える方法を
説明しています。参考にしてください。

.. raw:: html

   <DIV align="right">以上</DIV>

   <!-- DIV style="text-align: right;" >以上</DIV -->

