.. _ALTA_UserGuide:
================================
シミュレーションガイド　Overview
================================
ALTAのログイン
------------
ALBにログインする時と同じユーザIDとパスワードを使用します。


.. http://alb.anagix.com:8180/myGyazo/data/b5dc63331fa6346f7e6c1acb86719978.png

.. image:: images/b5dc63331fa6346f7e6c1acb86719978.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b5dc63331fa6346f7e6c1acb86719978.png

ALTAを実行するマシーンごとに、ALBサーバにライセンスの設定が必要なので、ログインできない場合は管理者に相談してください。

プロジェクトの選択
---------------
Setupボタンをクリックするとプロジェクト選択画面があらわれます。


.. http://alb.anagix.com:8180/myGyazo/data/69edb563c5dfb063a6676c6a56e0ee6a.png

.. image:: images/69edb563c5dfb063a6676c6a56e0ee6a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/69edb563c5dfb063a6676c6a56e0ee6a.png

Choose Projectの中からプロジェクトを選択してください。
新規にプロジェクトを作成するときは、Create New Projectをクリックします。

Browserの使い方
--------------

プロジェクトを選択すると自動的にBrowserが開きます。
意図的にBrowseするときにBrowseボタンを使います。


.. http://alb.anagix.com:8180/myGyazo/data/47df39e97f74241830cf7ef1c25bc5a0.png

.. image:: images/47df39e97f74241830cf7ef1c25bc5a0.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/47df39e97f74241830cf7ef1c25bc5a0.png

*注意：* 上図は、Browserの左側のみを表示しています

Browserの左側は、回路セルやテストベンチを操作するウィンドウです。
Browserの右側は、モデルライブラリを操作するウィンドウです。

ブラウザの左側では、ライブラリ、セル、インスタンス、テストベンチ選択の他、モデル参照を設定することができます。
以下のボタンをクリックできますが、何を選択しているかで動作が異なります（動作しない／禁止されている
組み合わせもあります）。

* Import：　LTspiceの回路を、プロジェクトやライブラリに取り込みます
* Edit:　回路セル、インスタンス、テストベンチをLTspiceで編集します
* Simulate:　テストベンチをシミュレーションします
* ADE: Cadence ADEにエキスポートします（Linux版の機能）

セル、インスタンスなどを選択した状態で右ボタンを押すと、以下のメニュを選択できます。

.. http://alb.anagix.com:8180/myGyazo/data/cde90fab3181ced93f5c0573159d7be4.png

.. image:: images/cde90fab3181ced93f5c0573159d7be4.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/cde90fab3181ced93f5c0573159d7be4.png

* ALTA → Import ：　前ページのImportボタンと同じ
*         altaSimulation： Simulationボタンと同じ
*         altaAppend： 選択したセルを、現在開いているLTspiceで使用できるようダウンロードします
*         adeXport： 前ページのADEでと同じ
*         addModels： 右側のウィンドウで選択しているモデルなどを、選択したインスタンスに付加します


.. http://alb.anagix.com:8180/myGyazo/data/3d1c25b9a61f8f903f02458a2ee54eef.png

.. image:: images/3d1c25b9a61f8f903f02458a2ee54eef.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/3d1c25b9a61f8f903f02458a2ee54eef.png

* ALB  → Show： 選択した要素をブラウザに表示します
*        Edit：　選択した要素をブラウザで編集します
* New： 選択した要素と同じ種類の要素を作成します
* newChild： 選択した要素の下位の要素を作成します
* Rename、Delete：　選択した要素の名称変更or削除

LTspiceの回路図を開く
------------------

前提条件： ALTAのシミュレーションプランナで回路図を開くには、まずALBにLTspiceの回路を登録しておく必要があります。

ALBに登録するには以下の方法があります（詳細は、ALTAユーザガイドを参照）。
* Cadence ADEからALBに読み込む
* ALTAを使って新規に作成する
* ALTAを使って既存のLTspiceの回路を登録する
* LTspiceの回路図を開く（つづき）

LTspiceの回路を開くには以下の２つの方法があります。

   * 方法１： ALBのテストベンチ画面からALTA EDITを実行
   * 方法２： ALTAのBrowser画面からEditを実行（あるいは、選択状態で右ボタンをクリックし、ALTAaltaEdit


.. http://alb.anagix.com:8180/myGyazo/data/14da942a76cf1bb4de16e028ddf7683b.png

.. image:: images/14da942a76cf1bb4de16e028ddf7683b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/14da942a76cf1bb4de16e028ddf7683b.png

回路が開くと、ALTAの画面がSchematic Tabに切り替わります。


.. http://alb.anagix.com:8180/myGyazo/data/c3b1a2625848efc0e90ae2c6fb9f251f.png

.. image:: images/c3b1a2625848efc0e90ae2c6fb9f251f.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/c3b1a2625848efc0e90ae2c6fb9f251f.png

この画面では、LTspiceのシミュレーション実行結果を使って、ALB特有のポストプロセスを作成したり、さらにパラメトリックプロットを実行するためにシミュレーションプランナを開くことができます。

Schematic Tabでできる操作
------------------------

* Postprocessに関係するもの

  * Create： LTspiceのグラフからポストプロセスの雛形を作成する
  * Save: ポストプロセスをALBにセーブする
  * Load: ポストプロセスをALBからロードする
  * PlanIt: シミュレーションプランナを開く

* LTspice回路図に関係するもの

  * Upload now：LTspice回路図をアップロードする
  * Reopen：一度閉じたLTspice回路図を再度開く

ポストスクリプトの作成
------------------
ポストプロセス全般については「ALBポストプロセス入門」を参照してください。

* ただし、この入門資料では、ALB（Webサーバ）でのポストプロセス開発を主眼にしているため、ポストプロセスのデバッグをおこなうために実行環境をダウンロードしていますが、ALTAではその必要はありません。
* ALTAではポストプロセスのデバッグがより簡単です。

ポストプロセスは、Ruby言語ですので、文法については、例えば以下のサイトを参照してください：

* 逆引きruby： http://www.namaraii.com/rubytips/　

ポストプロセス入力欄に直接入力することも出来るし、LTspice のグラフから雛形を生成することもできます


.. http://alb.anagix.com:8180/myGyazo/data/ac9ac98bef8dcabc75d65ff8c6d9ddb3.png

.. image:: images/ac9ac98bef8dcabc75d65ff8c6d9ddb3.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/ac9ac98bef8dcabc75d65ff8c6d9ddb3.png


Schematic TabのCreateボタンをクリックするとLTspiceのグラフからポストプロセスの雛形が生成されます。
* 準備としてLTspiceのグラフ（pltファイル）をセーブしておく必要があります。
* Createボタンの表示はExecuteボタンに変わります。

LTspiceのグラフをセーブするステップ：
--------------------------------
1. シミュレーションを実行する
2. プローブを立てて、グラフを作成する
3. グラフのウィンドウで、File → Save Plot Settingsを実行する


.. http://alb.anagix.com:8180/myGyazo/data/4cd002aebe6617607327558bf2aa24d6.png

.. image:: images/4cd002aebe6617607327558bf2aa24d6.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4cd002aebe6617607327558bf2aa24d6.png

この例の場合、vbgというノードを選択したので、 以下のようなポストプロセスの雛形が作成されます。

 | tb1_dc: dc
 |   wave = @ltspice.save 'dc.csv', 'dc', 'temperature', 'V(vbg)'

ポストプロセスのデバッグ
--------------------
Executeボタンをクリックすると、ポストプロセスが実行されます。


.. http://alb.anagix.com:8180/myGyazo/data/0bac93a31dd2fc03b61469ad978abc6c.png

.. image:: images/0bac93a31dd2fc03b61469ad978abc6c.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/0bac93a31dd2fc03b61469ad978abc6c.png

エラーがある場合上図のようにエラーメッセージが表示されます。
この例の場合、wave.col_vec(1) と書くべきところ、誤ってwave.colvec_1(1)と入力したためエラーが発生しました

ポストプロセスの中に以下のデバッグ出力を挟むことができます。
* log “メッセージ”    ---  log表示欄にメッセージが表示されます
* puts “メッセージ”  --- ALTAを起動したコンソールにメッセージが表示されます

ポストプロセスの中からデバッガの起動
--------------------------------
ポストプロセスの任意の位置に以下の行をいれると、ポストプロセス実行時にデバッガが起動します。

| debugger

デバッガの使い方は コンソールにhelp と入力してください。

ALBのネットリストをシミュレーションする
-----------------------------------

ALBのネットリストをシミュレーションするには、以下の２つの方法があります


.. http://alb.anagix.com:8180/myGyazo/data/e3e5d57644d07118452ab5222e33103d.png

.. image:: images/e3e5d57644d07118452ab5222e33103d.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/e3e5d57644d07118452ab5222e33103d.png

* 方法１： ALBのインスタンス画面やCellView画面からからAltaを実行

* 方法２： ALTAのBrowser画面からSimulateを実行（あるいは、選択状態で右ボタンをクリックし、altaSimulate）

オプションの設定
--------------
デフォルト状態では、シミュレーションはALTA上で実行され実行結果は自動的にALBに戻されます。
また、ALTA上の実行ディレクトリは削除されます。
これらは以下で変更できます。


.. http://alb.anagix.com:8180/myGyazo/data/a05a56be1271b4489834d27b513c160c.png

.. image:: images/a05a56be1271b4489834d27b513c160c.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/a05a56be1271b4489834d27b513c160c.png

* Start automaticallyのチェックを外す → Simulate nowでマニュアルで起動
* Batch modelからInteractive modeに変更（トグルになっています） → シミュレーション実行時にLTspiceのウィンドウが表示されます
* Remove simulation job directoryのチェックを外す → 実行ディレクトリが削除されません

ポストプロセスの実行
------------------


.. http://alb.anagix.com:8180/myGyazo/data/1dd1b6eb6b7e8a0363362410696de2d4.png

.. image:: images/1dd1b6eb6b7e8a0363362410696de2d4.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/1dd1b6eb6b7e8a0363362410696de2d4.png

“LTspiceの回路図を開く”の場合と同様にポストプロセスを実行することができます。但しログは、Schematicタブに表示されるので注意してください。

ボタンの説明
* Execute:　ポストプロセスを実行する
* Save:　ポストプロセスをALBのテストベンチに保存する
* Load:　ALBのテストベンチからポストプロセスをロードする
* PlanIt:　プランナを開く

シミュレーションプランナの起動
--------------------------


.. http://alb.anagix.com:8180/myGyazo/data/b26aacbf1c34f4d678396a40329aab4e.png

.. image:: images/b26aacbf1c34f4d678396a40329aab4e.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b26aacbf1c34f4d678396a40329aab4e.png

シミュレーションプランナは、SchematicタブからでもSimulationタブからでも開くことができます（同時に複数可）。


.. http://alb.anagix.com:8180/myGyazo/data/b1f0772d8e327f11fb9706f4dd4d63fb.png

.. image:: images/b1f0772d8e327f11fb9706f4dd4d63fb.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/b1f0772d8e327f11fb9706f4dd4d63fb.png

シミュレーションプランナは、ALTA本体とは独立したウィンドウで実行し、ALBのCellViewに対応しています。
シミュレーションプランナの設定は、ファイルにセーブすることができます（拡張子は、.apです）。

ALBに接続していない状態でも、シミュレーションプランナの設定ファイルを開くことで、シミュレーションプランナを起動することができます。

シミュレーションプランナの設定
--------------------------
プランナの画面は、下図に重ねて示すように以下の３つのタブから構成されています。


.. http://alb.anagix.com:8180/myGyazo/data/43418b726dac177da1a5fdd1c94c5a25.png

.. image:: images/43418b726dac177da1a5fdd1c94c5a25.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/43418b726dac177da1a5fdd1c94c5a25.png

* Postprocess：ポストプロセスの編集、実行、結果のグラフ表示処理などを行います
* Netlist：パラメータの使用などネットリストの編集を行います
* Control: スイープ条件（プラン）をここで作成します

ネットリストの編集
----------------
変数は、#{@temp}のような書式で設定します。


.. http://alb.anagix.com:8180/myGyazo/data/2554a72eecf35d8d18fcad71ace91a73.png

.. image:: images/2554a72eecf35d8d18fcad71ace91a73.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/2554a72eecf35d8d18fcad71ace91a73.png

Parametersと表示された欄でパラメータに値を与えることもできます。

*注意：* 　現在のポストプロセスではengineering notation は使えませんので@stop_freq = ‘1G’のように文字列はquotation markで囲ってください。1e9ならば、@stop_freq = 1e9でOKです。

ネットリストの変更はシミュレーションにそのまま反映されます

コントロールの作成
----------------
コントロール編集欄に自由に記述できますがEdit sweepダイアログを使って、新たにスイープ変数を付け加えたり、既存のスイープを
変更したりできます。


.. http://alb.anagix.com:8180/myGyazo/data/4485aae9ade6f07dbf0c2f8a139795b4.png

.. image:: images/4485aae9ade6f07dbf0c2f8a139795b4.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/4485aae9ade6f07dbf0c2f8a139795b4.png

タブの説明

* Source：電源をスイープする
* Param： LTspiceのパラメータ（.stepで指定）をスイープ
* Variable： ネットリストに指定した変数をスイープ
* Model：　モデルを切り替える（現在準備中）

ポストプロセスの実行
------------------
Simulateをクリックするとシミュレーションに続いてポストプロセスが実行されます


.. http://alb.anagix.com:8180/myGyazo/data/7069f031ebbf2fca404c83eb618751c6.png

.. image:: images/7069f031ebbf2fca404c83eb618751c6.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/7069f031ebbf2fca404c83eb618751c6.png

*注意：*  ポストプロセスに記述ミスがあり、再度シミュレーションは不要な場合、修正後RunPostprocessでポストプロセスのみ実行できます

この例では、パフォーマンスとして、 100MHzにおける位相(@phase100M) を計算しています。

結果の表示（表）
--------------


.. http://alb.anagix.com:8180/myGyazo/data/de63946a7e17fde7c5ca5a03989612e8.png

.. image:: images/de63946a7e17fde7c5ca5a03989612e8.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/de63946a7e17fde7c5ca5a03989612e8.png

Printボタンを押すと表が表示されます
WindowsではSaveボタンでExcelに表をセーブすることができます


.. http://alb.anagix.com:8180/myGyazo/data/62f553e782e19acb6ba4dc04054a53d5.png

.. image:: images/62f553e782e19acb6ba4dc04054a53d5.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/62f553e782e19acb6ba4dc04054a53d5.png

結果の表示（グラフ）
-----------------

スイープ変数を横軸、ポストプロセスで定義したパフォーマンスを縦軸としてグラフを描くことができます。
この例では、Sweepに@tempを選択、@src_V1（V1の値）がパラメータです。


.. http://alb.anagix.com:8180/myGyazo/data/d0ca4405fd38ff1aa4fc808bbe5bc011.png

.. image:: images/d0ca4405fd38ff1aa4fc808bbe5bc011.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/d0ca4405fd38ff1aa4fc808bbe5bc011.png

グラフのCreate Viewボタンにより、新規にビューを作成すれば、結果を更にポストプロセスすることができます。

結果のポストプロセス
------------------
以下の例のように新しいビュー（phase100M-temp）に更に計算処理を追加することができます。

   | @phase40 = phase100M.where temp, 40

計算を実行するには、Viewとして、phase100M-tempを選択し、RunPostprocessを実行します。

CellViewの作成・更新
-------------------
作成したビューは、ALBのCellViewとして保存することができます。

* ALB → Create View


.. http://alb.anagix.com:8180/myGyazo/data/1d23a27ff241aae689d613614ed5212a.png

.. image:: images/1d23a27ff241aae689d613614ed5212a.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/1d23a27ff241aae689d613614ed5212a.png

CellViewを更新するときは ALB  → Update View

設定をファイルに保存する
---------------------
File → Saveにより、プランナの設定をファイルに保存することができます（拡張子は、.apです）


.. http://alb.anagix.com:8180/myGyazo/data/fdb417240f6e31c2382023039ed371c3.png

.. image:: images/fdb417240f6e31c2382023039ed371c3.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/fdb417240f6e31c2382023039ed371c3.png

File → Loadにより設定をファイルから読み込むことができます


.. http://alb.anagix.com:8180/myGyazo/data/89897b2a73fa0eee5ff32fc382fd666b.png

.. image:: images/89897b2a73fa0eee5ff32fc382fd666b.png
    :scale: 75%
    :target: http://alb.anagix.com:8180/myGyazo/data/89897b2a73fa0eee5ff32fc382fd666b.png

ALBに接続していない状態でも、シミュレーションプランナの設定ファイルを開くことで、シミュレーションプランナを起動することができます。

Alta → Tools → Open → AltaPlanner

.. raw:: html

   <DIV align="right">以上</DIV>

   <!-- DIV style="text-align: right;" >以上</DIV -->



