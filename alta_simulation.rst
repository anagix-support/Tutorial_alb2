.. _alta_simulation:
===========================================
ALTAを使ったローカルマシーンでのシミュレーション
===========================================

ALTAを使ってローカルのLinuxマシーンでシミュレーションを実行する方法を説明するのが目的です。
ALBサーバにはSpectreのライセンスが無くSpectreを実行できないが、ローカルのLinuxマシーンでは実行できる場合に特に有効です。

このチュートリアルには、ALTA/ALBを使う上でのさまざまなノウハウを盛り込みました。
最初にLTspiceを使って回路図を作成し、ALBに登録します。回路図作成の詳細は省かれているので、
:ref:`インバータとリングオシレータ回路図の作成<schematic_creation>` を参考にしてください。
ALBには、LTspiceの回路図だけでなく、LTspice用のネットリストが登録されます。

Spectreでシミュレーションするために、ALB上で、LTspice用のネットリスト（と制御カード）をSpectre用に
変換します。この部分の詳細も省かれていますので、必要に応じて、:ref:`ALB最初の一歩 <alb_first_step>` を参照してください。

ローカルのLinuxマシーンでシミュレーションを実行する方法は２つあります。ALTAから、対話的にシミュレーション
する方法と、ALBからALTAを介したシミュレーションを起動する方法です。このチュートリアル
ではこの２つを説明します。

LTspiceで作成した回路図をALBに登録する
----------------------------------
以下のような回路図を作成してください。CRという名前の回路はサブサーキットになっており、テスト回路（testAC）では
X1というインスタンス名で呼び出されています。


.. http://alb.anagix.com:8180/myGyazo/data/7a3c9e289bf18fba229767016ca0ad80.png

.. image:: images/7a3c9e289bf18fba229767016ca0ad80.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/7a3c9e289bf18fba229767016ca0ad80.png

ALTAにログインし、適当なプロジェクトを選択してください。ここではユーザ専用に作成されたユーザ名と同じ名前のプロジェクト（Seijiro Moriyama）
を選択しました。


.. http://alb.anagix.com:8180/myGyazo/data/4c445f99fc368507d39c7ad3f1414407.png

.. image:: images/4c445f99fc368507d39c7ad3f1414407.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4c445f99fc368507d39c7ad3f1414407.png

LTspiceの回路図を取り込むために、適当なライブラリを作成します。それには、ALBタブの左側（回路側）で何も選択
されていない状態でマウスの右ボタンをクリックしNewを実行します。（または、既存のライブラリを選択した
状態でNewを実行します。）


.. http://alb.anagix.com:8180/myGyazo/data/48941d81d6663beec38ca2cd784a88ac.png

.. image:: images/48941d81d6663beec38ca2cd784a88ac.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/48941d81d6663beec38ca2cd784a88ac.png

Examplesという名前のライブラリを作成しました。


.. http://alb.anagix.com:8180/myGyazo/data/f965500e75418a9193042388ce87fc3f.png

.. image:: images/f965500e75418a9193042388ce87fc3f.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/f965500e75418a9193042388ce87fc3f.png

Examplesを選択した状態でマウスの右ボタンからALTA→Importを実行します。


.. http://alb.anagix.com:8180/myGyazo/data/6bb4e5d30229be0dbec6d46030a82440.png

.. image:: images/6bb4e5d30229be0dbec6d46030a82440.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/6bb4e5d30229be0dbec6d46030a82440.png

回路を作成したディレクトリを選択し、Openしてください。そして、回路が階層を
持っている場合、階層の一番上の回路（この場合は、testAC.ascというテストベンチ）を選択
してください。


.. http://alb.anagix.com:8180/myGyazo/data/9a426fba4ee25cb21f9bf6638ff0b82e.png

.. image:: images/9a426fba4ee25cb21f9bf6638ff0b82e.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/9a426fba4ee25cb21f9bf6638ff0b82e.png

Examplesには、回路セル（CR）および、シミュレーションのための
シミュレーションインスタンス（以下インスタンスと略記します）とテストベンチ（testAC）が作成されて
います。testAC(asc)のように(asc)が付加されているのは、testACが回路図であることを意味しています。
testAC(LTspice)の場合や、testAC(Spectre)の場合は、回路図はALB上に無く、それぞれLTspice, Spectre
に対応したネットリストが存在することを示しています。

LTspiceでシミュレーションする
--------------------------

テストベンチ（testAC）をダブルクリックするか、それを選択した状態でEditボタンをクリックしてLTspiceを
起動してください。


.. http://alb.anagix.com:8180/myGyazo/data/2309d8be353569bd2a9ff6191cd4a4d7.png

.. image:: images/2309d8be353569bd2a9ff6191cd4a4d7.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/2309d8be353569bd2a9ff6191cd4a4d7.png

LTspiceでシミュレーションを実行し、OUTノードにプローブを立ててください。


.. http://alb.anagix.com:8180/myGyazo/data/ffcc4048f8fbe0438eabfffc69c7fc1c.png

.. image:: images/ffcc4048f8fbe0438eabfffc69c7fc1c.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/ffcc4048f8fbe0438eabfffc69c7fc1c.png

シミュレーション結果をALBに送るために、プロットのウィンドウを一度マウスの左ボタンでクリックし、
LTspiceのメニュバーからFile→Saveを実行してください。（フロッピーディスクのようなアイコンをクリックしてもOKです。）

続いて、回路図のウィンドウを一度マウスの左ボタンでクリックし、LTspiceのメニュバーからFile→Saveを実行してください。

LTspiceのウィンドウを閉じると、シミュレーション結果がALBに送られ、LTspice用のネットリスト
がALB上に作成されます。

*注意：* LTspiceのControl Panelを開き、Operationのタブの設定を確認してください。


.. http://alb.anagix.com:8180/myGyazo/data/952af122b0009fca14afb7f1f20189af.png

.. image:: images/952af122b0009fca14afb7f1f20189af.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/952af122b0009fca14afb7f1f20189af.png

これはデフォルトの設定で、ALTAとの連携で特に不都合は発生していません。動作がおかしい場合、設定を適宜変更してください。

ALBで回路を開く
-------------

ALTA上で回路セルを選択し、Firefox上のALB画面に表示することができます。

ALTA上で、CRの回路を選択し、右マウスボタンで、ALB→Showを実行してください。


.. http://alb.anagix.com:8180/myGyazo/data/ddb3aa01eafbaa7ad86c8dfaa2f19f86.png

.. image:: images/ddb3aa01eafbaa7ad86c8dfaa2f19f86.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/ddb3aa01eafbaa7ad86c8dfaa2f19f86.png

以下のように、Firefoxの表示が、CRの回路のページに変わります。


.. http://alb.anagix.com:8180/myGyazo/data/489d04ba0c859b65e6afcb8ccffdc3e1.png

.. image:: images/489d04ba0c859b65e6afcb8ccffdc3e1.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/489d04ba0c859b65e6afcb8ccffdc3e1.png

*注意：* 

1. Firefox上で、ALBにはログイン済みである必要があります。

2. Firefoxに表示が出ない場合、Mozreplの設定が正しいか確認してください。

ALTAでの、Mozreplの設定は、Settingsタブで確認できます：


.. http://alb.anagix.com:8180/myGyazo/data/6d13bb373929ef72c4822c74ccf3ee74.png

.. image:: images/6d13bb373929ef72c4822c74ccf3ee74.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/6d13bb373929ef72c4822c74ccf3ee74.png

この例の場合、browser（Firefox）はlocalhostという名前、Mozreplで使用しているポートの
番号はデフォルトの4242です。

これに対応して、localhostのFirefoxは以下のように設定されていなければなりません。メニュバーの
ツール→MozReplを確認してください。


.. http://alb.anagix.com:8180/myGyazo/data/6002a5b658ad584e305c6832825aa043.png

.. image:: images/6002a5b658ad584e305c6832825aa043.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/6002a5b658ad584e305c6832825aa043.png

Activate on startupのチェックは、Firefox起動時にMozreplが有効になることを意味しています。
チェックを入れず、必要なときに、ツールー→MozRepl→Startを実行しても構いません。
Allow outside connectionのチェックは、ローカルのネットワークの外からのアクセスを許可するものです。

Spectre用ネットリストを生成する
----------------------------

回路セル（CR）のページで、Edit Cellをクリックしてセルを編集します。


.. http://alb.anagix.com:8180/myGyazo/data/9be44218931671ef049ad03ebb15c8ae.png

.. image:: images/9be44218931671ef049ad03ebb15c8ae.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/9be44218931671ef049ad03ebb15c8ae.png

SimulatorのプルダウンからSpectreを選択し、Saveしてください。回路が階層的な場合、
回路以下の階層のセルについて、Spectre用のネットリストが生成されます。また
その回路に対しSpectre用のテストベンチが生成されます。

*注意：* Spectre用ネットリストを生成しても、LTspice用のネットリストはそのままです。
セルや、テストベンチのページで、SimulatorのプルダウンからLTspiceを選択し、switchボタンを
クリックすれば表示を切り替えることができます。

この回路（CR）のネットリストを以下に示します。Spectre nativeのフォーマットではないため
ElementsやNetsは表示されていません。nativeフォーマットであれば、素子のリストと
すべてのネット名が表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/4a638119d9c5976a4d28794ee78bcc53.png

.. image:: images/4a638119d9c5976a4d28794ee78bcc53.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4a638119d9c5976a4d28794ee78bcc53.png

テストベンチ（testAC）です。ネットリストだけでなく、ControlやPostprocessもSpectre用の
ものに変換されています。


.. http://alb.anagix.com:8180/myGyazo/data/3ca45f26181734d4a663417a9a1bfde6.png

.. image:: images/3ca45f26181734d4a663417a9a1bfde6.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/3ca45f26181734d4a663417a9a1bfde6.png

ALTAでSpectreを実行する
----------------------

ALTAにもどり、Browseボタンをクリックしてください。前節でSpectre用のネットリストが作成されています。そのためBrowseボタンを
クリックしたことにより内容が更新され、Examples以下を展開すると、以下のように表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/78a842ab78871ab649972ec3b3cf8514.png

.. image:: images/78a842ab78871ab649972ec3b3cf8514.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/78a842ab78871ab649972ec3b3cf8514.png

テストベンチの表示がtestAC(asc,Spectre)となっていることに注目してください。ネットリストを作成する前は、testAC(asc)でした。

シミュレーションするために、テストベンチを選択しSimulateボタンを
クリックする、あるいは、テストベンチの上で、マウスの右ボタンからALTA→altaSimulateを実行してください。
表示がSimulationタブに変わります。


.. http://alb.anagix.com:8180/myGyazo/data/cb3f8f7ace9fe83391158a3ebdfba9d6.png

.. image:: images/cb3f8f7ace9fe83391158a3ebdfba9d6.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/cb3f8f7ace9fe83391158a3ebdfba9d6.png

Simulate nowボタンをクリックするとシミュレーションが開始します。デフォルトではSpectreシミュレーションがバッチモードで 
実行されます。実行終了後、シミュレーションのログはLOGボタン、ネットリストは、Show netlistボタン、DC動作点の
情報は、Show DCボタンを使って確認できます。

Upload nowボタンをクリックすると、シミュレーション結果がALBに送られます。

*注意：* Upload results when completedにチェックが入っていますが、ALTAで対話作業をしている場合には適用されません。
Remove simulation job directoryも同様に適用されません。シミュレーションに使用されるディレクトリ（jobディレクトリ）は、
以下の場所に存在します。時々整理するようにしてください。

Windows:: 
	c:\Users\（ユーザ名）\AppData\Roaming\ALB\（job ID）
Linux:: 
	（ユーザのホーム）/ALBDATA/（job ID）

Start automaticallyにチェックが入っていないことに注意してください。次の節で”ALBからALTAを介して
Spectreを実行する”場合、Start automaticallyにチェックを入れておくと便利です。

ポストプロセスを実行する
---------------------

Postprocess （ポストプロセス処理内容） は以下のようになっています。:

	    testAC_gain: frequencySweep.ac
	     wave = @spectre.get_psf 'gain.csv', 'frequencySweep.ac', 'freq', 'OUT'

以下のように処理を追加してください。:

	    testAC_gain: frequencySweep.ac
	     wave = @spectre.get_psf 'gain.csv', 'frequencySweep.ac', 'freq', 'OUT'
	     freq = wave.col_vec 0
	     out = wave.col_vec 1
	     @outAt10K = out.where freq, 1e4
	     log "Output at 10KHz = #{@outAt10K}"

Executeボタンをクリックするとポストプロセスが実行されます。ログは、SchematicタブのLogの
サブウィンドウに表示されます。

上記のポストプロセスで、waveという変数は、第１桁が周波数（freq）、第２桁が出力（OUT）
の行列です。col_vecというメソッドで、各桁のベクターを取り出しています。whereという
メソッドで、freqが 10KHzのときの出力を取り出しています。


.. http://alb.anagix.com:8180/myGyazo/data/ed6eec2b0243ba210c1b65f64c1d4262.png

.. image:: images/ed6eec2b0243ba210c1b65f64c1d4262.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/ed6eec2b0243ba210c1b65f64c1d4262.png

PostprocessのSaveボタンをクリックすると、このポストプロセスの内容はALBにセーブされます。

ALBからALTAを介してSpectreを実行する
---------------------------------
Simulationタブに戻って、Start automaticallyにチェックを入れてください。


.. http://alb.anagix.com:8180/myGyazo/data/907a10efa456c338169bf6db26c985f4.png

.. image:: images/907a10efa456c338169bf6db26c985f4.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/907a10efa456c338169bf6db26c985f4.png

Upload simulation resultsのサブウィンドウの中で、Upload results when completedにチェック
が入っていると、シミュレーション実行後にシミュレーション結果が自動的にALBに送られます。また、
Remove simulaitn job dir.にチェックが入っていると、シミュレーションに使用された
ディレクトリ（jobディレクトリ）は実行終了後に削除されます。

ALBからシミュレーションを実行するには、インスタンス（Instance0）のページに行きます。


.. http://alb.anagix.com:8180/myGyazo/data/067f75b4b5966acaced1a260850a755e.png

.. image:: images/067f75b4b5966acaced1a260850a755e.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/067f75b4b5966acaced1a260850a755e.png

テストベンチ（testAC）の行の右側にあるコマンドの中から、Altaを実行してください。

*注意：* このコマンドの実行にALTAが連動するためには、Firefoxで xxx.albのようにalbを
拡張子に持つファイルがダウンロードされたときに、alta_slaveコマンド（Windowsでは、alta_slave.bat）が
実行されるように設定しておく必要があります。

シミュレーションが成功するとALBの表示が変わります。


.. http://alb.anagix.com:8180/myGyazo/data/bf3c3a230f001646e3fb49eb5996f9f0.png

.. image:: images/bf3c3a230f001646e3fb49eb5996f9f0.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/bf3c3a230f001646e3fb49eb5996f9f0.png

Quick plotです。LTspiceとSpectreの結果が重なっているのがわかります。


.. http://alb.anagix.com:8180/myGyazo/data/23a9d1bd4938c09761557475f201bf90.png

.. image:: images/23a9d1bd4938c09761557475f201bf90.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/23a9d1bd4938c09761557475f201bf90.png

Plot instancesのtestACをクリックすると、Quick plotと同じ結果が表示されます。縦軸を左右別々に
するために、Edit Plot Instanceをクリックするか、プロットの上でマウスの左ボタンをクリックしてください。


.. http://alb.anagix.com:8180/myGyazo/data/da061ce5ca43bc703a37bfc7eb5e2d00.png

.. image:: images/da061ce5ca43bc703a37bfc7eb5e2d00.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/da061ce5ca43bc703a37bfc7eb5e2d00.png

Yaxisを、auto, auto に変更し、Saveすると以下のようにゲインと位相が左右別々の軸で表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/17620a1e80a095fd78bf6c02a513fa94.png

.. image:: images/17620a1e80a095fd78bf6c02a513fa94.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/17620a1e80a095fd78bf6c02a513fa94.png

.. raw:: html

   <DIV align="right">以上</DIV>

   <!-- DIV style="text-align: right;" >以上</DIV -->

