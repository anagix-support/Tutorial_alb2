.. _ADEin_conversion:
================================
Cadence ADEからの回路データ取り込み
================================

このアプリケーションノートでは、Cadence ADEから回路データをALBに取り込みます。
取り込んだあとで、回路の素子数カウントをおこない、さらにALBおよびALTA上でネットリストの
比較を行います。

CadenceはIC5141, IC61のどちらにも対応しています。
Cadence ADEのデータは、ALBによりバージョン管理されますので、ALBのプロジェクト画面から
任意のバージョンをダウンロードすることができるようになります。

また、ALBに取り込んだ回路データは、ALTAの形式に変換されているので、LTspiceなどのパーソナルツール
を使って編集することができます。

ALTA形式の回路データをCadence ADE用に変換する方法は、アプリケーションノート
:ref:`Cadence ADEへの回路データ書き出し<ADEout_conversion>`　を参照してください。

Cadence ADEデータの作成
----------------------

CadenceはIC5141, IC61のどちらにも対応しています。回路シミュレータはSpectreを使用してください。

*注意：* simulationディレクトリにシミュレーション結果を保存していないと、ネットリストを取り込むことはできません。

ALBにSpectreのネットリストを取り込めば、それをLTspice用に変換し、ALB上でLTspiceを実行することが
できます。

ポストプロセスの作成に必要なネット名や、calculatorで作成した式を取り込むためには、
artist statesを作成してください。

*注意：*　artist statesは、CellviewとDirectoryの両方に対応しています。

作成した回路の例(opampとCMRRテストベンチ）は、アナジックスのALBサーバ（http://alb.anagix.com:8180/）の
Resourcesタブに置いています。


.. http://alb.anagix.com:8180/myGyazo/data/0f52e98071aa3b328fd1b7fec00b4a78.png

.. image:: images/0f52e98071aa3b328fd1b7fec00b4a78.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/0f52e98071aa3b328fd1b7fec00b4a78.png

Sample projectsの中に、アプリケーションノートのデータを置いていますので、
”Cadence ADEからの回路データ取り込み”の回路データ例（opamp_CMRR.tgz）を適当なディレクトリに
展開して利用してください。

*注意：* ALBサーバからResourcesのタブをクリックした場合、ページの見かけは変わりませんが、アナジックスの
ALBサーバに移動しています。もともとのALBサーバに戻るには、ブラウザの戻るボタンを使ってください。

Linux版altaの起動
----------------
*注意：* Cadenceでシミュレーションを行ったのと同じ環境（環境変数PATHの設定）で、altaを起動してください。

altaをコンソールからコマンドで呼び出す場合、以下の例のようにspectreやoceanのパス
が表示されればOKです::

	$ which spectre
	/cadence/mmsim/mmsimxxx/linux/tools/bin/spectre
	$ which ocean
	/cadence/ic5141/linux/tools/dfII/bin/ocean

ADE Express Wizardの起動
------------------------

ALTAにログイン後、メニュバーから Tools->Virtuoso(ADE)->Expressを実行します。


.. http://alb.anagix.com:8180/myGyazo/data/ad085643c672f3de1fef217e074c5ae4.png

.. image:: images/ad085643c672f3de1fef217e074c5ae4.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/ad085643c672f3de1fef217e074c5ae4.png

Choose projectのプルダウンから既存のプロジェクトを選択するか、Create New Projectボタンで
新規にプロジェクトを作成します。


.. http://alb.anagix.com:8180/myGyazo/data/070409976e90ae9a0c92ebcfab17cdca.png

.. image:: images/070409976e90ae9a0c92ebcfab17cdca.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/070409976e90ae9a0c92ebcfab17cdca.png

Create ALB work directory automaticallyにチェックが入っているとALB
work directoryは、NEXTボタンをクリックした時に自動的に作成されます。ALB work directory
のデフォルトは、”ユーザのログインID/ALB/プロジェクト名”です。

*注意：* プロジェクト名にスペースが入っている場合、ALB work directory名では、スペースはアンダースコア（'_'）に
置き換えられます。

既存のALB work directoryを選択するにはBrowseボタンでディレクトリに存在するalb.confファイルを選択します。

NEXTボタンをクリックすると、設定にエラーが無ければ次のステップに進みます。

注意：下図のようなエラーが出た場合、Firefoxで、mozreplを起動してください。


.. http://alb.anagix.com:8180/myGyazo/data/b2d034e8328ec8453c767d209f13dee4.png

.. image:: images/b2d034e8328ec8453c767d209f13dee4.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b2d034e8328ec8453c767d209f13dee4.png

mozreplは、Firefoxのアドオンです。

Cadence ADEディレクトリの選択
---------------------------

Cadence ADEディレクトリ（Cadenceを起動するディレクトリ、cds.libが存在する）を選択します。
また、SpectreのネットリストをALBに取り込むために、Simulationディレクトリ(Simulation dir)を設定します。

*注意：* 回路データをLTspice用に変換するだけならネットリストを取り込む必要はありません。しかし、Spectreで
正しいことが検証されたネットリストがあれば、LTspice（エディタ）で作成したネットリストと比較することで、
変換にエラーがなかったことを検証することができます。ネットリスト比較は、ALBおよびALTAで実行することが
できます。

ポストプロセスの作成に必要なネット名や、calculatorで
作成した式を取り込むためには、artist statesを設定します。


.. http://alb.anagix.com:8180/myGyazo/data/b657452062c490f526c6b1b762d56350.png

.. image:: images/b657452062c490f526c6b1b762d56350.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b657452062c490f526c6b1b762d56350.png

Browseボタンをクリックし、Cadence ADEディレクトリ（ADE path）を選択します。
下図のように、Cadenceのディレクトリに存在するcds.libを選択してください。


.. http://alb.anagix.com:8180/myGyazo/data/075cfc4a69a6a93c3ceb00ffa3eeb826.png

.. image:: images/075cfc4a69a6a93c3ceb00ffa3eeb826.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/075cfc4a69a6a93c3ceb00ffa3eeb826.png

Simulationディレクトリは、対応するBrowseボタンをクリックし、下図のように（この場合は、simulation
という名前のディレクトリを）選んでください。


.. http://alb.anagix.com:8180/myGyazo/data/dcccbf89c4a33eb870535661a991599f.png

.. image:: images/dcccbf89c4a33eb870535661a991599f.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/dcccbf89c4a33eb870535661a991599f.png

artist_statesも同様に、選んでください。この例の場合、ディレクトリ名は、.artist_statesであり、
simulationディレクトリと同じディレクトリに存在します。

*注意：* 
1. ファイルブラウザの設定を隠しファイルを表示するように変更する必要があるかも知れません。
2. ディレクトリの場所および名前は、Cadenceの個人設定により異なります。デフォルトでは、ホームディレクトリの.artist_statesかも知れません。


.. http://alb.anagix.com:8180/myGyazo/data/e343b248395d60bf7febfe342be94b2b.png

.. image:: images/e343b248395d60bf7febfe342be94b2b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e343b248395d60bf7febfe342be94b2b.png

NEXTボタンをクリックして次のステップに進みます。

回路階層のトップにあるセルを選択する
--------------------------------

以下のように、Cadenceのデータ（ライブラリとCell）が表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/eb686d506f623c34d4532a0113ea8392.png

.. image:: images/eb686d506f623c34d4532a0113ea8392.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/eb686d506f623c34d4532a0113ea8392.png

適当な回路セルを選択した状態で、Addボタンをクリックすると、選択されたセルのライブラリ名とセル名、および、
前のステップでSpectreのネットリストをALBに取り込むと指定した場合、ネットリストのパスが表示されます。

Anagix ALBサーバのResourcesのSample projectsにあるopamp_CMRR.tgzを使用した場合、テストベンチは
CMRRしかありませんのでCMRRを選択してください。

トップセルの選択を取り消すには、対象をクリックして選択し、Deleteを実行してください。


.. http://alb.anagix.com:8180/myGyazo/data/bfb387575ffb691c3cad378ebb615a71.png

.. image:: images/bfb387575ffb691c3cad378ebb615a71.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/bfb387575ffb691c3cad378ebb615a71.png

NEXTボタンをクリックして次のステップに進みます。

回路データ取り込みのオプションを指定する
-----------------------------------


.. http://alb.anagix.com:8180/myGyazo/data/8cb9ae45012adf55720c1c4f46b99275.png

.. image:: images/8cb9ae45012adf55720c1c4f46b99275.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/8cb9ae45012adf55720c1c4f46b99275.png

Cadence ADEのデータはALB上でバージョン管理されますが、コメントは、バージョンを区別するために
使用されます。

オプションの意味を以下にまとめます。

* Include layout view ---　schematic view(回路図)とともにlayout view(レイアウト)もALBに取り込む

* Include models --- シミュレーションに使用したモデルライブラリをALBに取り込む

* Include gds files ---　Cadence ADEディレクトリ（Cadenceを起動するディレクトリ、cds.libが存在する）にGDSというディレクトリがある場合、そこに置かれたGDSファイル(拡張子がgdsまたはGDS）をALBに取り込む。

* Always make testbench top level --- テストベンチ回路を通常の回路と区別しない。このオプションがチェックされていない時には、テストベンチ回路にDUT(Device Under Test)回路が１つだけで、そのほかは電源や負荷抵抗などの受動素子のみが含まれる場合に限り、テストベンチ回路をDUTにぶら下げる。そういうデータ構造をALB上に生成する。

* Preserve net name --- Cadence ADEのネット名をすべて保存する

* Exclude simple nets --- n001のようなシステムが自動的に付けたネット名は保持せず、ALBで適当な名前を生成する。ただしOUTAのようにユーザが意図的に付けた名前は保持する。

* Grid size --- この数値を半分にすると、LTspice上では、図形のサイズが倍になる。デフォルトは、0.0625。

この例の場合、Always make testbench top levelのチェックは外しました。

Executeボタンをクリックすると、以下のような確認のフォームが出ますので、OKしてください。


.. http://alb.anagix.com:8180/myGyazo/data/c60784813d979c3319e4678c66421375.png

.. image:: images/c60784813d979c3319e4678c66421375.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/c60784813d979c3319e4678c66421375.png

Spectreネットが取り込まれていることを確認する
----------------------------------------
CMRRを取り込んだ場合、ALTAのALBタブの表示は以下のようになります。


.. http://alb.anagix.com:8180/myGyazo/data/bc7bdfe7efaaa6545c9030993d1846c6.png

.. image:: images/bc7bdfe7efaaa6545c9030993d1846c6.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/bc7bdfe7efaaa6545c9030993d1846c6.png

CMRRテストベンチの上で、マウスの右ボタンをクリックし、ALB -> Show を選択すると、Firefoxブラウザに以下のように
CMRRテストベンチが表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/9ab5a6ac50fcb2cc3dcbd988d9853e93.png

.. image:: images/9ab5a6ac50fcb2cc3dcbd988d9853e93.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/9ab5a6ac50fcb2cc3dcbd988d9853e93.png

Spectreの制御コマンド（Control）や、ネットリストが取り込まれていることを確認してください

素子数カウントを表示する
---------------------
Elements count (recursively)と表示されたところで、countをクリックすると、下図に示すようにこのテストベンチに
含まれる素子の数を素子のタイプ別に表示します。


.. http://alb.anagix.com:8180/myGyazo/data/3780c0a643f7ca5eecb110be55ddf604.png

.. image:: images/3780c0a643f7ca5eecb110be55ddf604.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/3780c0a643f7ca5eecb110be55ddf604.png

上図では、capacitorやresistorなど素子タイプ別の総数を表示していますが、素子タイプをクリックすると
その内訳を表示します。

recursivelyあるいはRecursiveをクリックすると、この回路に含まれる下位の階層の回路に含まれる素子もカウントします。
以下の例では、capacitorとmosfetの内訳を表示しています。


.. http://alb.anagix.com:8180/myGyazo/data/fa0550ab43e532617ffb19c1ce2edc96.png

.. image:: images/fa0550ab43e532617ffb19c1ce2edc96.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/fa0550ab43e532617ffb19c1ce2edc96.png

DLボタンをクリックすると、現在の表示内容をcsvファイルにしてダウンロードすることができます。

ネットリストの変換とdiff表示
-------------------------
ADEから取り込んだ状態では、Spectreのネットリストしかありませんが、Spectreのネットリストから
LTspice用のネットリストを変換により作成することができます。

Edit Testbenchをつかってテストベンチを編集し、下図のように Simulatorとして LTspiceを選択して
Saveしてください。


.. http://alb.anagix.com:8180/myGyazo/data/4d2ae82011e4915b9ed481de22a1a62a.png

.. image:: images/4d2ae82011e4915b9ed481de22a1a62a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4d2ae82011e4915b9ed481de22a1a62a.png

テストベンチを表示したページでShow Testbench Implementationsをクリックすると、以下のように
このテストベンチには、Spectreのネットリストと、それから変換して生成された LTspiceのネットリストが
存在することがわかります。


.. http://alb.anagix.com:8180/myGyazo/data/420e875a06911f6dd645f3fc6dd614f3.png

.. image:: images/420e875a06911f6dd645f3fc6dd614f3.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/420e875a06911f6dd645f3fc6dd614f3.png

現在表示されているControlとNetlistは、LTspiceのものに変わっていることに注意してください。

Spectreの行に表示された Diffコマンドを実行すると下図のように、CotrolおよびNetlistの
テキストの違いを表示します。


.. http://alb.anagix.com:8180/myGyazo/data/0e4453e6116d971d769f084dee10ce46.png

.. image:: images/0e4453e6116d971d769f084dee10ce46.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/0e4453e6116d971d769f084dee10ce46.png

ALBでのネットリストの比較
----------------------

もともとのSpectreネットと変換されたLTspiceネットを比較しますが、その前に
opampセルをCMRRテストベンチと同じようにLTspice用に変換してください。


.. http://alb.anagix.com:8180/myGyazo/data/708d29ee78674377c2d679d75c629005.png

.. image:: images/708d29ee78674377c2d679d75c629005.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/708d29ee78674377c2d679d75c629005.png

Spectreの行に表示された Compare コマンドを実行すると、回路比較プログラムが実行され、
実行結果が以下のように表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/1d0f174aa7654df646d25be18c082d4b.png

.. image:: images/1d0f174aa7654df646d25be18c082d4b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/1d0f174aa7654df646d25be18c082d4b.png

当然ですが、素子の接続(elements connection)にも、素子のパラメータ(elements parameters)にも
違いはありません。

次に、CMRRテストベンチでCompareコマンドを実行してみます。Spectreのネット(Neta)ではサブサーキット(opamp)を
I0とI12で呼んでいるのに対し、基準となるLTspiceのネット(Netb)では、XI0とXI12で呼んでいます。
LTspiceに限らずSpiceでは、Xがサブサーキットの引用を意味します。


.. http://alb.anagix.com:8180/myGyazo/data/97b3aeb72b4efa28693b66ebc5856609.png

.. image:: images/97b3aeb72b4efa28693b66ebc5856609.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/97b3aeb72b4efa28693b66ebc5856609.png

以下の図に示すように、CMRRテストベンチのPropertiesの１つである　compare_optionsに
element_name_mapとして、I0をXI0に、I12をXI12に変換する指示を与えることができます。


.. http://alb.anagix.com:8180/myGyazo/data/77b7a3d1b369e635cd28549e898db7c7.png

.. image:: images/77b7a3d1b369e635cd28549e898db7c7.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/77b7a3d1b369e635cd28549e898db7c7.png

これで、以下のように素子の接続(elements connection)には違いが無くなります。


.. http://alb.anagix.com:8180/myGyazo/data/162441980b2d1060b579fe05056ce2d7.png

.. image:: images/162441980b2d1060b579fe05056ce2d7.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/162441980b2d1060b579fe05056ce2d7.png

素子のパラメータについては、spectreでは、capacitorやresistorがモデル名であるのに対し、
LTspiceではモデルは使われていません。また、Spectreでは、100Mが100e6であるのに対し、LTspice
では、100MEGを使用しています。

ALTAでのネットリストの比較
-----------------------
ALTAでは、LTspiceの回路図から作成されるネットリストと、もともとALBに存在するネットリスト
の比較を行います。

まずLTspiceの回路図を開き、ネットリストを作成します。ALTAのALBタブは、以下のように
なっています。ADEから読み込んだ直後は、テストベンチは、CMRR(asc,Spectre)と表示されていましたが、
今は、CMRR(asc,LTspice)と表示されています。ascは、LTspiceで開くことのできる回路図が存在すること
を意味し、そのあとのシミュレータ名は、ALBで現在選択されているシミュレータを示しています。


.. http://alb.anagix.com:8180/myGyazo/data/9fafa3259560d448a0320c17391f6e34.png

.. image:: images/9fafa3259560d448a0320c17391f6e34.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/9fafa3259560d448a0320c17391f6e34.png

CMRRテストベンチをダブルクリックするか、選択した後で、Editコマンドをクリックして回路を開いてください。


.. http://alb.anagix.com:8180/myGyazo/data/092842a1a9fda8bdbb7d4eed2ef3679e.png

.. image:: images/092842a1a9fda8bdbb7d4eed2ef3679e.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/092842a1a9fda8bdbb7d4eed2ef3679e.png

シミュレーションを実行するか、View->SPICE Netlistを実行するとネットリストが作成されます。
ALTAのSchematicタブは、以下のようになっています。


.. http://alb.anagix.com:8180/myGyazo/data/79cb082180d2547e5919b944feb7709d.png

.. image:: images/79cb082180d2547e5919b944feb7709d.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/79cb082180d2547e5919b944feb7709d.png

Show netlistボタンを実行すると、以下のようなネットリストが作られていることが確認できます。


.. http://alb.anagix.com:8180/myGyazo/data/a6f607a57b28889af1b0c529d5b82db0.png

.. image:: images/a6f607a57b28889af1b0c529d5b82db0.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/a6f607a57b28889af1b0c529d5b82db0.png

次に、ALBタブに戻って、テストベンチCMRR(asc,LTspice)を選択し、Simulateコマンドを実行してください。
ALTAの表示が以下のように Simulationタブに変わります。Show netlistで、以下のように ALBが持っている（Spectre
から変換された）LTspiceのネットリストが表示されます。


.. http://alb.anagix.com:8180/myGyazo/data/d9e67d26a05ae3237ed8327e9f3f5aed.png

.. image:: images/d9e67d26a05ae3237ed8327e9f3f5aed.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/d9e67d26a05ae3237ed8327e9f3f5aed.png

ネットリストの比較は Schematicタブから実行できます。Compareコマンドを実行すると、比較
結果のLogが表示されます。素子接続(elements connection)に違いはありませんが、素子パラメータ
は異なっていることがわかります。この場合、LTspiceの回路図では R0の値が 20Kでしたが、基準となる
ALBのネットリストでは 160Kでした。（もともとのCadence ADEで、ネットリストを作成したあとで、回路図を
変更したためにこのようなことが起きました。）

以上


